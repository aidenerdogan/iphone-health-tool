# Product definition

## One sentence

iPhone Tune-Up is a private desktop assistant that finds likely causes of
battery drain or poor performance, guides safe repairs, and verifies whether
the situation improved.

## Primary user

A nontechnical iPhone owner who has a concrete problem and wants to run the tool
once or at long intervals. The person should not need Xcode, command-line
knowledge, an account, or a permanently installed iPhone app.

## Jobs to be done

- Explain why the battery is draining faster than expected.
- Explain why the phone feels slow, hot, full, or unstable.
- Distinguish software, configuration, usage, storage, thermal, and battery-age
  causes.
- Complete the safest high-impact fixes with clear consent.
- Know when software cannot solve the problem and service is appropriate.
- Produce a useful support report without exposing unnecessary personal data.

## Product loop

1. Connect
2. Diagnose
3. Fix
4. Verify

Analysis without an actionable repair plan is incomplete. A repair without a
verification method is also incomplete.

## First-release scope

The English macOS MVP supports four symptom paths:

- Battery drains too quickly
- iPhone feels slow
- iPhone gets too hot
- Storage is almost full

It uses a cable-presence check, guided evidence entry, transparent diagnostic
rules, repair-plan ranking, exact on-device instructions, official Apple
handoffs, local session persistence, and before-and-after verification.

The MVP remains usable when the connected-device adapter can report only
presence. Deeper USB data, OCR, imported sysdiagnose parsing, a temporary iPhone
helper, and Windows packaging follow after the core workflow is validated.

## Outcome rules

The product may report:

- Improved
- Unchanged
- Worse
- Insufficient evidence
- Hardware or service action recommended

It must not promise a fixed percentage improvement. A short battery-level change
is not enough to prove longer battery life. Storage and software-version changes
can be verified immediately; battery outcomes require normal use and a delayed
comparison.

## Product principles

- Evidence before recommendation
- High-impact actions before cosmetic suggestions
- One clear decision per screen
- Plain English and no developer jargon
- Explicit consent for every change
- Reversible actions first
- Official Apple workflows for update, backup, restore, diagnostics, and service
- Local processing and minimal retention
- Honest limits instead of simulated precision

## Success criteria for the MVP

- A first-time user can finish a manual-fallback tune-up without documentation.
- Every finding links to its evidence and every action states its expected effect.
- The product works with a mock adapter in automated tests and without deep USB
  access in production.
- Declining an action or disconnecting the phone never blocks completion.
- No user-visible text outside tests is written in a language other than English.
- A completed session produces a readable local report and a valid verification
  state.
