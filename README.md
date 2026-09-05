# iPhone Health Tool

An open-source, privacy-first iOS developer tool for understanding an app's
performance, energy behavior, and device conditions on real iPhones.

The project combines two related product tracks:

1. **Performance diagnostics** — launch responsiveness, hangs, CPU, memory,
   disk writes, network activity, and thermal pressure.
2. **Battery diagnostics** — battery state, low-power mode, energy-related app
   metrics, and repeatable benchmark sessions.

## Product boundary

iOS apps are sandboxed. This tool measures its own process, benchmarks that run
inside the app, and MetricKit reports delivered for this app. It does not claim
to read battery health, inspect other apps, or replace Instruments and Xcode
Organizer.

## Planned experience

- A live dashboard for battery, power, and thermal state.
- Guided performance and energy benchmark sessions.
- Daily MetricKit report history and diagnostic details.
- Local JSON export for reproducible bug reports.
- Clear provenance on every metric: live sample, benchmark result, or delayed
  system report.
- On-device storage by default, with no account and no analytics SDK.

## Repository layout

    App/                         SwiftUI application target
    Packages/DiagnosticsCore/    Testable collection and analysis domain
    docs/architecture.md         Product and technical design
    docs/roadmap.md              Milestones and scope
    prompts/                     GPT-5.6 Sol implementation tasks
    RUNBOOK.md                   Commands for running the prompts

## Status

Design scaffold. Run the performance prompt first, followed by the battery
prompt. See RUNBOOK.md.

## License

MIT
