# Repository instructions

- Read README.md, NEXT_SESSION.md, and every file in docs/ that is relevant to
  the task before changing product behavior.
- The product is desktop-first. A permanent iPhone app is not the primary
  experience.
- Keep the first release and all user-visible copy in English.
- Optimize for an infrequent five-to-ten-minute tune-up, not continuous
  monitoring or daily engagement.
- Preserve the connect, diagnose, fix, verify product loop.
- Use public, documented Apple capabilities for the supported path.
- Never make private frameworks or undocumented device protocols mandatory.
  Experimental adapters must be isolated, capability-probed, replaceable, and
  visibly labeled.
- Never use jailbreak assumptions, device fingerprinting, hidden background
  services, or misleading cleanup claims.
- Require explicit user confirmation for every mutation. Back up before any
  destructive recovery handoff.
- Represent evidence provenance and confidence explicitly. Do not infer missing
  values or present heuristics as measurements.
- Keep UI, workflow orchestration, diagnostic rules, remediation policies, and
  platform adapters separated.
- Keep the diagnostic and remediation core portable so Windows support does
  not require a rewrite.
- No account, advertising, analytics SDK, telemetry, or cloud upload in the
  first release.
- Prefer deterministic fixtures and adapters in tests. Hardware-only checks
  require a documented manual test plan.
- Update the support matrix, remediation catalog, and relevant ADR when a
  capability or product boundary changes.
- Run focused tests first, then formatting, linting, all tests, and a production
  build before finishing.
