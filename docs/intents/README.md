# Intent System

Intents are compact skill blueprints. Each one describes *what* a skill should do, and points to a reference file that shows *exactly how* to do it. When you install Cake AI, your AI assistant reads each intent, translates the reference into its native skill format, and installs it.

**Why intents instead of pre-written skills?** Because every AI assistant has a different format. Intents let one definition work across Cursor, Cline, Windsurf, Claude Code, Copilot, Kiro, and Aider.

## How Translation Works

```
Intent (.intent-*.md)          →  describes what, when, constraints
Reference (.reference-*.md)    →  shows exactly how (production-quality example)
Your AI                        →  translates reference to its native skill format
```

The golden rule: **Translate, Don't Create.** The AI preserves all specificity from the reference. It doesn't simplify, summarize, or reinterpret.

## Intent Index

| Intent | Auto-Trigger | Description |
|--------|-------------|-------------|
| [archive-dont-delete](archive-dont-delete.md) | Always-on rule | Move files to `.archive/` instead of deleting |
| [hypo](hypo.md) | Every 5 chats | Systematic hypothesis-driven debugging |
| [create-project](create-project.md) | None | Scaffold organized project folders for multi-chat work |
| [capture-learnings](capture-learnings.md) | Every 5 chats | Extract insights from chats into AI short-term memory |
| [consolidate-learnings](consolidate-learnings.md) | Every 30 chats | Archive overflow learnings, optimize tags |
| [workspace-prune](workspace-prune.md) | Every 30 chats | Periodic workspace hygiene and bloat detection |
| [package-tool](package-tool.md) | None | Turn a working script into a publishable npm package |
| [security-filter](security-filter.md) | On web fetch | Multi-layer defense against prompt injection |
| [explain](explain.md) | Setup + always-on | IDE onboarding: stealth explanations, scavenger hunt, deep dives |
| [baker](baker.md) | None | Scaffold structured agents, rules, skills, workflows, steering files |

## Pre-Built Skills

Some skills are too interaction-heavy for intent translation — they require tone calibration, pacing, and judgment that a reference can't fully capture. These ship as hand-crafted skills:

- **explain-onboard** — always-on stealth explanations (part of the explain system)
- **unstuck** — emotional calibration, escalation ladder
- **checkpoint** — Git integration, teaching moments
- **session-handoff** — summarization judgment
- **reflect** — conversational pacing, journey integration
- **skill-builder** — meta-skill teaching
- **workspace-init** — narration, micro-teaching, Git opt-in UX
