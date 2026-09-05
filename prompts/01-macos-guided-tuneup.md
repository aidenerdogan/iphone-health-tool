# Task: build the macOS guided tune-up MVP

Continue the repository after M0. Read AGENTS.md, README.md, NEXT_SESSION.md,
all docs, the implementation, tests, and git status. Preserve sound decisions
and user changes. Work until the MVP is functional and verified.

## Goal

Turn the foundation into a useful English macOS tune-up that can detect an
iPhone cable connection when safely possible, always offers a manual fallback,
diagnoses four common symptom groups, produces a prioritized repair plan, and
guides the user through supported actions.

The basic product must not depend on private Apple frameworks, MDM,
libimobiledevice, Developer Mode, Xcode, or a permanent iPhone app.

## Required implementation

1. Implement a macOS UsbPresenceAdapter using the least-privileged stable
   mechanism available. It may claim only the facts it can verify.
2. Model connection states explicitly: waiting, locked or trust may be required,
   connected, disconnected, unsupported, permission failure, and manual mode.
3. Keep the manual-evidence path fully functional when USB detection fails.
4. Build symptom-specific evidence flows for:
   - battery drains too quickly;
   - iPhone feels slow;
   - iPhone gets too hot;
   - storage is almost full.
5. Collect only the minimum relevant user-confirmed facts from iPhone Battery,
   Battery Health, iPhone Storage, charging state, recent updates, heat, and
   unexpected shutdowns.
6. Add a review step so detected and entered evidence cannot be confused.
7. Implement documented, transparent rules for at least:
   - critically low storage;
   - one app dominating background battery use;
   - Battery Health showing Service;
   - temporary post-update battery impact;
   - Low Power Mode explaining reduced responsiveness;
   - thermal conditions invalidating a performance check;
   - repeated freezes or restarts requiring escalation.
8. Build a repair-plan screen that shows evidence, confidence, impact, time,
   reversibility, and verification for each action.
9. Implement exact English guided steps and safe official handoffs for iPhone
   Settings, Finder backup/update, Apple Diagnostics, and Apple Support.
10. Do not automate Finder through fragile UI scripting. If no documented
    integration exists, provide a clear handoff and return checklist.
11. Preserve and resume a session after disconnect or application restart.
12. Generate a readable local report with no sensitive data by default.

## UX requirements

- A first-time nontechnical user must be able to finish without external docs.
- Every screen has one clear primary action and a safe way back.
- A cable is recommended but never becomes a dead end.
- Explain why each requested value matters.
- Use familiar English and hide implementation details.
- Declining a repair does not prevent other repairs or the final report.
- Never show mock or fixture data in production mode.

## Safety requirements

- No device mutation in this milestone.
- Never read more data than the user selected or confirmed.
- Never infer a battery-health value.
- Never claim that software restores chemical battery capacity.
- A restart, restore, erase, uninstall, or security change can only be an
  explained future or official handoff, never an automatic action.

## Verification

- Add adapter contract tests and fixtures for every connection state.
- Add rule tests with positive, negative, missing, and contradictory evidence.
- Add end-to-end tests for all four symptom paths in connected and manual modes.
- Test disconnect, resume, decline, cancel, and corrupted local-session cases.
- Run formatting, strict linting, all tests, and a production build.
- Perform the manual smoke test in docs. If a real iPhone is available, execute
  and record the read-only connection matrix without storing personal data.

## Completion report

Report the exact supported macOS behavior, manual fallback behavior, checks run,
real-device evidence if available, and remaining gaps. Clearly distinguish
tested support from best effort. Do not stop at a plan.
