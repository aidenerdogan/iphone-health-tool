# Roadmap

## M0 — repository foundation

- Reproducible Xcode project and DiagnosticsCore package
- CI build and unit tests
- Architecture, contribution, security, and privacy documentation

## M1 — performance vertical slice

- Live thermal and low-power conditions
- One deterministic guided workload
- Session persistence and comparison
- Legacy MetricKit ingestion and fixture-driven report UI
- JSON diagnostic export

## M2 — battery vertical slice

- Battery level and charging-state history
- Energy-focused guided workload
- Session quality gates and invalid-comparison warnings
- Energy-related MetricKit normalization
- Battery findings backed by traceable evidence

## M3 — developer usefulness

- Import/export compatibility tests
- Signpost-based custom interval support
- Trend views by app and OS version
- Accessibility, localization, and privacy review

## Explicitly out of scope

- Battery-health or capacity estimation
- System-wide process monitoring
- Reading another app's resource or battery use
- Private APIs or jailbreak-only features
- Cloud accounts and telemetry in the initial releases
