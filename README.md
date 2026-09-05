# iPhone Tune-Up

An open-source, privacy-first desktop assistant that helps people diagnose,
fix, and verify common iPhone battery and performance problems.

The normal workflow does not require a permanent iPhone app. A person opens the
desktop tool, connects an iPhone with a cable, approves the trusted-computer
prompt, selects a symptom, and follows a short evidence-based tune-up.

## What it is for

- Battery draining faster than expected
- A phone that feels slow or frequently becomes unresponsive
- Low available storage
- Excessive heat
- Repeated freezes, restarts, or app terminations
- Preparing a clear report before contacting Apple Support

## The product promise

The tool does more than display diagnostics. It turns evidence into a prioritized
repair plan, helps the person complete each safe action, and verifies the result.
It only claims an improvement when before-and-after evidence supports one.

Depending on the cause, a repair may mean freeing storage, changing a specific
app setting, updating iOS, creating a backup, handing off to an Apple repair
flow, or recommending battery service. It never presents memory cleaning or
generic percentage-based speed claims as real optimization.

## Typical use

1. Install the desktop application on a Mac.
2. Connect and unlock the iPhone, then tap **Trust**.
3. Choose a symptom and run a five-to-ten-minute check.
4. Review the evidence and the recommended actions.
5. Approve actions one at a time. The tool performs safe supported actions or
   guides the person through the exact iPhone or Apple utility screen.
6. Run an immediate verification check.
7. For battery-life changes, return after normal use for a delayed comparison.

Windows support follows the macOS release. An optional temporary iPhone helper
may be added later for tests that cannot be performed from the desktop. It must
never be required for the basic tune-up.

## Safety and platform boundaries

- Use public, documented platform capabilities for the supported path.
- Keep any independently implemented device-protocol adapter optional,
  capability-tested, and clearly labeled.
- Require explicit confirmation before every change.
- Back up before a destructive recovery workflow.
- Never erase, restore, uninstall, or change security settings silently.
- Keep diagnostic data local unless the person explicitly exports it.
- Do not promise access to data that Apple does not expose.

## Repository map

    docs/product.md                 Product definition and first-release scope
    docs/user-journey.md            End-to-end customer experience
    docs/architecture.md            Desktop and diagnostic architecture
    docs/remediation-catalog.md     Evidence-to-action rules
    docs/support-matrix.md          Supported platforms and capability levels
    docs/research.md                Source-backed platform constraints
    docs/adr/                       Architectural decisions
    prompts/                        Ordered GPT-5.6 Sol implementation tasks
    NEXT_SESSION.md                 Exact development handoff
    RUNBOOK.md                      Commands for running the tasks

## Status

Product and implementation design. The previous app-only concept has been
retired because an App Store app cannot diagnose or repair the rest of an
iPhone. Development starts with the feasibility and foundation task in
NEXT_SESSION.md.

## Language

The first release, all user-facing text, and the repository documentation are
English.

## License

MIT
