# Architecture

## Product shape

iPhone Tune-Up is a desktop application with a portable diagnostic core. The
first release targets macOS. Windows is a planned second platform. A temporary
iPhone helper is an optional future adapter, not a basic requirement.

The architecture must remain useful when deep USB diagnostics are unavailable:
the tool can combine safe connection facts, guided user evidence, imported
Apple diagnostic files, and transparent rules.

## System overview

    Desktop UI
        |
    Tune-up workflow coordinator
        |
    Evidence store ---- Diagnostic rules ---- Remediation policy
        |                                         |
    Capability-based device adapters         Action adapters
        |                                         |
    USB presence / manual evidence /         Guided iPhone step /
    imported logs / optional protocol        official utility handoff /
    adapter / optional helper                local safe action

## Desktop shell and portable core

The preferred implementation is Tauri 2 with a Rust core and a
TypeScript-based UI. A feasibility task must confirm the installed toolchain and
record any blocking issue before this becomes irreversible.

The portable Rust core owns:

- versioned evidence models;
- diagnostic findings and confidence;
- symptom-specific rules;
- remediation eligibility and safety gates;
- tune-up session state;
- before-and-after comparisons;
- local export and redaction.

The UI owns:

- onboarding and device trust instructions;
- symptom selection;
- evidence collection;
- repair-plan presentation;
- per-action confirmation;
- verification and English explanations.

## Capability-based adapters

No workflow may assume a data source exists. Each adapter reports capabilities
at runtime and the coordinator selects the safest available path.

### Supported adapters

- UsbPresenceAdapter: confirms a connected device without claiming deeper data.
- ManualEvidenceAdapter: records values the person reads from Battery, Battery
  Health, and iPhone Storage.
- ScreenshotEvidenceAdapter: stores a user-selected screenshot locally; OCR is
  deferred until it can be made reliable and reviewable.
- DiagnosticImportAdapter: imports explicitly selected Apple diagnostic or
  analytics files through versioned parsers.
- OfficialHandoffAdapter: opens or explains Finder, Apple Devices, Settings,
  Apple Diagnostics, backup, update, and support workflows.

### Experimental adapters

An independently implemented native-protocol adapter such as libimobiledevice
may expose additional read-only facts. It must be:

- disabled by default until compatibility is demonstrated;
- isolated behind the same device interface;
- dynamically capability-probed;
- read-only in the first release;
- covered by fixture and device compatibility tests;
- labeled as independent and not endorsed by Apple.

Failure of an experimental adapter must fall back to the supported workflow.

### Optional iPhone helper

A future helper may run a short, user-started workload or export data owned by
that helper. It cannot inspect or repair other apps. The desktop app must explain
this boundary and uninstall instructions must be obvious.

## Core domain

### TuneUpSession

Contains session ID, product/schema version, timestamps, selected symptoms,
platform, device descriptor, capability snapshot, evidence references,
findings, action decisions, action results, and verification state.

### Evidence

Every evidence item contains:

- source type;
- collection time;
- value and unit;
- provenance;
- confidence;
- optional redacted source reference;
- compatibility or freshness warning.

Values from user input, USB queries, screenshots, and imported logs are never
silently merged.

### Finding

A finding has an ID, symptom category, severity, explanation, supporting and
contradicting evidence, confidence, and eligible remediations.

### Remediation

Remediations have one of four execution modes:

1. Local safe action
2. Guided action on the iPhone
3. Handoff to an official Apple utility or service
4. Informational recommendation

Each remediation declares preconditions, expected effect, reversibility,
confirmation text, verification method, and whether a backup is required.

## Tune-up state machine

    Welcome
      -> Connect or continue manually
      -> Select symptom
      -> Collect minimum evidence
      -> Diagnose
      -> Review repair plan
      -> Confirm and complete one action at a time
      -> Immediate verification
      -> Optional delayed verification
      -> Export or finish

Sessions are resumable. Disconnecting the phone, closing the app, or declining
an action must not corrupt the session.

## Verification

Immediate checks cover facts such as available storage, OS version, and whether
an intended action completed. Battery-life claims require delayed evidence after
normal use. The product reports improved, unchanged, worse, or insufficient
evidence; it never converts a short battery-percentage sample into an energy
claim.

## Privacy and security

- Local storage by default
- No account, telemetry, or cloud processing
- User-selected import and export only
- Redaction preview before export
- Path traversal and archive-bomb defenses for imported diagnostics
- No execution of imported files
- Explicit consent before any setting, file, app, backup, update, or recovery
  action
- No silent restart, restore, erase, uninstall, or security reduction

## Packaging

The macOS release should be signed and notarized. Distribution outside the Mac
App Store may be necessary for device communication, but the product should
still use least privilege and avoid persistent privileged helpers. Windows
packaging is a later milestone using the same core and UI.
