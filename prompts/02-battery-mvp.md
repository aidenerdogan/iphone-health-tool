# Task: build the battery diagnostics vertical slice

Continue this repository after the performance vertical slice. Read AGENTS.md,
README.md, the architecture and roadmap documents, the current implementation,
tests, and git status before changing anything. Preserve sound existing
decisions and user changes.

## Goal

Add a battery-focused vertical slice that records transparent device conditions,
runs a controlled energy-oriented session, explains relevant system-provided
metrics, and prevents misleading comparisons.

## Required behavior

1. Add a battery monitor using public UIDevice APIs for charge level and
   charging state. Enable monitoring only while needed and handle unknown data.
2. Observe Low Power Mode and thermal-state changes and record them in the
   session timeline.
3. Add one configurable, cancellable energy-oriented scenario using app-owned
   work. Keep the device responsive and bound the duration.
4. Record whether the device is charging, Low Power Mode changes, thermal
   transitions, app lifecycle interruptions, workload settings, and sample
   timestamps.
5. Add comparison eligibility rules. Warn or block direct comparisons when
   device class, app version, charging state, Low Power Mode, thermal state, or
   workload parameters make the evidence incompatible.
6. Normalize available energy-related MetricKit fields, including CPU/GPU,
   display, network, location, and runtime where present. Missing categories
   remain missing; never synthesize values.
7. Add Battery Session and Comparison screens with clear source labels and an
   accessible timeline.
8. Extend the versioned JSON export and its redaction tests.
9. Explain in the UI and documentation that the tool cannot read battery
   health, capacity, system-wide consumption, or another app's energy use.

## Accuracy constraints

- Battery percentage is a coarse device condition, not a direct power meter.
- Do not claim causal energy savings without comparable evidence.
- Do not publish a composite health or efficiency score in this milestone.
- Separate live samples, benchmark results, and delayed MetricKit reports.
- Never use private APIs, undocumented entitlements, or jailbreak assumptions.

## Verification

- Add unit tests for unknown battery values, state transitions, session
  interruption, comparison rules, normalization with missing fields, and export
  schema compatibility.
- Build the app and run the complete test suite.
- Document physical-device checks separately from automated verification.

## Completion report

Finish with what works, checks run, limitations that remain by design, and exact
physical-device validation steps. Do not stop at a plan or leave obvious
scaffolding unfinished.
