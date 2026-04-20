# File Bloat Audit & Fixes

**Date:** 2026-04-18  
**Issue:** Violated economy and progressive disclosure principles

---

## Problem Identified

Created long files with ceremonial content that explains what we did or how to use things, rather than just providing the structure.

**Root cause:** Not following our own economy-first rule.

---

## Bloat Found & Fixed

### 1. Rules (agent/rules/)

**Before:** 100+ lines with verbose explanations  
**After:** 38-63 lines with YAML frontmatter + brief rule + link to references  

| Rule | Was | Now | Reduction |
|------|-----|-----|-----------|
| archive-dont-delete | - | 38 | New format |
| checkbox-inviolate | - | 38 | New format |
| economy-first | - | 38 | New format |
| git-branching-workflow | - | 45 | New format |
| no-destructive-git-operations | - | 39 | New format |
| hostile-input-scanner | 101 | 48 | 52% |
| rules-meta | - | 63 | New format |

**Total rules:** 309 lines (average 44 lines each) ✅

### 2. Template Files (my-projects/template/)

**Before:** 100+ lines with "Instructions for AI" sections  
**After:** 13-23 lines with just structure + one-liner footer

| File | Was | Now | Reduction |
|------|-----|-----|-----------|
| learnings.md | 103 | 17 | 83% |
| gleanings.md | 101 | 13 | 87% |
| scratchpad.md | 94 | 19 | 80% |
| readme.md | 59 | 23 | 61% |

**Bloat removed:** ~240 lines of ceremonial instructions

### 3. Top-Level Files

| File | Was | Now | Reduction |
|------|-----|-----|-----------|
| USERS.md | 101 | 23 | 77% |
| LEARNINGS.md | 64 | 19 | 70% |

**Bloat removed:** ~120 lines of placeholder examples

---

## Total Bloat Removed: ~360 lines

From ceremonial explanations that don't add value.

---

## What Was Bloat?

**Ceremonial content:**
- Multi-paragraph "Instructions for AI" sections in templates
- Verbose examples of "what goes here" in placeholder files
- Long explanations of rationale when the rule is self-evident
- Redundant "why this exists" sections that repeat the core rule

**Not bloat (kept):**
- YAML frontmatter (enables triggering)
- Core rule statement (essential)
- Quick reference bullets (scannable)
- Links to references (progressive disclosure)
- Actual examples (one good example, not 5)

---

## Principles to Prevent Bloat

### 1. Economy First Rule
Every line must earn its place. Cut:
- Explanations of what we did
- Instructions on how to use templates
- Placeholder examples
- Redundant rationale

### 2. Progressive Disclosure
- Brief rule (38-63 lines)
- Link to references/ for details
- Don't dump everything in one file

### 3. Self-Evident Structure
Templates should be obvious from structure alone:
```markdown
# File Name

## Section
- Example item

---

*One-line footer if needed*
```

No need for 40 lines explaining what goes in each section.

### 4. YAML Frontmatter
Rules use frontmatter for metadata:
```yaml
---
trigger: always | keywords
keywords: [if applicable]
alwaysApply: true/false
description: One-line summary
---
```

This enables smart loading without bloating the rule content.

---

## Rules Format (Final)

```markdown
---
trigger: always | keywords
keywords: [list]
alwaysApply: true
description: Brief summary
---

# Rule Name

## Core Rule 📋
2-3 sentence rule statement.

## Quick Reference 📋
- ✅ Do X
- ❌ Don't Y

## Details 🔬
See [references/RULE.md] for examples.
```

**Target:** 30-50 lines, 100 lines absolute max

---

## Lessons Learned

1. **We violated our own rules** - Created verbose files despite economy-first principle
2. **Templates don't need instructions** - Structure is self-evident
3. **Placeholder files should be minimal** - Auto-populated files don't need examples
4. **Progressive disclosure works** - Brief files + links to references

---

## Remaining Files to Audit

Files we kept long (justifiable):
- `README.md` (373 lines) - User-facing documentation, one-time read
- `QUICKSTART.md` (220 lines) - Setup guide, one-time read  
- `MANIFEST.md` (192 lines) - Package inventory, reference
- `AGENTS.md` (131 lines) - Could trim further, but is reference doc
- `agent-memory/SKILL.md` (179 lines) - Acceptable for skill (under 200)
- `agent-memory/references/*.md` (224-356 lines) - Reference docs, read on-demand

**Verdict:** These files serve specific purposes (user docs, reference materials, on-demand reading). Not bloat.

---

## High-Level Rule Created

Added to `rules-meta.md`:
- Rules must be 30-50 lines (100 max)
- YAML frontmatter required
- Link to references/ for details
- Progressive disclosure, not monolithic docs

---

## Summary

**Fixed bloat:**
- ✅ Restructured 7 rules (now 38-63 lines each)
- ✅ Cut template bloat (240 lines removed)
- ✅ Cut placeholder bloat (120 lines removed)
- ✅ Total: ~360 lines of ceremony eliminated

**Result:**
- Files are scannable
- Economy principle enforced
- Progressive disclosure works
- YAML frontmatter enables smart triggering

**Never again:** No more verbose explanations of what we did or how to use files. Structure is self-evident. Economy first.
