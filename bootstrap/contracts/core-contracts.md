# Core Contracts

## 1. CLAUDE.md Template

The bootstrap agent must generate the root `CLAUDE.md` using this template, filling in the dispatch table with actual files created for this repo.

```
## .claude/ System — Central Guidance

You are operating inside a managed `.claude/` system. This file tells you what to load based on the task.

FIRST PRINCIPLES: Write nothing based on assumptions. Every statement must be backed by evidence — code you read, patterns you observed, or explicit user statements.

### MANDATORY 7-STEP WORKFLOW — DO NOT SKIP

**Every task MUST follow these 7 steps. This is not optional.**

**Think → Plan → Build → Review → Test → Ship → Reflect**

1. **Think** — Read the request. Gather context. Ask clarifying questions if ambiguous.
2. **Plan** — Break into subtasks. Identify affected files. Choose the simplest approach.
3. **Build** — Implement the plan. Write clean, minimal code following project conventions.
4. **Review** — Examine your code for bugs, edge cases, regressions.
5. **Test** — Run relevant tests. Fix failures. Add tests for new behavior.
6. **Ship** — Summarize changes. Confirm the solution works. Leave the codebase clean.
7. **Reflect** — Assess the outcome. Auto-update `.claude/` docs.

**Show each step label in your response.** Trivial tasks may abbreviate steps 4-7, but steps 1-3 are never skippable. For full step details, read `skills/task-execution/SKILL.md`.

### How to use this file

1. Read the user's task.
2. Follow the 7-step workflow above.
3. Match the task against the dispatch table below.
4. Read ONLY the files listed for that task type.

### Dispatch table

| Task type | Rules | Agent | Skill | Context |
|-----------|-------|-------|-------|---------|
| [fill per repo] | `rules/...` | `agents/...` | `skills/...` | section in `context.md` |
| Any task (always) | ALL `rules/` | — | `skills/task-execution/SKILL.md` | — |

**Always read ALL rules.** Rules are hard constraints loaded in full. Agents and skills are loaded selectively.

### After any task — validate and learn

1. Re-read all rules and check your work against each. Fix violations.
2. Extract user-expressed preferences/constraints to `.claude/rules/`.
3. Update `.claude/` if your changes affect it. Create/retire files as needed.
4. Report every `.claude/` file touched, or state why none needed updating.

### Commands
- `/update-claude-docs` — full `.claude/` audit
- `/fpt` — first-principles thinking mode

### Project context
Read `.claude/context.md` for project overview, stack, architecture, and conventions.
```

Fill in the dispatch table with actual files created for this repo. **CLAUDE.md must stay under 200 lines.**

## 2. Per-Task Behavior

Before starting any task:
1. Read `CLAUDE.md` and follow the 7-step workflow (see `agent-workflow.md` for step details).
2. Match the task against the dispatch table; load the pointed agents and skills.
3. Read ALL files in `.claude/rules/` as hard constraints.
4. Read relevant sections of `.claude/context.md` for project context.

Before finishing any task:
1. Validate work against all loaded rules. Fix violations.
2. Scan user instructions for implicit/explicit rules; persist any found to `.claude/rules/`.
3. Check whether `.claude/` needs updating (new concerns, changed structure, stale docs).
4. Update `.claude/` in the same task. State what changed or why nothing did.

## 3. Rule Learning

Scan every user message for implicit or explicit preferences, constraints, or conventions.

**Extraction procedure:**
1. Parse the full message for preferences, constraints, conventions, or architectural decisions.
2. Separate the TASK (what to do now) from the RULE (how things should always be).
3. Check `.claude/rules/` for an existing rule covering this concern.
4. If none exists, create a new kebab-case file. If one exists but is incomplete, update it.
5. Tell the user what you persisted and where.

**Examples:** "only access DB through models" -> `rules/database-access.md` | "never use default exports" -> `rules/module-exports.md` | "errors must return structured JSON" -> `rules/error-response-format.md`

**Rule file format:** `# Rule: [title]` with sections: Source, Scope, Rule, Rationale, Anti-patterns, Enforcement.

**Constraints:** Do not ask permission — just persist. Only persist project-specific decisions (not trivially obvious ones). If the user contradicts an existing rule, update it. User rules = code-detected rules in authority.

## 4. Self-Maintenance

Embedded in root `CLAUDE.md` and `.claude/commands/update-claude-docs.md` (manual fallback).

- New concern in repo -> create needed agent/rule/command/skill.
- Repo structure changed -> update `.claude/context.md` and affected rules.
- Files created/renamed/retired -> update dispatch table in `CLAUDE.md`.
- Unused `.claude/` file -> fix its triggers or retire it.
- Never leave `.claude/` stale. Prefer small continuous updates over large rewrites.

## 5. Core Principles

**First-principles thinking — no assumptions, ever.** Every statement in any `.claude/` file must be backed by evidence: a file you read, a command you ran, a pattern you observed, or something the user explicitly said. If you cannot verify it, do not include it. Never use "likely", "probably", "should be", "might be" in `.claude/` files. Decompose problems to fundamental truths.

**Agent files are living instructions.** They must be created, expanded, revised, or simplified as the repo evolves — never left as static templates.

**Staleness rule.** Do not finish a task while relevant `.claude/` guidance is stale. If no update is needed, explicitly explain why.

**User instructions are a source of truth.** When a user expresses a rule, persist it to `.claude/rules/` immediately. If it contradicts a prior rule, update the rule file.
