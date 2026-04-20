# Capture Learnings

> Extract insights from chats into AI short-term memory. Paired with [Consolidate Learnings](consolidate-learnings.md) — together they form the AI memory cycle.

## The Memory Cycle

Capture and consolidate are two phases of one system:

> **When:** every 5 chats (or manual request)
> **Then:** scan chats → extract learnings → validate tags → dedup → write to `memory.md` (max 15)
> **Overflow:** > 15 items triggers [Consolidate Learnings](consolidate-learnings.md)

**Capture** fills the bucket. **Consolidate** empties it. The cycle keeps short-term memory sharp while building a searchable long-term archive.

## What It Creates

| File | Purpose |
|------|---------|
| `.ai-learn/memory.md` | Short-term memory (max 15 atomic learnings, always loaded) |
| `.ai-learn/.lock` | File lock to prevent race conditions |

## Auto-Trigger

Every **5 chat sessions** (counter-based). Also fires at session end when scratchpad shows `tasks: complete`.

## Triggers

**Manual:** "capture learnings", "remember this", "add to memory", "what did we learn?"

## Learning Types

| Type | Scope | Example |
|------|-------|---------|
| Principle | Universal | "Always check lock files before writing" |
| Abstract | Domain-wide | "React state updates are batched in event handlers" |
| Specific | Project-only | "This repo uses vitest, not jest" |

## Constraints

- **Never** exceed 15 learnings in `memory.md` — overflow triggers consolidation.
- **Never** write without checking `.ai-learn/.lock` first.
- Each learning is atomic: date, type, tags (max 3), one-line content.
- Tags validated: lowercase, single-word, 3-20 chars, starts with letter.
- Duplicates: exact match = skip, refinement = edit in place, related but distinct = add.

## Source Files

- Intent: `.intent-capture-learnings.md`
- Reference: `.reference-capture-learnings.md`
