# Security Filter

> Defense-in-depth hook that scans web-retrieved content for prompt injection. A seatbelt, not a force field.

## Flow

> **In:** web-fetched content (any tool call, MCP, or browser fetch)
> **Through:** pattern scan (regex + fuzzy + encoding) → sandbox (boundary markers) → output monitor (post-processing symptom check)
> **Out:** clean content, or user warning + incident log. User can always override with informed consent.

Three layers, each catching what the previous missed. Pattern scan and output monitoring run outside the context window.

## What It Creates

| File | Purpose |
|------|---------|
| `~/.ai-assist/security/incidents.log` | Audit trail of flagged content |
| `~/.ai-assist/security/patterns.json` | Updatable attack signature database |

## Auto-Trigger

Hooks into **every web fetch operation** (tool call, MCP, browser). Runs automatically.

## Triggers

**Manual:** "scan this for injection" (scan specific text), "security report" (view incident log)

## The Three Layers

| Layer | What it does | Where it runs |
|-------|-------------|---------------|
| Pattern Scan | Regex, fuzzy match, encoding detection against `patterns.json` | Before content enters context |
| Sandboxing | Wraps content in boundary markers (~3 lines added) | In context window |
| Output Monitor | Checks AI response for injection symptoms | After AI processes content |

## Constraints

- **Never** silently block content — always show user what was flagged and why.
- **Never** claim this is bulletproof — honest framing about limitations.
- `patterns.json` is refreshable without reinstalling.
- Sandboxing adds minimal context overhead (~3 lines).
- User can always override with informed consent.

## Source Files

- Intent: `.intent-security-filter.md`
- Reference: `.reference-security-filter.md`
