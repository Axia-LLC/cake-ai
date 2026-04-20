# Workspace Prune

> Periodic workspace hygiene — scan for bloat, propose cleanup, execute with user approval.

## Flow

> **Phase 1:** Quick scan (skip `node_modules/`, `.git/`, `.archive/`) → brief summary to user
> **Phase 2** (if approved): Build checklist in `scratchpad.md` → execute item by item with user approval → archive (never delete)

Two phases: **scan** (always runs, low-cost) and **execute** (only with user approval, item by item). Every destructive action goes through archive-dont-delete.

## What It Creates

| Output | Purpose |
|--------|---------|
| Summary report | Quick scan results shown to user |
| `scratchpad.md` checklist | Thorough review action items (Phase 2 only) |

## Auto-Trigger

Every **30 chat sessions** (counter-based).

## Triggers

**Manual:** "review workspace", "clean workspace", "prune", "workspace hygiene", "check bloat"

## What It Detects

- Orphaned files (no imports, no references)
- Duplicate content
- Oversized documents
- Empty folders
- Stale scratchpads from completed projects

## Constraints

- **Never** delete files — always move to `.archive/`.
- **Never** rewrite files during pruning — move as-is.
- **Never** act without user approval on each checklist item.
- Skips: `node_modules/`, `.git/`, `.archive/`, `_bmad/`
- If BMAD not installed: offer install, custom path, or built-in fallback. Don't block.

## Source Files

- Intent: `.intent-workspace-prune.md`
- Reference: `.reference-workspace-prune.md`
