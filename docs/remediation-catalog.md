# Remediation catalog

This catalog defines what the first releases may recommend or perform. Each
implementation must preserve evidence, confirmation, reversibility, and
verification fields.

| Finding | First action | Execution mode | Verification |
| --- | --- | --- | --- |
| Critically low free storage | Review iPhone Storage recommendations and the largest unused apps | Guided iPhone action | Re-read or re-enter available storage |
| One app dominates background battery use | Review that app's Background App Refresh, location, and notification behavior | Guided iPhone action | Delayed Battery comparison |
| Battery health reports Service | Start an Apple battery-service handoff | Official handoff | Service outcome and later battery comparison |
| Issue began immediately after an iOS update | Explain that background post-update work may be temporary and schedule a later check | Informational | Delayed comparison |
| iOS update is available and symptoms persist | Back up, then update through the official flow | Official handoff | Confirm OS version and rerun symptom checks |
| Low Power Mode explains reduced responsiveness | Explain the tradeoff and let the user decide whether performance or battery life is the priority | Guided iPhone action | Confirm mode and repeat the relevant check |
| Device is thermally constrained | Stop the test, disconnect charging if appropriate, move to a moderate environment, and wait | Guided action | Thermal state or user-confirmed temperature after rest |
| Repeated freezes or restarts | Preserve evidence, update first, then use Apple Diagnostics or support | Official handoff | No immediate success claim; monitor recurrence |
| Restore is a justified last resort | Require a verified backup and hand off to the official recovery workflow | Official handoff | Restore completion and post-restore symptom check |

## Ranking policy

Candidate actions are ranked by:

1. Evidence confidence
2. Expected impact on the selected symptom
3. Safety and reversibility
4. Effort and time
5. Ability to verify

High-risk and destructive actions always rank below relevant reversible actions.

## Prohibited remediations

- Generic RAM cleaning
- Purging undocumented system caches
- Silent app deletion or offloading
- Silent settings changes
- Disabling security features
- Installing MDM for a personal tune-up
- Restarting, restoring, or erasing without a separate explicit flow
- Claiming battery capacity can be restored by software
- Claiming a percentage speed or battery improvement without comparable evidence

## Action contract

Every action definition includes:

- stable action ID;
- English title and explanation;
- triggering and contradicting evidence;
- supported execution modes;
- preconditions;
- expected effect;
- risk and reversibility;
- backup requirement;
- explicit confirmation copy;
- completion evidence;
- immediate or delayed verification method;
- official source link where applicable.
