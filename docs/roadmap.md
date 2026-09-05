# Roadmap

## M0 — feasibility and foundation

- Confirm the desktop stack and packaging approach
- Build the English desktop shell and portable Rust core
- Implement the tune-up session state machine
- Define versioned evidence, finding, remediation, and verification models
- Add mock, manual-evidence, and USB-presence adapters
- Record supported and experimental capability decisions

## M1 — macOS guided tune-up MVP

- Cable connection and trusted-computer onboarding
- Manual fallback when no device data is available
- Symptom flows for battery drain, slowness, heat, and low storage
- Evidence-driven diagnostic rules
- Prioritized repair plan with per-action confirmation
- Guided iPhone steps and official Finder/Apple Support handoffs
- Immediate verification and local English report

## M2 — remediation depth

- User-selected Battery, Battery Health, and Storage evidence
- Safe backup and update handoff
- Delayed battery verification
- Resume an interrupted tune-up
- Import selected analytics and diagnostic files
- Redacted support bundle export

## M3 — optional deeper diagnostics

- Read-only libimobiledevice feasibility and compatibility matrix
- Optional, clearly labeled native-protocol adapter
- Optional temporary iPhone helper for bounded tests
- Physical-device test lab and release gates

## M4 — Windows

- Windows packaging and Apple Devices onboarding
- Reuse the portable diagnostic and remediation core
- Platform-specific handoffs and device-presence adapter
- Cross-platform session and report compatibility

## Explicitly out of scope

- Generic RAM or cache cleaning claims
- Guaranteed percentage improvements
- Continuous monitoring or background daemons
- Silent deletion, uninstall, restore, or security-setting changes
- Reading another app's private container
- Requiring private Apple frameworks or jailbreak access
- MDM enrollment for personal users
- Cloud accounts, remote source upload, advertising, or telemetry
