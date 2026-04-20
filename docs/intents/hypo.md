# Hypothesis-Driven Debugging

> Systematic debugging using the scientific method. Replaces guessing with structured hypothesis → test → validate cycles.

## Flow

> **When:** test fails 2+ times, or user is stuck in trial-and-error
> **Then:** hypothesis → predict → isolate → test one change → full suite (loop on failure)
> **Escape:** Five Whys after 2 failed hypotheses — stop at first uncertainty

## Auto-Trigger

Every **5 chat sessions**, the counter checks context for stuck signals:
- "didn't work", "still failing", "same error", "tried multiple", "not working"

If detected, AI **suggests** `/hypo` to the user. Never auto-runs.

## Triggers

**Manual:** "run hypo", "/hypo", "hypothesis debugging"

## Constraints

- **One hypothesis, one change, one validation.** No simultaneous changes.
- **Never** skip the full test suite — isolated tests hide cascading failures.
- **Stop** Five Whys at first uncertainty — never speculate past what's confirmed.
- Output is concise: one sentence per step, no educational filler.

## Source Files

- Intent: `.intent-hypo.md`
- Reference: `.reference-hypo.md`
