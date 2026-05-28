# Enhanced OpenCode AGENTS.md

A production-grade `AGENTS.md` for [OpenCode](https://opencode.ai) that ports in the best behavioral guardrails and workflow patterns from Claude Code's system prompt among others.

## What This Is

OpenCode reads `AGENTS.md` to govern how its AI agent behaves — parallel tool use, confirmation gates, communication style, code quality rules, and more. This file distills the Claude Code defaults into explicit, portable instructions your agent will actually follow.

**What's included:**

- Reversibility checks and blast-radius awareness before destructive actions
- Parallel tool call discipline (independent calls always in the same message)
- Terse, signal-dense communication style with no emoji
- Task tracking rules (when to use todos vs. when not to)
- Blocker handling — surface, don't silently workaround
- Subagent prompting principles
- Code quality rules: no defensive over-engineering, no backward-compat shims, no what-comments
- Self-review checklist after every implementation
- Verification protocol (runtime observation, not just tests)
- Git conventions (Conventional Commits, stage by name, pre-commit hook footgun warning)

## Installation

1. Copy `src/AGENTS.md` from this repo into `~/.config/opencode/AGENTS.md` (global) or into the root of any project (project-level).
2. Open a new OpenCode session — the agent will pick up the instructions automatically.

Project-level `AGENTS.md` files take precedence over the global one, so you can override specific sections per-project without touching the global defaults.

## Customization

The file is plain markdown with clearly labeled sections. Strip or replace any section that doesn't fit your workflow. Common edits:

- **Git conventions** — swap out Conventional Commits for your team's format
- **Communication style** — adjust verbosity rules to taste

## Why Not Just Use Claude Code?

Claude Code embeds these behaviors natively. OpenCode doesn't — it's more of a blank slate. This file makes OpenCode behave closer to Claude Code's defaults while keeping you on whichever model or provider OpenCode is configured to use.

## License

MIT
