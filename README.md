# Enhanced OpenCode AGENTS.md

A production-grade global `AGENTS.md` for [OpenCode](https://opencode.ai) that synthesizes the behavioral guardrails and workflow discipline of the major coding harnesses — Claude Code, Codex, and Cursor — into one portable, provider-agnostic set of instructions: the behavioral layer you'd otherwise have to assemble yourself.

## What This Is

OpenCode reads `AGENTS.md` to govern how its agent behaves — when to confirm before acting, how to plan and verify, what "done" means, how to write and review code. Commercial harnesses like Claude Code and Codex get their polish from three things: the system prompt, a model they tune it to, and the surrounding mechanics — and of those, only the prompt is portable. This file ports that portable layer over, so you get much of their discipline while keeping OpenCode's open-source, multi-provider control.

Out of the box, OpenCode runs on a fairly general built-in prompt and ships without a global `AGENTS.md` — that file is yours to create. Its defaults also appear to lag the pace at which the commercial harnesses iterate on their own system prompts, which get refined release after release. So a lot of the behavioral polish those tools are known for simply isn't there until you add it. Arguably defaults like these belong in the harness itself; until they do, this file is a ready-made set of them, so you don't have to reconstruct them by hand.

It doesn't copy any single prompt, because no one of them is gospel — they contradict each other on things like verbosity and comment policy, and even OpenCode's own base reflects an earlier iteration of one. Copying one verbatim means inheriting its quirks. Instead, the rules here are **synthesized across Claude Code, Codex, and Cursor and filtered against OpenCode's own base prompts**: keep what the sources agree on, drop what conflicts, and resolve anything that fought the base.

That synthesis is what makes it portable. A commercial harness tunes its prompt to exactly one model; this file is written to hold up across whatever providers and models you point OpenCode at — load-bearing safety rules front-loaded, sections scoped to when they apply, conflicts with the underlying prompts removed — so behavior stays consistent whether you run one model or several.

One honest note on scope: this shapes *behavior*, not capability. It makes a model operate with more discipline — verify at runtime, stay in scope, never fabricate — but it won't raise the underlying model's ceiling or turn a small model into a frontier one.

**What's included:**

- Reversibility and blast-radius checks before destructive or out-of-tree actions
- A hard line against presenting unverified work as fact — no fabricated output, file contents, or APIs
- Right-sizing: the complete-but-not-expansive change in existing code (docs the change affects included), ambition on greenfield work
- Persistence — see a task through to a verified result before handing back
- Ambiguity handling that resolves itself first and escalates to you only when it can't and the stakes warrant
- Honest pushback under pressure: hold your reasoning, update on evidence, don't capitulate to displeasure alone
- Terse, signal-dense communication
- Task tracking via persistent todos — and when to skip it
- Subagent briefing principles
- Code quality: no defensive over-engineering, no backward-compat shims, root-cause fixes, readable code, typed edges (never `any`)
- Verification by runtime observation plus the project's real lint/typecheck — not just green tests
- Git conventions (Conventional Commits, stage by name, pre-commit-hook footgun warning)

## Installation

1. Copy `src/AGENTS.md` from this repo into `~/.config/opencode/AGENTS.md` (global) or into the root of any project (project-level).
2. Open a new OpenCode session — the agent will pick up the instructions automatically.

Project-level `AGENTS.md` files take precedence over the global one, so you can override specific sections per-project without touching the global defaults.

## Customization

The file is plain markdown with clearly labeled sections. Strip or replace any section that doesn't fit your workflow. Common edits:

- **Git conventions** — swap out Conventional Commits for your team's format
- **Communication style** — adjust the verbosity rules to taste
- **Code-quality opinions** — relax the stricter calls (for example, the `any` ban) for a project that needs them

## License

MIT