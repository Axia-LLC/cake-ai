---
current_counter: 0
last_updated: 2026-04-18T00:00:00Z
---

# Agent Counter Register

This file tracks the chat counter and defines periodic consolidation tasks.

## Counter Programs

| Modulo | Period | Action | Description |
|--------|--------|--------|-------------|
| 5 | Every 5 chats | `glean-chat` | Extract learnings, decisions, and key abstractions from current chat |
| 15 | Every 15 chats | `consolidate-gleanings` | Merge all gleaning files into learnings-primary.md |
| 50 | Every 50 chats | `review-critical` | Review all learnings to update USERS.md and AGENTS.md |
| 100 | Every 100 chats | `deep-consolidation` | Deep review and pruning of all learning files |

## How It Works

1. **Start of turn:** `counter-increment.py` runs, increments counter by 1
2. **End of turn:** `counter-check.py` runs, checks counter % period for each row
3. If remainder is 0, execute the corresponding action
4. Each action is defined as a skill in `~/my-skills/`

## Counter State

Current counter: **0**  
Last updated: 2026-04-18T00:00:00Z
