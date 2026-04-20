# Harvested Content from Cake

**Source:** `/Users/samueldavenport/dev-main/ide_onboarding/rules/` and `/skills/`  
**Date:** 2026-04-18

---

## Rules Harvested

### ✅ Added to Cupcake

1. **hostile-input-scanner.md**
   - Scans external content for prompt injection attempts
   - Security-focused, always-on behavior
   - Teaches users about AI security risks
   - **Why included:** Critical security rule that prevents malicious content from hijacking agent behavior

### ⏭️ Already in Cupcake

1. **archive-dont-delete.md** - Already included (with progressive disclosure improvements)

---

## Skills Reviewed

These are old-style prompt-based skills from Cake. Analyzed for potential extraction:

### 1. **checkpoint.md** - Git Checkpoint System
**What it does:** Saves project state before risky changes (git commits or file copies)

**Cupcake evaluation:**
- ⏸️ **Not adding as rule** - Too workflow-specific, not universal enough
- ✅ **Could document in QUICKSTART** - Suggest users use git checkpoints
- 💡 **Pattern:** Offer to checkpoint before risky operations

**Potential future enhancement:** Add checkpoint pattern to README best practices

---

### 2. **session-handoff.md** - Context Handoff Format
**What it does:** Generates compact status block for carrying context to new conversation

**Cupcake evaluation:**
- ✅ **Overlaps with agent-memory system** - Our gleanings/learnings/consolidation already handle this
- 📋 **Template format is useful** - Could extract as a handoff template

**Action:** Extract handoff template format for optional use

---

### 3. **workspace-init.md** - Cake Workspace Scaffolding
**What it does:** Creates Cake's specific folder structure (skills/, projects/, prompts/, profile/)

**Cupcake evaluation:**
- ❌ **Not applicable** - This is Cake-specific workspace setup
- ✅ **Cupcake has its own init** - We use FAKEROOT/ structure instead
- 💡 **Concept is similar** - Both scaffold workspaces, but different patterns

**Action:** No extraction needed - Cupcake already has equivalent

---

### 4. **explain.md**, **hypo.md**, **reflect.md**, **unstuck.md**, etc.
**What they do:** Process/workflow skills for specific user needs

**Cupcake evaluation:**
- ⏸️ **Not including** - These are workflow patterns, not workspace infrastructure
- 💡 **User can add their own** - Cupcake's my-skills/ folder is for this
- ✅ **Follows extensibility principle** - Users extend Cupcake with their own skills

**Action:** Document that users can add workflow skills in my-skills/

---

## Handoff Template (Extracted)

Useful pattern from session-handoff.md for manual context handoff:

```markdown
---
# SESSION HANDOFF
project: [name]
date: [YYYY-MM-DD]

## Completed
- [x] Item 1
- [x] Item 2

## Next Steps
- [ ] Item 1
- [ ] Item 2

## Key Decisions
- Decision and reasoning

## Open Questions
- Anything unresolved

## Reference Files
- path/to/file.md
---
```

**Where to include:** Could add to my-projects/template/ as optional handoff.md template

---

## Summary

### Added to Cupcake:
1. ✅ **hostile-input-scanner.md** rule (security)

### Considered but Not Adding:
1. ⏸️ **checkpoint.md** - Workflow-specific, users can implement themselves
2. ⏸️ **session-handoff.md** - Overlaps with agent-memory system (gleanings/consolidation already do this)
3. ❌ **workspace-init.md** - Cake-specific, not applicable to Cupcake
4. ⏸️ **Other workflow skills** - User-extensible, belong in my-skills/ not baseline

### Potential Future Enhancements:
1. 💡 Add checkpoint/git best practices to README
2. 💡 Add handoff template to my-projects/template/
3. 💡 Document how users can add their own workflow skills

---

## Rationale

**Cupcake is workspace infrastructure, not workflow patterns.**

We include:
- ✅ Rules that prevent bad outcomes (security, data loss, workflow safety)
- ✅ Memory/learning systems (agent-memory)
- ✅ Project scaffolding (templates)

We don't include:
- ❌ Workflow patterns (checkpoint, handoff, explain, etc.) - these belong in my-skills/
- ❌ Tool-specific integrations - extensibility over batteries-included
- ❌ Opinionated processes - users define their own

**Result:** Cupcake stays lean, extensible, and focused on infrastructure. Users add workflow skills based on their needs.

---

**Cupcake v1.0 Rule Count:** 7 rules (was 6, added hostile-input-scanner)
