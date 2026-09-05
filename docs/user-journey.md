# User journey

## 1. Welcome

The first screen says what the tool can do and what it cannot do. The primary
action is **Start a Tune-Up**. No account, subscription prompt, or background
monitoring request appears.

## 2. Choose the problem

The person chooses one or more symptoms:

- Battery drains too quickly
- iPhone feels slow
- iPhone gets too hot
- Storage is almost full
- iPhone freezes or restarts

The app estimates the time required and identifies whether a cable is useful.

## 3. Connect

The default path asks the person to:

1. Connect the iPhone with a cable.
2. Unlock it.
3. Tap **Trust** on the iPhone if asked.

The screen shows separate states for waiting, locked, trust required,
connected, unsupported, and connection lost. A **Continue without connection**
option starts the manual-evidence path.

## 4. Collect minimum evidence

The tool asks only for evidence relevant to the selected symptom. Each step
shows an illustration or precise path and explains why the value matters.

Examples:

- Settings > Battery
- Settings > Battery > Battery Health
- Settings > General > iPhone Storage
- Current charging state
- Whether the issue began after an iOS update
- Whether the phone is currently hot
- Recent unexpected shutdowns

The person reviews every detected or entered value before diagnosis.

## 5. Diagnose

The result screen answers three questions:

1. What is most likely happening?
2. What evidence supports that conclusion?
3. What should be done first?

Findings are ordered by likely impact, confidence, safety, and effort. Missing
evidence is visible and does not become an invented conclusion.

## 6. Repair plan

The plan contains a small number of actions. Every action shows:

- expected benefit;
- evidence that triggered it;
- time estimate;
- whether it is reversible;
- whether a backup is needed;
- what will change;
- how the result will be checked.

The person confirms actions individually. Declining an action does not block the
rest of the tune-up.

## 7. Complete actions

Actions use one of these experiences:

- The desktop tool performs a local safe action.
- The tool gives an exact, step-by-step iPhone instruction.
- The tool hands off to Finder, Apple Devices, Apple Diagnostics, or Apple
  Support.
- The tool recommends service when software cannot restore battery capacity or
  hardware performance.

Destructive recovery is never a one-click optimization. It requires a backup,
an explicit risk explanation, and a separate official workflow.

## 8. Verify

The tool repeats immediately verifiable checks. It then classifies the result as
improved, unchanged, worse, or insufficient evidence.

For battery life, the user can save the session and return after two to seven
days of normal use. The delayed comparison must account for different usage,
charging, thermal, and software conditions.

## 9. Finish

The final screen contains:

- completed actions;
- declined or unfinished actions;
- verified outcomes;
- remaining concerns;
- whether service is recommended;
- a local report export;
- a **Delete session data** action.

The tool does not ask to stay running in the background.
