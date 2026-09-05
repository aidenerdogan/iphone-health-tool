# Repository instructions

- Read README.md, docs/architecture.md, and docs/roadmap.md before changing code.
- Preserve the privacy-first, on-device product boundary.
- Use public Apple APIs only. Never add private API access, jailbreak
  assumptions, device fingerprinting, or claims about other apps.
- Keep collection, persistence, analysis, and presentation separated.
- Put reusable logic in DiagnosticsCore and keep SwiftUI views thin.
- Use protocol-backed platform adapters so MetricKit versions and test doubles
  can coexist.
- Label delayed MetricKit reports separately from live measurements.
- Prefer deterministic tests. Do not make tests wait for real MetricKit delivery.
- Update architecture and roadmap documents when a design decision changes.
- Run the smallest relevant tests first, then the full project checks before
  finishing.
