# Package Tool

> Turn a working script or tool into a publishable npm/npx package.

## Flow

> **In:** a working script or tool the user wants to share
> **Through:** analyze existing code → propose structure (user refines) → scaffold files → `npm pack --dry-run` (loop until clean)
> **Out:** publishable npm package with `package.json`, bin entry, README, LICENSE

## What It Creates

| File | Purpose |
|------|---------|
| `package.json` | Package metadata, bin entry, dependencies |
| `bin/` or entry point | CLI entry with shebang |
| `.gitignore` | If missing |
| `.npmignore` | Keeps published package clean |
| `LICENSE` | User's choice of license |
| `README.md` | Install and usage instructions |

## Triggers

**Manual:** "package this", "make this an npm package", "publish this", "how do I share this tool?"

**Auto:** None — always user-initiated.

## Constraints

- **Never** overwrite existing files without asking — analyze first.
- **Always** dry run before suggesting publish.
- Ask guided questions with examples ("What should this be called? e.g., 'markdown-to-doc'").
- Minimal additions — a simple script needs less packaging than a framework.

## Source Files

- Intent: `.intent-package-tool.md`
- Reference: `.reference-package-tool.md`
