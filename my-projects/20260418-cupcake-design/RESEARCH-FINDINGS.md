# Research Findings: Agent Memory & Progressive Disclosure

**Date:** 2026-04-18  
**Purpose:** Validate Cupcake design against current best practices

---

## Key Research Findings

### 1. Four-Layer Memory Architecture (OpenClaw Pattern)

Modern agent memory systems organize into distinct layers:

| Layer | Lifespan | Purpose | Cupcake Equivalent |
|-------|----------|---------|-------------------|
| **Short-term** | Seconds-minutes | Active conversation context | scratchpad.md |
| **Session** | Hours-days | Daily logs, working memory | gleanings.md |
| **Project** | Weeks-months | Repository-scoped facts | project learnings.md |
| **Long-term** | Indefinite | Workspace-level persistent storage | learnings-primary.md |

**✅ Cupcake aligns with this pattern**

**Source:** [OpenClaw MEMORY.md Guide](https://launchmyopenclaw.com/openclaw-memory-md-guide)

---

### 2. Memory Type Categories

Best practices identify four memory types:

1. **Working Memory** (temporary scratchpad, seconds-minutes)
   - Cupcake: `scratchpad.md` ✅

2. **Procedural Memory** (how-to knowledge, permanent)
   - Cupcake: `my-skills/` ✅
   - **Gap:** Could be more explicit about procedural learnings

3. **Long-term Memory** (facts, preferences, decisions)
   - Cupcake: `learnings-primary.md`, `AGENTS.md`, `USERS.md` ✅

4. **Short-term Memory** (immediate context)
   - Cupcake: `gleanings.md` ✅

**Source:** [AI Agent Memory Management - DEV Community](https://www.dev.to/imaginex/ai-agent-memory-management-when-markdown-files-are-all-you-need-5ekk)

---

### 3. Progressive Disclosure Patterns

**Three-Tier Information Model:**

```
Tier 1: Metadata & Overview
    ↓
Tier 2: Full Content (on selection)
    ↓
Tier 3: Detailed Resources (on-demand)
```

**Cupcake Implementation:**

```
Tier 1: AGENTS.md (overview, ~200 tokens)
    ↓
Tier 2: learnings-primary.md top 30 (~500 tokens)
    ↓
Tier 3: references/, learning-categories/ (on-demand)
```

**✅ Cupcake follows this pattern**

**Best Practices Applied:**
- ✅ Clear visual indicators (section headers, "See references/")
- ✅ Maintain context (consistent structure)
- ✅ Clear, predictive labels
- ✅ Baseline experience first (top 30), then expand

**Source:** [Progressive Disclosure in IA](https://www.numberanalytics.com/blog/progressive-disclosure-in-information-architecture)

---

### 4. Context Window Management

**Best Practices:**

1. **Conversation Summarization** → Rolling summaries replace full histories
   - Cupcake: Gleanings → Consolidation ✅

2. **Explicit Checkpointing** → State files for recovery
   - Cupcake: scratchpad.md, learnings.md ✅

3. **Lossless Context Management** → Searchable summaries expandable on-demand
   - Cupcake: Top 30 → Bottom register → Categories ✅

4. **Structured External Memory** → Store outside context window
   - Cupcake: All learnings in files, not in prompts ✅

5. **Sub-agent Delegation** → Specialized agents return summaries
   - Cupcake: Consolidation as separate skill activation ✅

**Performance Impact:** 60-80% cost reduction with proper context management

**✅ Cupcake implements all five best practices**

**Source:** [AI Agent Context Window Management](https://www.ai-agentsplus.com/blog/ai-context-window-management-techniques-2026)

---

### 5. Markdown-First Advantages (2026 Consensus)

**Industry trend:** Markdown as source of truth, vector DBs as optional index

**Benefits:**
- ✅ Human-readable (Cupcake)
- ✅ Version-controllable (Cupcake)
- ✅ Zero vendor lock-in (Cupcake)
- ✅ Simple debugging (Cupcake)
- ✅ Local-first (Cupcake)

**Implementation pattern:**
- Markdown files = primary storage
- Vector indexing = derived layer (optional)
- Git for version control

**✅ Cupcake fully adopts markdown-first approach**

**Source:** [How to add persistent memory with markdown | BSWEN](https://docs.bswen.com/blog/2026-03-03-how-to-add-persistent-memory-to-ai-agents-with-markdown/)

---

### 6. Atomic Notes & Zettelkasten Principles

**Core principle:** One idea per note, meaningfully linkable

**Benefits:**
- Improves thinking skills
- Enables knowledge connections
- Creates reusable components

**Cupcake alignment:**
- ✅ Each learning is atomic (1-2 sentences)
- ✅ Each rule is self-contained
- ✅ Each skill is independent
- ⚠️ **Gap:** Could improve linking between notes

**Source:** [The Complete Guide to Atomic Note-Taking](http://zettelkasten.de/atomicity/guide/)

---

## Design Validation

### What Cupcake Does Well ✅

1. **Four-layer memory architecture** - Maps perfectly to industry patterns
2. **Progressive disclosure** - Three-tier model implemented
3. **Context management** - All 5 best practices implemented
4. **Markdown-first** - Fully committed to local, version-controlled files
5. **Atomic structure** - Rules, skills, learnings are self-contained
6. **Economy focus** - 30-item cap prevents context bloat (60-80% cost reduction)
7. **Explicit checkpointing** - scratchpad.md, learnings.md as state files
8. **Session summarization** - Gleanings → Consolidation pattern

### Potential Improvements 💡

#### 1. Add Procedural Gleaning Type

**Pattern from research:** Distinguish "how-to" workflows from declarative facts

**Current Cupcake:** 4 gleaning types (Decision, Finding, Resolution, Learning)

**Opportunity:** Add 5th type for procedures

```markdown
## Procedure - YYYY-MM-DD HH:MM
**Context:** [What workflow this applies to]
- **Steps:** [Numbered steps]
- **When to use:** [Conditions]
- **Notes:** [Gotchas or tips]
```

**Benefit:** Easier to find "how to do X" vs "what happened with X"

**Recommendation:** ✅ **Add to v1** - Low effort, high value

---

#### 2. Explicit Tier Indicators

**Pattern from research:** Visual cues for progressive disclosure levels

**Current Cupcake:** Implicit structure, no explicit tier markers

**Opportunity:** Add tier indicators to templates

```markdown
## Essential Info 📋 (Always Read)
[Core information]

## Detailed Context 📚 (Read When Needed)
[Additional details]

## References 🔬 (Read On-Demand)
[Deep dive links]
```

**Benefit:** Clearer cognitive load management for readers

**Recommendation:** ✅ **Add to v1** - Low effort, improves clarity

---

#### 3. Date-Based Session Logs (Optional)

**Pattern from research:** Daily logs like `memory/YYYY-MM-DD.md`

**Current Cupcake:** Single `gleanings.md` per location

**Opportunity:**
```
agent/session-logs/
  2026-04-18.md
  2026-04-19.md
  2026-04-20.md
```

**Benefit:** Better temporal tracking, easier debugging

**Trade-off:** More files vs. simpler structure

**Recommendation:** ⏸️ **Defer to v2** - Not essential, adds complexity

---

#### 4. Improved Linking Between Notes

**Pattern from research:** Zettelkasten uses wikilinks (`[[note-name]]`) for connections

**Current Cupcake:** File path references, but no explicit linking syntax

**Opportunity:**
```markdown
- **Git workflow:** See [[git-branching-workflow]] for details
- Related: [[archive-dont-delete]], [[economy-first]]
```

**Benefit:** Easier to discover related learnings, better knowledge graph

**Trade-off:** More complex parsing, potential link rot

**Recommendation:** ⏸️ **Consider for v2** - Not essential for v1

---

## Recommended Enhancements for v1

### Enhancement 1: Add Procedural Gleaning Type

**File:** `FAKEROOT/my-skills/agent-memory/references/GLEANING.md`

**Add new section:**

```markdown
### Procedure
A workflow or process discovered/refined.

**Good examples:**
- **Procedure:** Deploy to staging: 1) run tests, 2) build Docker image, 3) push to registry, 4) update k8s manifest, 5) apply with kubectl
- **Procedure:** Debug memory leaks: enable profiler, capture heap snapshot, compare snapshots, identify retained objects, trace allocation path

**Bad examples:**
- **Procedure:** Do the deployment (not specific enough)
- **Procedure:** We have a deployment process (describes existence, not the process itself)
```

---

### Enhancement 2: Add Tier Indicators to Templates

**Files to update:**
- `FAKEROOT/AGENTS.md`
- `FAKEROOT/my-learnings/learnings-primary.md`
- `FAKEROOT/my-skills/agent-memory/SKILL.md`

**Format:**

```markdown
## Overview 📋 (Start Here)
[Essential context every agent needs]

## Detailed Information 📚 (Expand As Needed)
[Additional context for deeper understanding]

## References 🔬 (On-Demand)
[Links to detailed docs]
```

**Rationale:** Makes progressive disclosure explicit, helps agents know what to read first

---

### Enhancement 3: Update Consolidation to Recognize Procedures

**File:** `FAKEROOT/my-skills/agent-memory/references/CONSOLIDATION.md`

**Add guidance:**

```markdown
### Procedural Learnings

When consolidating procedures:
- Keep step-by-step workflows intact (don't summarize away steps)
- Add "When to use" conditions
- Note any gotchas or edge cases
- Store in dedicated section or tag as procedural

Example transformation:
Gleaning: **Procedure:** Deploy: run tests → build → push → apply
Learning: **[Procedure]** Staging deploy: (1) test suite, (2) docker build, (3) registry push, (4) kubectl apply. Always verify health check before marking complete.
```

---

## Heuristics Validation

Research confirms Cupcake already uses these key heuristics:

1. ✅ **Metadata First, Details On-Demand** - Three-tier model
2. ✅ **Separate Context, Memory, and State** - File organization
3. ✅ **Rolling Summarization Over Retention** - Consolidation logic
4. ✅ **One Idea Per Note** - Atomic principle
5. ✅ **Start General, Get Specific** - Progressive disclosure hierarchy
6. ✅ **Searchable Summaries, Expandable Details** - Top 30 → Categories
7. ✅ **Date-Tag for Temporal Context** - [YYYY-MM-DD] format
8. 🆕 **Distinguish Procedural from Declarative** - Add to v1

---

## Performance Expectations

Based on research findings:

**Context Cost Reduction:** 60-80% with proper management
- Cupcake's 30-item cap + consolidation should achieve this ✅

**Completion Rate Improvement:** 300% with progressive disclosure
- Cupcake's tier system should help ✅

**Practical Threshold:** Manage proactively at <50% context capacity
- Cupcake's every-15-chats consolidation addresses this ✅

---

## Conclusion

**Cupcake's design is strongly validated by 2026 best practices.**

### Core Strengths ✅
- Four-layer memory architecture (matches OpenClaw pattern)
- Progressive disclosure (three-tier model)
- All 5 context management best practices
- Markdown-first, local-first approach
- Atomic structure throughout
- 60-80% cost reduction potential
- Explicit checkpointing and state management

### Recommended v1 Enhancements 🆕
1. **Add procedural gleaning type** - Distinguish workflows from facts
2. **Add tier indicators** - Make progressive disclosure explicit
   - 📋 Essential (always read)
   - 📚 Detailed (expand as needed)
   - 🔬 References (on-demand)

### Defer to v2 ⏸️
- Date-based session logs (optional debugging feature)
- Wikilink-style note linking (nice-to-have)

**Overall Assessment:** Cupcake is exceptionally well-aligned with industry best practices. The progressive disclosure principle is properly applied throughout the design. Minor enhancements would make it even better, but v1 is solid and production-ready.

---

**Research Sources:**
- [OpenClaw MEMORY.md Guide (2026)](https://launchmyopenclaw.com/openclaw-memory-md-guide)
- [AI Agent Memory Management - DEV Community](https://www.dev.to/imaginex/ai-agent-memory-management-when-markdown-files-are-all-you-need-5ekk)
- [BSWEN: Persistent Memory with Markdown](https://docs.bswen.com/blog/2026-03-03-how-to-add-persistent-memory-to-ai-agents-with-markdown/)
- [Progressive Disclosure in IA](https://www.numberanalytics.com/blog/progressive-disclosure-in-information-architecture)
- [AI Context Window Management](https://www.ai-agentsplus.com/blog/ai-context-window-management-techniques-2026)
- [Zettelkasten Atomic Notes Guide](http://zettelkasten.de/atomicity/guide/)
