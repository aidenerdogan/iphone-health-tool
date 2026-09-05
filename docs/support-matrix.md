# Support matrix

## Product platforms

| Platform | Status | Basic tune-up | Deep USB data | Official utility handoff |
| --- | --- | --- | --- | --- |
| macOS | First release | Planned | Best effort, optional | Finder, Apple Diagnostics, Apple Support |
| Windows | Later release | Planned | Best effort, optional | Apple Devices, Apple Diagnostics, Apple Support |
| Linux | Not planned for first releases | Manual evidence only if added | Experimental only | Limited |
| iPhone app | Optional future helper | Not the primary product | App-owned data only | On-device instructions |
| Web | Not a diagnostic platform | Documentation only | No | Links only |

## Capability levels

- Supported: built on documented platform behavior and covered by release tests.
- Guided: the user performs an action in iOS or an Apple utility.
- Experimental: independent protocol implementation with runtime capability
  checks and no availability promise.
- Unavailable: the platform does not expose the capability safely.

## First-release evidence

| Evidence | macOS MVP | Source |
| --- | --- | --- |
| Cable/device presence | Supported or graceful manual fallback | Desktop adapter |
| Model and OS version | Only when safely available; otherwise user-confirmed | Device or manual |
| Available storage | User-confirmed first; read-only adapter later | iPhone Storage |
| Battery use by app/activity | User-confirmed | iPhone Battery |
| Battery health/service message | User-confirmed | iPhone Battery Health |
| Charging and heat condition | User-confirmed | Current device condition |
| Analytics or diagnostic file | Deferred to M2 | User-selected import |
| Gas gauge or NAND details | Experimental M3 only | Optional protocol adapter |

## Release policy

The basic tune-up must pass without experimental capabilities. A new iOS release
may disable an optional adapter without disabling symptom selection, manual
evidence, diagnosis, repair guidance, verification, or report export.
