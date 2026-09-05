# Task: add remediation and verification depth

Continue after the macOS guided tune-up MVP. Read the repository instructions,
product documents, current implementation, tests, and git status. Preserve user
changes and work until the acceptance criteria are complete.

## Goal

Make the product deliver a defensible outcome: help the user complete the safest
high-impact repairs, verify immediate effects, and create a delayed battery
comparison without misleading claims.

Do not add experimental USB protocols or an iPhone helper in this task.

## Required implementation

1. Implement the remediation catalog as versioned data with stable IDs,
   preconditions, contradicting evidence, expected effect, execution mode,
   reversibility, backup requirement, confirmation copy, and verification.
2. Support four execution modes:
   - local safe action;
   - guided action on the iPhone;
   - official Apple utility or service handoff;
   - informational recommendation.
3. Implement guided repair flows for:
   - freeing storage with iPhone Storage recommendations;
   - reviewing background activity, location, and notification behavior for a
     specific high-use app;
   - choosing the appropriate Low Power Mode tradeoff;
   - cooling and retesting a thermally constrained phone;
   - waiting and rechecking temporary post-update activity;
   - escalating Battery Health Service to Apple service;
   - backing up before an update or recovery handoff.
4. Require explicit confirmation for each action and record completed,
   declined, failed, cancelled, and handed-off outcomes.
5. Add return-from-handoff checklists rather than assuming an external action
   succeeded.
6. Implement immediate verification for available storage, OS version,
   selected settings, and action completion evidence.
7. Implement a delayed battery verification session for two-to-seven days
   later. Record enough context to detect incomparable usage, charging, thermal,
   and software conditions.
8. Report improved, unchanged, worse, or insufficient evidence. Explain the
   result in plain English and preserve the supporting data.
9. Add local export with a redaction preview and a **Delete session data**
   action.
10. Add a safety gate that prevents destructive recovery guidance unless a
    backup is confirmed and lower-risk relevant actions were considered.

## Prohibited behavior

- Automatic app deletion or offloading
- Automatic restart, restore, erase, or security reduction
- Generic RAM or cache cleaning
- Fixed percentage performance claims
- Treating a short battery-level sample as proof of battery life
- Hiding missing, user-entered, or low-confidence evidence
- Runtime account, telemetry, cloud processing, or background daemon

## Verification

Add tests for:

- remediation schema and stable IDs;
- deterministic action ranking;
- all action outcome states;
- backup and destructive-recovery safety gates;
- handoff return checklists;
- immediate and delayed verification;
- comparable and incomparable battery sessions;
- report redaction and local data deletion;
- every remediation in docs/remediation-catalog.md;
- English UI copy.

Run formatting, strict linting, all tests, a production build, and the complete
manual smoke test. Exercise a before-and-after demo with fixtures without
presenting fixture data as a real device result.

## Documentation

Update the remediation catalog, support matrix, user journey, README, privacy
notes, and manual test plan to match the implementation.

## Completion report

Report the repairs users can complete, how each outcome is verified, all checks
run, unsupported automation that remains a guided handoff, and the next smallest
milestone. Do not stop after planning.
