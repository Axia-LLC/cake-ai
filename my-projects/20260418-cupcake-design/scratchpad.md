# Scratchpad - Cupcake Design

**Purpose:** Temporary working document for plans, analysis, and task tracking

---

## Current Working Items

### Folder Structure Analysis

**CONFIRMED Structure:**
```
FAKEROOT/                               # Package folder (literal, for distribution)
  my-projects/
    readme.md                           # Overview of projects
    template/
      YYYYMMDD-[topic-name]/            # Template example (AI copies this)
        readme.md                       # Instructions for project readme
        scratchpad.md                   # Instructions for scratchpad use
        learnings.md                    # Instructions for permanent learnings
        gleanings.md                    # Instructions for temporary gleanings
        z_archive/                      # Archive folder (never delete)

  my-skills/                            # User's skill definitions

  my-dev/                               # Development workspace

  agent/                                # Agent infrastructure
    rules/                              # Atomic rule files
    scripts/                            # Helper scripts (Python, etc.)
    hooks/                              # Hook definitions
    counter-register.md                 # Counter state + program table

  AGENTS.md                             # Critical info for AI agents
  USERS.md                              # Critical info about user
  LEARNINGS.md                          # Workspace-level learnings
  my-learnings/                         # Learning consolidation
    learning-categories/                # Categorized learnings
    learnings-primary.md                # Top 30 + infinite bottom
```

**Decisions Made:**
- ✅ FAKEROOT/ is a literal folder for packaging/distribution
- ✅ Template is populated with instructions (compact templating without separate skills)
- ✅ gleanings.md (not duplicate learnings.md) for temporary consolidation
- ✅ Use "my-" prefix to differentiate from external projects/folders
- ✅ Project-specific learnings stay in project folders, workspace learnings in top-level files

---

### Agent-Memory System Design

**Components:**

1. **Counter Register** (`agent/counter-register.md`)
   - YAML frontmatter with current counter
   - Table mapping modulo operations to actions
   - Example: counter % 5 = 0 → glean chat
   
2. **Counter Script** (Python)
   - Reads counter from YAML
   - Increments by 1
   - Writes back to file
   - Triggered by: start-of-turn hook
   
3. **Counter Check Script** (Python + small AI call)
   - Reads current counter
   - Checks modulo against table
   - Executes corresponding action if remainder = 0
   - Triggered by: end-of-turn hook

**Consolidation Cadence:**
- Every 5 chats → Glean current chat for learnings
- Every 15 chats → Consolidate gleaning files into learnings-primary.md
- Every 50 chats → Review all learnings, update USERS.md / AGENTS.md

**Decisions Made:**

- ✅ **Gleaning Storage:** Both project-level AND workspace-level
  - One gleaning session can create multiple files in different locations
  - Project gleanings: `my-projects/20260418-topic/gleanings.md`
  - Workspace gleanings: `gleanings.md` (at root)
  - Category gleanings: `my-skills/gleanings.md`, `my-dev/gleanings.md`, etc.
  - Files are TEMPORARY - only exist between prunings

- ✅ **Gleaning Format:** Optimized for economy + thoroughness
  ```markdown
  ## [Gleaning Type] - YYYY-MM-DD HH:MM
  **Context:** [Project/concern/category]
  - **Decided:** X
  - **Found:** Y
  - **Resolved:** Z
  - **Learned:** W
  ```
  - Include taxonomy (type) but stay flexible - don't force fit
  - Keep concise, balance thoroughness with brevity

- ✅ **Consolidation Flow:** BOTH project and workspace
  - Project gleanings → project `learnings.md` (flat file)
  - Workspace gleanings → `my-learnings/learnings-primary.md` (structured)
  - Category gleanings → category-specific files in `my-learnings/learning-categories/`
  - Global learnings are most plentiful (need robust category system)

- ✅ **30-Item Cap:** Option A or D - AI chooses/scores
  - Mechanism defined in `my-skills/agent-memory/SKILL.md`
  - AI must evaluate relative value and demote lower-priority items

- ✅ **Category Strategy:** Option A - AI decides
  - Mechanism defined in `my-skills/agent-memory/SKILL.md`
  - AI creates categories dynamically based on content patterns

- ✅ **Critical Criteria:** Needs mechanism
  - Defined in `my-skills/agent-memory/SKILL.md`
  - Criteria for promoting to USERS.md/AGENTS.md

---

### Economy & Anti-Bloat Mechanisms

**Design Principles:**
- **Atomic structure** - Each rule, skill, learning is self-contained
- **Adaptability** - System adjusts to different project types
- **Economy** - Aggressive pruning, hierarchical storage
- **Usefulness** - Only keep what's actionable or critical
- **Robustness** - System survives interruptions, works with zero context

**Proposed Mechanisms:**
1. **30-item cap** on learnings-primary.md top register
2. **Categorized overflow** to learning-categories files
3. **Periodic consolidation** forces review and pruning
4. **Gleaning → Primary → Categories → USERS/AGENTS** hierarchy
5. **AI prompts** emphasize brevity and elimination of redundancy

**Questions to resolve:**
- [ ] What's the format of learnings-primary.md? (markdown list? table?)
- [ ] How do we prevent category files from bloating?
- [ ] Should there be a max size for USERS.md / AGENTS.md?
- [ ] How do we handle conflicts between old and new learnings?
- [ ] What's the demotion strategy (top → bottom → category)?

---

### Checkbox Rule

**Core Rule:** Checkboxes are inviolate
- ✅ Checked = finished, reference only
- ☐ Unchecked = must be resolved before moving on
- AI must always resolve applicable checkboxes before new work

**Questions to resolve:**
- [ ] How does AI determine "applicable" checkboxes?
- [ ] Should this be enforced at file level or workspace level?
- [ ] What happens if a checkbox is blocked? (escalate to user?)

---

### Archive Rule

**Core Rule:** Never delete, always archive
- Any deletion → move to `z_archive/` folder
- Only user can request deletion
- AI never removes files, only archives

**Questions to resolve:**
- [ ] Archive within project folder or global archive?
- [ ] Should archive be timestamped or keep original structure?
- [ ] How long do archives persist?

---

## Cupcake Ships With

**Skills (follows agentskills.io spec):**
1. `my-skills/agent-memory/` - Learning consolidation system
2. `my-skills/skill-creator/` - From Anthropic's exemplar (https://github.com/anthropics/skills/tree/main/skills/skill-creator)

**Reference:** https://agentskills.io/specification

---

## Next Steps

- [x] Finalize folder structure
- [x] Confirm consolidation flow (both project + workspace)
- [x] Define gleaning taxonomies (Decision, Finding, Resolution, Learning, Procedure)
- [x] Design agent-memory SKILL.md structure (complete with 4 reference docs)
- [x] Spec out learnings-primary.md structure (top 30 + bottom + categories)
- [x] Create counter-register.md format (YAML + table + metadata)
- [x] Design counter scripts (counter-increment.py and counter-check.py)
- [x] List all atomic rules needed (7 rules: archive, checkbox, economy, git-branching, git-safety, hostile-input, rules-meta)
- [x] Design template folder contents (readme, scratchpad, learnings, gleanings)
- [x] Package Cupcake for distribution (complete FAKEROOT structure)
- [x] Add Cursor hooks for counter automation
- [x] Harvest rules from Cake (added hostile-input-scanner)
- [x] Research validation (against 2026 best practices)
- [x] FIX BLOAT: Restructure rules to 38-63 lines with YAML frontmatter
- [x] FIX BLOAT: Cut ceremony from templates (83-87% reduction)
- [x] FIX BLOAT: Trim placeholders (70-77% reduction)
- [ ] Test installation process
- [ ] Final review for any remaining bloat

---

## Agent-Memory Skill Design

**Location:** `my-skills/agent-memory/SKILL.md`

**Components to define:**

1. **Gleaning Taxonomies**
   - Decision (architectural, technical, process)
   - Finding (bug, optimization, insight)  
   - Resolution (blocker removed, problem solved)
   - Learning (pattern, technique, principle)
   - [Others?]

2. **30-Item Cap Mechanism**
   - **Scoring criteria (weighted):**
     - **Value to project** (HIGH) - how useful is this to the work?
     - **Criticality/Usefulness** (HIGH) - is this essential or nice-to-have?
     - **Complexity** (MEDIUM) - if hard to rediscover, keep it
     - **Breadth of applicability** (MEDIUM) - applies to one project or many?
     - ❌ NOT recency (not valuable)
     - ❌ NOT frequency of reference (too complicated, breadth covers it)
   - Demotion logic: score items, move lowest to bottom register
   - Merge opportunity detection: identify similar items that can be consolidated

3. **Category Creation Logic**
   - Use **kebab-case** naming (e.g., `learnings-git-workflows.md`)
   - Merge into existing categories when it makes sense
   - Use **common sense** - no rigid rules
   - Keep it **lightweight, easy, repeatable**
   - Avoid over-process

4. **Critical-Info Promotion Criteria**
   - ❌ NOT based on counting (too much overhead)
   - Same scoring as pruning (value, criticality, complexity, breadth)
   - **Key questions:**
     - "Do ALL zero-context, stateless agents need to know this about how they should work?"
     - "Is this useful info about the users that agents should know?"
   - Focus on **cold-start effectiveness** - what helps new agents be productive immediately?

5. **Expiry / Aging**
   - ❌ NO automatic expiry
   - Manual archive if irrelevant
   - Keep everything unless explicitly moved to archive

---

## Ideas & Notes

- Gleaning types should be flexible - AI can adapt taxonomies based on actual usage
- Consider adding metadata to learnings (last referenced date, reference count)
- Should learnings have expiry? (e.g., after 6 months without reference, auto-demote?)
- Multi-workspace: gleanings.md should be workspace-specific (no cross-workspace pollution)
- Consider using TOML for counter-register instead of YAML?
- Hooks should be IDE-agnostic where possible (or provide adapters)
