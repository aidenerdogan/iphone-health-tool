# Platform research

Last reviewed: 2026-09-05.

This document records the sources behind the product boundary. Recheck them
before changing device access, remediation, packaging, or marketing claims.

## Why the product is desktop-first

Apple's App Review Guidelines require apps to use public APIs and prevent an app
from reading or writing outside its designated container or changing the
functionality of other apps. An iPhone app therefore cannot truthfully serve as
a system-wide cleaner or repair tool.

Source:
https://developer.apple.com/app-store/review/guidelines/

## Supported computer workflows

Apple documents cable connection and the trusted-computer flow. Finder on macOS
and Apple Devices on Windows can display a connected device. Apple also
documents backup, update, and restore through these utilities.

Sources:

- https://support.apple.com/en-us/109054
- https://support.apple.com/en-ie/108392
- https://support.apple.com/en-us/HT212185
- https://support.apple.com/en-us/108967
- https://support.apple.com/guide/devices-windows/restore-your-device-to-factory-settings-mchl21d802fe/windows

These pages establish supported user workflows; they do not establish a public
third-party API for automating all Finder or Apple Devices operations. The
product must use a guided handoff where no documented integration exists.

## Actionable battery and performance evidence

iOS Battery identifies app and system activity, including on-screen,
background, low-signal, and notification-related use. Apple recommends Low
Power Mode for longer battery life and battery service when Battery Health shows
Service. Apple also notes that post-update background work may temporarily
affect battery life and thermal performance.

Sources:

- https://support.apple.com/guide/iphone/understand-iphone-battery-usage-health--iphd453d043a/ios
- https://support.apple.com/en-us/120745
- https://support.apple.com/en-us/101575

## Actionable storage and thermal evidence

Apple recommends maintaining at least 1 GB of available storage to avoid
slowdowns, provides iPhone Storage recommendations, and supports offloading an
app while retaining its documents. Apple also explains that a device can run
slower when it is too hot or cold.

Sources:

- https://support.apple.com/en-us/102598
- https://support.apple.com/en-us/108429

## Diagnostics

Apple documents iPhone Diagnostics Mode and publishes profiles and instructions
for collecting iOS logs, battery-life evidence, sysdiagnose, and related
diagnostics. These are appropriate advanced or support paths rather than the
first screen of a consumer tune-up.

Sources:

- https://support.apple.com/en-us/101944
- https://developer.apple.com/feedback-assistant/profiles-and-logs/?platform=ios

Xcode Power Profiler can measure app and overall-system power behavior but
requires a developer workflow and is not appropriate as the basic consumer
experience.

Source:
https://developer.apple.com/documentation/xcode/measuring-your-app-s-power-use-with-power-profiler

## Independent device protocols

libimobiledevice is an independent, cross-platform implementation of native iOS
device protocols. Its diagnostics interface describes GasGauge and NAND
queries. The project states that it is not authorized, sponsored, or approved
by Apple.

Sources:

- https://libimobiledevice.org/
- https://docs.libimobiledevice.org/libimobiledevice/latest/diagnostics__relay_8h.html

This makes it useful for an optional compatibility-tested adapter, but unsuitable
as the only path through the product.

## Product conclusions

- Basic use must work without a permanent iPhone app.
- Basic use must work without deep or experimental USB access.
- Every device capability is discovered at runtime.
- Unsupported automation becomes an exact guided or official handoff.
- Software cannot restore chemically aged battery capacity.
- Battery improvements require delayed verification under comparable use.
- Marketing must describe diagnostic and repair assistance, not generic cleaning.
