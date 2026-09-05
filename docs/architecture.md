# Architecture

## Product definition

iPhone Health Tool is a developer-facing diagnostic companion. It explains how
the tool's own iOS process behaves under representative workloads and stores
system-provided reports for that process. It is not a system-wide task manager.

## Capability model

| Capability | Source | Timing | Notes |
| --- | --- | --- | --- |
| Battery charge and charging state | UIDevice | Live | Requires battery monitoring |
| Low Power Mode | ProcessInfo | Live | Observe power-state changes |
| Thermal state | ProcessInfo | Live | Nominal, fair, serious, critical |
| Performance benchmark | App-owned workloads | On demand | Comparable only under recorded conditions |
| CPU, GPU, memory, launch, hangs, disk, network | MetricKit | Delayed | Reports are system-generated and app-scoped |
| Export | Local store | On demand | Redacted JSON by default |

Every displayed value must show its source and collection time.

## Layers

    SwiftUI screens
          |
    Feature view models
          |
    Use cases / analysis policies
          |
    DiagnosticsCore domain models
          |
    Platform adapters + local persistence

### App

Owns navigation, dependency assembly, permissions/explanations, and SwiftUI
presentation. Proposed tabs:

- Overview: current device conditions and recent findings.
- Sessions: guided performance and energy benchmark runs.
- Reports: MetricKit history and diagnostic drill-down.
- Export: preview, redact, and share a diagnostic bundle.

### DiagnosticsCore

Contains domain models, collectors expressed as protocols, benchmark
coordination, scoring policies, report normalization, and export schemas. It
must build and test independently of the application UI.

### Platform adapters

- DeviceConditionsAdapter wraps UIDevice and ProcessInfo.
- LegacyMetricKitAdapter supports MXMetricManager on broadly deployed iOS
  versions.
- ModernMetricKitAdapter can adopt MetricManager behind availability checks.
- LocalReportStore persists versioned normalized records.
- DiagnosticExporter creates a documented, redacted JSON bundle.

## Data model

- DeviceConditionSample: timestamp, battery level/state, low-power mode,
  thermal state, app version, OS version, device class.
- BenchmarkSession: identifier, scenario, start/end, conditions, samples,
  interruptions, and result.
- NormalizedMetricReport: reporting window, source API version, app version,
  metric groups, and raw-payload reference.
- Finding: severity, evidence references, explanation, and suggested action.

Raw and normalized representations remain separate so future migrations do not
destroy source evidence.

## Accuracy principles

- Do not turn battery percentage change into an energy claim for short sessions.
- Do not compare benchmark sessions with materially different thermal,
  low-power, charging, app-version, or device conditions without warning.
- Report missing data explicitly.
- Use descriptive findings before introducing any composite score.
- Treat simulator output as UI/test data, not device-performance evidence.

## Privacy and security

- No backend is required.
- No advertising or analytics SDK.
- Export is user initiated.
- File paths, signpost text, and stack data are reviewed for sensitive values
  before export.
- Diagnostic schemas are versioned and documented.

## Decisions deferred to implementation

- Minimum supported iOS version after validating the current Xcode toolchain.
- SwiftData versus a file-backed store.
- Whether the optional modern MetricKit adapter should ship in the first release.
