# Learnings - Cupcake Design

**Purpose:** Permanent record of key insights and decisions for this project

---

## Key Decisions

- **[2026-04-18]** FAKEROOT/ is literal package folder for distribution (not conceptual)
- **[2026-04-18]** Use "my-" prefix for folders (differentiates from external projects)
- **[2026-04-18]** gleanings.md is temporary (pruned every 15 chats), learnings.md is permanent
- **[2026-04-18]** Template folder contains instructive examples (compact templating without separate skills)
- **[2026-04-18]** Ship with two skills: agent-memory (custom) + skill-creator (from Anthropic)
- **[2026-04-18]** learnings-primary.md has 30-item cap on top register (economy principle)
- **[2026-04-18]** Counter system uses modulo arithmetic (5, 15, 50, 100) to trigger consolidation actions
- **[2026-04-18]** No automatic expiry for learnings (manual archive if irrelevant)

---

## Design Philosophy

- **[2026-04-18]** Five core principles: Atomic structure, Adaptability, Economy, Usefulness, Robustness
- **[2026-04-18]** Zero-context ready: any stateless agent should be productive from turn one
- **[2026-04-18]** Economy over completeness: combat context bloat through aggressive consolidation
- **[2026-04-18]** Lightweight process: common sense over rigid rules

---

## Technical Insights

- **[2026-04-18]** Counter scripts use Python to read/write YAML frontmatter in counter-register.md
- **[2026-04-18]** One gleaning session can create multiple files in different locations (project, workspace, skills)
- **[2026-04-18]** Scoring learnings: value+criticality (HIGH 40% each), complexity+breadth (MEDIUM 10% each)
- **[2026-04-18]** NOT using frequency-of-reference (too complex, breadth covers it)
- **[2026-04-18]** NOT using recency (not valuable for scoring)
- **[2026-04-18]** Follow agentskills.io specification for all skills (YAML frontmatter + markdown body)

---

## Agent-Memory System

- **[2026-04-18]** Gleaning types: Decision, Finding, Resolution, Learning (flexible taxonomy)
- **[2026-04-18]** Consolidation flow: project gleanings → project learnings; workspace gleanings → learnings-primary
- **[2026-04-18]** 30-item cap enforced via scoring + demotion to bottom register
- **[2026-04-18]** Category creation: use kebab-case, merge when sensible, use common sense
- **[2026-04-18]** Critical promotion criteria: "Do ALL zero-context agents need this?" (AGENTS.md) or "Useful user info?" (USERS.md)
- **[2026-04-18]** Four actions: glean-chat (5), consolidate-gleanings (15), review-critical (50), deep-consolidation (100)

---

## Rules System

- **[2026-04-18]** Three atomic rules: archive-dont-delete, checkbox-inviolate, economy-first
- **[2026-04-18]** Archive rule: move to z_archive/ instead of deleting (safety over cleanup)
- **[2026-04-18]** Checkbox rule: checked = done (reference only), unchecked = must resolve before proceeding
- **[2026-04-18]** Economy rule: prioritize brevity, eliminate redundancy, maintain focus
- **[2026-04-18]** Added git-branching-workflow: always use feature branches (feature/, fix/, refactor/), never commit to main
- **[2026-04-18]** Added no-destructive-git-operations: never force push, hard reset, or destructive ops without explicit approval
- **[2026-04-18]** Added hostile-input-scanner: scan external content for prompt injection attempts, alert user when suspicious patterns found
- **[2026-04-18]** Added rules-meta: meta-rules about rule design (atomic, progressive disclosure, actionable)
- **[2026-04-18]** Harvested content from Cake (reviewed 9 skills, added hostile-input-scanner rule)
- **[2026-04-18]** FIXED: Restructured all 7 rules to be brief (38-63 lines, was 100+) with YAML frontmatter and progressive disclosure
- **[2026-04-18]** FIXED: Cut bloat from template files (was 100+ lines with ceremonial instructions, now 20-30 lines)
- **[2026-04-18]** FIXED: Cut bloat from USERS.md (101→19 lines), LEARNINGS.md (64→15 lines)

---

## Folder Structure

- **[2026-04-18]** Projects use date prefix: YYYYMMDD-[topic-name] for chronological organization
- **[2026-04-18]** Each project has: readme, scratchpad, learnings, gleanings (temp), z_archive
- **[2026-04-18]** Skills follow agentskills.io structure: SKILL.md + optional references/, scripts/, assets/
- **[2026-04-18]** Top-level files: AGENTS.md (for agents), USERS.md (about user), LEARNINGS.md (overview)
- **[2026-04-18]** my-learnings/ has structured format: learnings-primary.md + learning-categories/

---

## Process Notes

- **[2026-04-18]** Keep consolidation lightweight - use common sense over rigid rules
- **[2026-04-18]** No counting-based promotion (too much overhead) - use scoring criteria instead
- **[2026-04-18]** Gleanings format: type, date/time, context, decided/found/resolved/learned/procedure
- **[2026-04-18]** Template files are instructive (explain what to do, not just structure)
- **[2026-04-18]** Progressive disclosure: metadata (~100 tokens) → SKILL.md (<5000 tokens) → references (as needed)
- **[2026-04-18]** Research validation: Added procedural gleaning type (5th type) to distinguish "how-to" workflows
- **[2026-04-18]** Research validation: Added tier indicators (📋📚🔬) to make progressive disclosure explicit

