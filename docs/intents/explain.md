# Explain

> IDE onboarding system — stealth explanations, scavenger hunt, and on-demand deep dives backed by official docs.

One install decision creates **three skills** that form a lifecycle:

## The Explain Lifecycle

> **Phase 1 — Setup** (runs once): fetch + cache IDE docs → generate scavenger hunt (essentials + advanced)
> **Phase 2 — Onboard** (always-on): stealth explanations in parentheticals → offer side quests on unchecked hunt items → essentials complete? teach user to disable
> **Phase 3 — On-Demand** (invoke only): user says "explain X" → structured deep dive backed by cached docs

## The Three Phases

| Phase | Skill | Type | When it runs |
|-------|-------|------|-------------|
| **Setup** | `setup-explain` | Intent-generated | Once, on install |
| **Onboard** | `explain-onboard` | **Pre-built** (too interaction-heavy for intents) | Always-on until essentials complete |
| **On-Demand** | `explain-feature` | Intent-generated | User invokes "explain X" |

**Why is onboard pre-built?** It requires tone calibration (stealth, not lecture), pacing judgment (when to offer side quests vs. stay quiet), and emotional sensitivity (encouraging without being patronizing). A reference file can't capture that.

## What It Creates

| File | Purpose |
|------|---------|
| `~/.ai-assist/explain/docs/` | Cached IDE documentation (shared across projects) |
| `~/.ai-assist/explain/scavenger-hunt.md` | Essentials (above the line) + advanced (below the line) |

## Triggers

**Setup:** Runs once on install, or "setup explain"

**Onboard:** Always-on at session start. Auto-disables when above-the-line items complete.

**Feature:** "explain X", "explain this", "side quest on X"

## The Scavenger Hunt

The hunt file has two sections separated by a line:

- **Above the line:** Essential IDE concepts every user needs (e.g., "what git commit does", "what a terminal is")
- **Below the line:** Advanced topics for when the user is curious (e.g., "how LSP works", "what tree-sitter does")

Items are small learning nuggets, not broad topics.

## Constraints

- Explanations live in parentheticals within normal chat — never separate sections or bullet lists.
- Never ask open-ended questions without an example response.
- Side quests are offered, never forced.
- Encouraging but factual tone — no sycophancy, no misinformation.
- If offline during setup: note it, retry next online session.
- No dependency on the learnings system (fully atomic).

## Source Files

- Intent (setup): `.intent-explain.md` → `.reference-setup-explain.md`
- Intent (feature): `.intent-explain.md` → `.reference-explain-feature.md`
- Pre-built (onboard): `.reference-explain-onboard.md` — copy and adapt format only
