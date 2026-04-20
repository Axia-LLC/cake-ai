# Consolidate Learnings

> Archive overflow learnings and optimize tag structure. Paired with [Capture Learnings](capture-learnings.md) — together they form the AI memory cycle.

## Flow

> **When:** every 30 chats, or `memory.md` overflows past 15
> **Then:** backup → group overflow by topic → archive to `.ai-learn/archive/` → optimize tags (merge synonyms, prune unused) → update `index.md` → trim `memory.md` back to 15
> **First run:** asks once about workspace-level promotion, then respects the answer forever

See [Capture Learnings](capture-learnings.md) for the full memory cycle. Consolidation is the second phase — runs less frequently, handles the long-term archive.

## What It Creates

| File | Purpose |
|------|---------|
| `.ai-learn/archive/{topic}.md` | Semantically grouped long-term learnings |
| `.ai-learn/index.md` | Tag → archive file mapping |
| `.ai-learn/memory.md.backup-{timestamp}` | Safety backup before destructive operations |
| `~/.ai-assist/.workspace-ai-learn/` | Cross-project learnings (opt-in) |

## Auto-Trigger

Every **30 chat sessions** (counter-based).

## Triggers

**Manual:** "consolidate learnings", "archive memory"

Also fires when `memory.md` contains a "Pending Consolidation" note.

## Adaptive Thresholds

Archive file size limits scale with project age:

| Project Age | Max Learnings per Archive |
|-------------|--------------------------|
| < 3 months | 100 |
| 3–12 months | 200 |
| > 12 months | 500 |

## Constraints

- **Never** archive without creating a timestamped backup first.
- **Never** split or merge learning units during archive — atomic preservation.
- **Never** write without checking `.ai-learn/.lock` first.
- Max 3 tags per learning.
- Workspace consolidation: ask once, then respect `.no-workspace` flag.

## Source Files

- Intent: `.intent-consolidate-learnings.md`
- Reference: `.reference-consolidate-learnings.md`
