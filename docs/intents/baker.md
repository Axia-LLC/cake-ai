# Baker

> Scaffold structured agents, rules, skills, workflows, or steering files using progressive disclosure.

## Flow

> **When:** user says "create a rule", "make an agent", "new skill", "create a workflow", or "steering file"
> **Then:** identify type → gather requirements (one question at a time) → preview → approve → generate → register in manifest
> **Fallback:** no existing structure? offer standalone artifacts or minimal scaffolding

## Artifact Types

| Type | Format | Location |
|------|--------|----------|
| **Rule** | `.mdc` with YAML frontmatter (description, globs, alwaysApply) | `.cursor/rules/` |
| **Agent** | `.md` with XML activation sequence, persona, menu, config loading | `agents/` |
| **Skill** | `SKILL.md` — thin wrapper that loads an agent or workflow | `.cursor/skills/{name}/` |
| **Workflow** | `workflow.md` + step files (just-in-time loading, sequential) | `workflows/` |
| **Steering file** | `.md` with scope, audience, rules, examples | Project root or module dir |

## Operating Contract

Every generated artifact follows these principles:

- Ask one question at a time, confirm before advancing
- Load config before substantive output
- Registry-first routing through manifests
- Keep state in files, not implicit memory
- Define outputs as explicit contracts for downstream phases

## What It Creates

The artifact itself, plus a row in the appropriate manifest CSV (`agent-manifest.csv`, `workflow-manifest.csv`, `files-manifest.csv`). Rules and skills are self-discoverable and don't need manifest entries.

## Triggers

**Manual:** "create a rule", "make an agent", "new skill", "create a workflow", "steering file", "create instructions", "baker"

**Auto:** None — artifact creation is always user-initiated.

## Constraints

- **Never** dump all questions at once — progressive disclosure, one at a time.
- **Never** write files without showing a preview and getting approval first.
- **Never** skip manifest registration if a manifest system exists.
- **Always** match existing project patterns — if structured artifacts already exist, use their format exactly.
- **Never** generate agents without the XML activation sequence — it's what makes agents work.
- **Never** generate workflows as monoliths — break into step files.

## Source Files

- Intent: `.intent-baker.md`
- Reference: `.reference-baker.md`
