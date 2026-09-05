# Next development session

Use a new Codex session opened at this repository. Select GPT-5.6 Sol with high
reasoning.

## Before starting

1. Pull the latest main branch.
2. Confirm the working tree is clean.
3. Read AGENTS.md, README.md, all documents in docs/, and this file.
4. Do not begin with the optional iPhone helper or experimental USB protocols.

## Session 1 objective

Complete M0: feasibility and foundation. The outcome must be a buildable English
desktop application with a portable tested core, not another design document.

Run:

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/00-feasibility-and-foundation.md

Review the result and commit it only after:

- the desktop app launches;
- the English first-run flow is visible;
- a mock tune-up can reach a completed report;
- the manual-evidence fallback works;
- core tests, frontend tests, linting, and a production build pass;
- the implementation does not require deep USB access.

## Session 2 objective

Complete the macOS guided tune-up MVP:

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/01-macos-guided-tuneup.md

Use a real iPhone for the manual test plan if one is available. Do not weaken
automated tests when hardware is unavailable.

## Session 3 objective

Add the first remediation and verification depth:

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/02-remediation-and-verification.md

## Product acceptance gates

- A nontechnical user can complete a useful tune-up without Xcode or Terminal.
- The basic workflow survives missing USB capabilities.
- Every recommendation points to evidence.
- Every mutation requires explicit confirmation.
- Destructive recovery requires a backup and official handoff.
- Battery claims use delayed, comparable evidence.
- All first-release UI is English.
- No account, telemetry, cloud upload, or permanent background process exists.

## Later work

Only after the macOS MVP is useful:

1. Evaluate read-only libimobiledevice integration behind an experimental flag.
2. Evaluate a temporary iPhone helper for a narrowly defined missing capability.
3. Add imported diagnostic parsing.
4. Build the Windows adapter and package using the same core.
