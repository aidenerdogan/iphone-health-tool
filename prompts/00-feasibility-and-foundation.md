# Task: build the desktop foundation

You are implementing M0 of iPhone Tune-Up with GPT-5.6 Sol. Continue until the
defined result is working and verified. Do not stop after research or planning.

## Read first

Read AGENTS.md, README.md, NEXT_SESSION.md, every document in docs/, the current
git status, and the current repository tree. Preserve unrelated user changes.

Inspect the installed Rust, Node.js, package-manager, and macOS development
toolchains. Check current primary documentation before selecting dependency
versions. Record material decisions and source links in the repository.

## Product goal

Build the foundation of an English desktop assistant for an infrequent
five-to-ten-minute iPhone tune-up. A complete session follows:

Connect or continue manually -> choose a symptom -> collect evidence -> diagnose
-> review actions -> confirm actions -> verify -> finish with a local report.

The foundation must work without a real iPhone and without deep USB access.

## Technical direction

Use Tauri 2, a Rust core, and a TypeScript UI unless the feasibility check finds
a concrete blocking issue. If blocked, document the evidence, choose the
smallest cross-platform alternative that preserves the Rust domain core, and
continue implementing.

Create clear boundaries for:

- desktop UI;
- workflow orchestration;
- portable domain core;
- evidence persistence;
- diagnostic rules;
- remediation policy;
- capability-based platform adapters.

Do not integrate libimobiledevice, private Apple frameworks, MDM, or an iPhone
helper in this task.

## Required implementation

1. Create a reproducible desktop project with pinned dependency policy and
   documented development commands.
2. Implement versioned Rust models for TuneUpSession, DeviceDescriptor,
   CapabilitySnapshot, Evidence, Finding, Remediation, ActionDecision,
   ActionResult, and Verification.
3. Implement a typed state machine for the complete product loop. Invalid
   transitions must fail explicitly.
4. Implement in-memory and local file session stores behind interfaces. Use a
   versioned format and atomic writes.
5. Implement capability interfaces and two adapters:
   - a deterministic mock device for demos and tests;
   - a manual-evidence adapter that requires no connection.
6. Implement a small transparent rules engine with at least one fixture-backed
   finding for each symptom: battery drain, slowness, heat, and low storage.
7. Implement a remediation policy that ranks actions by evidence confidence,
   expected impact, safety, reversibility, effort, and verifiability.
8. Build the complete English UI using the mock adapter:
   - Welcome
   - Connect or continue manually
   - Symptom selection
   - Evidence review
   - Findings
   - Repair plan
   - Per-action confirmation
   - Verification
   - Final report
9. Make evidence provenance and confidence visible.
10. Include empty, loading, error, declined-action, disconnected, and
    insufficient-evidence states.
11. Add a local English demo dataset and a clear development-only way to launch
    it. Production behavior must not silently use mock data.

## UX constraints

- All user-visible first-release copy is English.
- Use plain language and one primary decision per screen.
- Do not expose developer terms such as MetricKit, plist, sysdiagnose, or
  lockdownd in the basic flow.
- Do not promise a percentage improvement.
- Never call a battery percentage sample an energy measurement.
- Every action explains what will change, expected benefit, risk,
  reversibility, and verification.
- The interface must be keyboard accessible and work at increased text sizes.

## Safety and privacy

- No account, analytics, telemetry, advertising, cloud upload, or background
  daemon.
- No destructive action in this milestone.
- Never execute imported or user-selected content.
- Never imply access to other apps' private data.
- Do not require network access at runtime.

## Verification

Add meaningful Rust and frontend tests for:

- valid and invalid state transitions;
- schema serialization and migration behavior;
- atomic persistence failure;
- evidence provenance;
- rule evaluation with missing and contradicting evidence;
- deterministic remediation ranking;
- declined actions;
- improved, unchanged, worse, and insufficient verification states;
- all four symptom journeys;
- English user-visible copy.

Run formatting, linting with warnings treated as errors, unit tests, frontend
tests, and a production desktop build. Launch the app and verify the complete
mock journey. If GUI inspection is unavailable, document the limitation and
verify the navigation state programmatically.

## Documentation

Update README setup instructions and add:

- dependency and development commands;
- a repository map matching the actual tree;
- a short architecture decision if the preferred stack changes;
- a test strategy;
- a manual smoke-test checklist.

## Completion report

Report what works, the exact checks and results, files or decisions that changed,
and any real blocker. Do not claim hardware support that was not tested. Do not
leave placeholder logic where the acceptance criteria require working behavior.
