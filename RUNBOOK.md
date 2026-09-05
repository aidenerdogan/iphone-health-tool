# GPT-5.6 Sol runbook

Run tasks from the repository root and review each result before starting the
next phase.

## 1. Feasibility and foundation

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/00-feasibility-and-foundation.md

## 2. macOS guided tune-up MVP

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/01-macos-guided-tuneup.md

## 3. Remediation and verification

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/02-remediation-and-verification.md

The exact new-session handoff and acceptance gates are in NEXT_SESSION.md.
