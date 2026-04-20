# Archive Don't Delete

> AI never deletes files. When asked to delete, remove, or clean up, move files to `.archive/` instead.

## Flow

User says "delete" → AI intercepts → Move to `.archive/` → Confirm with file paths → (undo? restore from `.archive/`)

Always-on behavioral rule — fires every time a delete, remove, or cleanup request is detected. No auto-trigger.

## What It Creates

| File/Dir | Purpose |
|----------|---------|
| `.archive/` | Contains all "deleted" files, preserving original folder structure |

## Triggers

**Keywords:** "delete", "remove", "get rid of", "clean up", "archive"

## Constraints

- AI **never** deletes files. No exceptions.
- Only the user can delete from `.archive/`.
- Original folder structure is preserved (`src/old.tsx` → `.archive/src/old.tsx`).
- `.gitignore` updated to include `.archive/` if Git is present.

## Source Files

- Intent: `.intent-archive-dont-delete.md`
- Reference: `.reference-archive-dont-delete.md`
