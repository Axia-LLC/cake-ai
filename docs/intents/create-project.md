# Create Project

> When a task spans multiple chats, scaffold an organized project folder with persistent context.

## Flow

Multi-chat task detected → Scaffold `my-projects/{date}-{slug}/` → Create README.md + scratchpad.md → Each session: load metadata, work, graduate insights → Tasks complete: archive scratchpad, README is permanent record

Two files, two roles: **README** is the human-facing permanent record (always loaded as metadata). **Scratchpad** is AI working memory (loaded when tasks incomplete, archived when done).

## What It Creates

| File | Purpose |
|------|---------|
| `my-projects/{YYYY-MM-DD}-{slug}/README.md` | Permanent record with YAML metadata (`load-to-context: always`) |
| `my-projects/{YYYY-MM-DD}-{slug}/scratchpad.md` | AI working memory with actionable checklist |
| `my-projects/` | Parent directory (created if missing) |

## Triggers

**Manual:** "build", "create", "implement", "design" + anything multi-chat; "new project", "let's start a project"

**Auto:** None — AI uses judgment to detect multi-chat scope and suggests scaffolding.

## Constraints

- **Never** create project folders for single-chat tasks.
- README metadata controls context loading — `load-to-context: always` means metadata only.
- Scratchpad is AI-only — user never edits it directly.
- README stays lean (~500 tokens of content).

## Source Files

- Intent: `.intent-create-project.md`
- Reference: `.reference-create-project.md`
