# Task: build the performance diagnostics vertical slice

You are implementing the first usable vertical slice of this repository with
GPT-5.6 Sol. Work autonomously until the defined result is complete.

Start by reading AGENTS.md, README.md, docs/architecture.md, and
docs/roadmap.md. Inspect the installed Xcode and Swift toolchain before deciding
the minimum deployment target and project-generation approach. Record material
decisions in the repository.

## Goal

Create a buildable SwiftUI iPhone application plus a testable DiagnosticsCore
package. The first vertical slice must let a developer observe current device
conditions, run one repeatable app-owned performance workload, inspect a saved
session, and preview normalized MetricKit data from deterministic fixtures.

## Required behavior

1. Create a reproducible project that builds without a paid service.
2. Implement live thermal state and Low Power Mode observation using public
   Apple APIs.
3. Implement one cancellable, bounded benchmark scenario that exercises
   app-owned computation without freezing the main thread.
4. Capture session start/end times, device conditions, workload parameters,
   duration, interruptions, app version, OS version, and device class.
5. Persist sessions locally behind a protocol so tests can use an in-memory
   store.
6. Add a MetricKit ingestion boundary. Support the broadly available
   MXMetricManager API first; isolate newer MetricManager adoption behind
   availability checks and do not raise the minimum OS solely for it.
7. Normalize at least CPU, memory, launch/responsiveness, disk, and network
   fixture data into versioned domain models.
8. Build a small SwiftUI flow: Overview, Run Session, Session Detail, and
   Reports.
9. Make the source and timestamp of every metric visible. Fixture data must be
   labeled as sample data.
10. Export one redacted, versioned JSON diagnostic bundle and preview it before
    sharing.

## Product constraints

- Measure only this app and workloads run by this app.
- Never use private APIs or imply access to other apps.
- Do not invent precise energy consumption from battery percentage.
- Keep UI code thin and put logic in DiagnosticsCore.
- Keep raw MetricKit payloads separate from normalized records.
- Use accessible labels, Dynamic Type, and meaningful empty/error states.
- No analytics SDK, account system, backend, or network dependency.

## Verification

- Add meaningful unit tests for normalization, session comparison eligibility,
  cancellation, persistence boundaries, and export redaction.
- Use fixtures instead of waiting for system-delivered reports.
- Build the app and run all relevant tests.
- If a physical-device-only behavior cannot be exercised, document the exact
  manual verification step and verify the surrounding logic with tests.

## Completion report

Finish with a concise summary of what works, checks run, remaining physical
device checks, and any documented design decision. Do not stop after proposing
a plan.
