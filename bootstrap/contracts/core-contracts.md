# Core Contracts

## 1. CLAUDE.md Template

Generate root `CLAUDE.md` using this template. Fill in project rules and context pointer for this repo.

```
## .claude/ System

FIRST PRINCIPLES: Every statement must be backed by evidence — code you read, patterns you observed, or explicit user statements.

### MANDATORY 7-STEP WORKFLOW — DO NOT SKIP

**Every task MUST follow these 7 steps. This is not optional.**

**Think → Plan → Build → Review → Test → Ship → Reflect**

1. **Think** — Read the request. Gather context. Ask clarifying questions if ambiguous.
2. **Plan** — Break into subtasks. Identify affected files. Choose the simplest approach.
3. **Build** — Implement the plan. Write clean, minimal code following project conventions.
4. **Review** — Examine your code for bugs, edge cases, regressions.
5. **Test** — Run relevant tests. Fix failures. Add tests for new behavior.
6. **Ship** — Summarize changes for the user. Confirm the solution works. **STOP — you are not done. Proceed to Reflect.**
7. **Reflect** — Update `.claude/` docs if needed. State what changed or why nothing needed updating.

**Show each step label in your response. Your response is INCOMPLETE until ## Reflect is shown.** Trivial tasks may abbreviate steps 4-7, but steps 1-3 are never skippable.

### Project Rules

[Insert universal rules discovered from repo evidence here. These apply to ALL tasks. Keep concise — one line per rule. Concern-specific rules belong in the relevant skill's SKILL.md, not here.]

### Project Context

Read `.claude/context.md` for project overview, stack, architecture, and conventions.

### Commands
- `/update-claude-docs` — full `.claude/` audit
- `/fpt` — first-principles thinking mode
```

**CLAUDE.md must stay under 200 lines.** Only universal rules go here. Concern-specific rules go in skill files.

## 2. Per-Task Behavior

Before starting any task:
1. Read `CLAUDE.md` and follow the 7-step workflow.
2. Read relevant sections of `.claude/context.md`.
3. Claude Code will auto-activate matching skills based on the task.

Before finishing any task:
1. Scan user instructions for preferences/constraints; persist to CLAUDE.md (universal) or relevant skill (specific).
2. Check whether `.claude/` needs updating. Update in the same task.
3. State what changed or why nothing did.

## 3. Rule Learning

Scan every user message for implicit preferences, constraints, or conventions.

**Procedure:**
1. Parse the message for preferences, constraints, conventions, or architectural decisions.
2. Separate the TASK (what to do now) from the RULE (how things should always be).
3. Universal rules → add to CLAUDE.md "Project Rules" section.
4. Concern-specific rules → add to the relevant skill's SKILL.md.
5. Tell the user what you persisted and where.

**Examples:** "only access DB through models" → add to data-models skill | "never use default exports" → add to CLAUDE.md if universal

**Constraints:** Do not ask permission — just persist. Only persist project-specific decisions. If the user contradicts an existing rule, update it.

## 4. Self-Maintenance

- New concern in repo → create a new skill.
- Repo structure changed → update `context.md` and affected skills.
- Skills created/renamed/retired → no dispatch table to update (skills auto-trigger by description).
- Unused skill → fix its description or retire it.
- Never leave `.claude/` stale. Prefer small continuous updates.

## 5. Core Principles

**First-principles thinking.** Every `.claude/` file must be backed by evidence. If you cannot verify it, do not include it. Never use "likely", "probably", "should be" in `.claude/` files.

**Living system.** Skills must be created, expanded, revised, or simplified as the repo evolves — never left as static templates.

**User instructions are a source of truth.** When a user expresses a rule, persist it immediately.

## 6. Post-Install

After the bootstrap completes, **tell the user to restart Claude Code** (start a new session). CLAUDE.md is auto-loaded at session start — it does NOT activate mid-session. The `.claude/` system only takes full effect in the next session.
