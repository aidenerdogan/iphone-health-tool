# GPT-5.6 Sol runbook

Run the prompts in order from this repository root. High reasoning is selected
for implementation work; the model also supports higher settings if a later
task proves unusually difficult.

## 1. Performance vertical slice

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/01-performance-mvp.md

## 2. Battery vertical slice

    codex exec -m gpt-5.6-sol -c 'model_reasoning_effort="high"' --approve-for-me -C . - < prompts/02-battery-mvp.md

Commit and review the first result before running the second command.
