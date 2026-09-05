# ADR 0001: Desktop-first guided tune-up

Status: Accepted

Date: 2026-09-05

## Context

The original concept was an iPhone application that measured its own process
using public iOS APIs. The intended customer outcome is broader: a person should
use the product infrequently, identify real causes of battery or performance
problems, complete safe repairs, and verify improvement.

An App Store application cannot inspect or modify the rest of the device. A
permanent mobile application also conflicts with the infrequent maintenance use
case.

## Decision

Build a desktop-first product with macOS as the first release and Windows as the
next platform. The normal flow uses a cable when helpful, supports manual
evidence fallback, and hands unsupported actions to exact iOS or official Apple
workflows.

Use a portable diagnostic and remediation core. Keep any independently
implemented USB protocol adapter optional, read-only initially, and isolated
behind runtime capabilities. Consider a temporary iPhone helper only after the
desktop MVP is useful without it.

## Consequences

- The old SwiftUI iPhone MVP prompts are retired.
- English desktop UX becomes the first deliverable.
- Product value is measured by completed, verified repairs rather than collected
  metrics.
- Some steps require user confirmation on the iPhone or in an Apple utility.
- The MVP can ship before deep USB diagnostics are reliable.
- Windows support can reuse the same core and most of the UI.
