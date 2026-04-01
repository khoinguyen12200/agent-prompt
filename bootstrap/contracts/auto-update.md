# Mandatory Auto-Update Contract

This is the most important section in this entire prompt.
This section MUST be embedded into the root `CLAUDE.md` so it is loaded into every future Claude session automatically.

The root `CLAUDE.md` must be structured as a dispatcher. Here is the template — the bootstrap agent must fill in the actual file paths based on what it creates:

```
## .claude/ System — Central Guidance

You are operating inside a managed `.claude/` system. This file tells you what to load based on the task.

FIRST PRINCIPLES: Write nothing based on assumptions. Every statement must be backed by evidence — code you read, patterns you observed, or explicit user statements.

### How to use this file

1. Read the user's task.
2. Match it against the dispatch table below.
3. Read ONLY the files listed for that task type.
4. Begin work with the right constraints, role, and workflow loaded.

### Dispatch table

[This table is dynamically generated based on what agents, rules, and skills exist in the repo. The bootstrap agent must build this from what it actually creates. Example format:]

| Task type | Read these rules | Use this agent | Follow this skill | Context sections |
|-----------|-----------------|----------------|-------------------|-----------------|
| Backend / API work | `rules/api-conventions.md`, `rules/error-handling.md` | `agents/backend-architect.md` | `skills/feature-delivery.md` | Architecture, API in `context.md` |
| Frontend / UI work | `rules/component-style.md`, `rules/accessibility.md` | `agents/frontend-wizard.md` | `skills/frontend-design.md` | UI, Components in `context.md` |
| Database / migrations | `rules/database-conventions.md` | `agents/database-guardian.md` | `skills/migration-review.md` | Database in `context.md` |
| Testing | `rules/testing.md` | `agents/test-engineer.md` | — | Testing in `context.md` |
| Deployment / release | `rules/release-workflow.md` | `agents/release-manager.md` | `skills/deploy.md` | Deployment in `context.md` |
| Security-sensitive | `rules/security.md` | `agents/security-auditor.md` | `skills/security-review.md` | Security in `context.md` |
| Any task (always) | ALL files in `rules/` | — | `skills/task-execution.md` | — |

**Important: Always read ALL rules.** The dispatch table tells you which agents and skills to activate, but rules are always loaded in full — they are hard constraints.

**Universal Workflow:** For every task, follow the 7-step workflow defined in `skills/task-execution.md`: Think → Plan → Build → Review → Test → Ship → Reflect. This skill is always loaded.

### After any task — validate and learn:

1. **Rule compliance**: re-read all rules in `.claude/rules/` and check your work against each one. Fix violations before finishing.
2. **Rule learning**: if the user expressed any preference, convention, or constraint in their instructions, extract it and save as a new file in `.claude/rules/`.
3. **Update `.claude/`**: if your changes affect any `.claude/` file, update it. Create new files for new concerns. Retire files for dead concerns.
4. **Report**: list every `.claude/` file you touched, or state why none needed updating.

### Commands (user-invoked)
- `/update-claude-docs` — full `.claude/` audit
- `/fpt` — first-principles thinking mode for important tasks

### Project context
Read `.claude/context.md` for project overview, stack, architecture, and conventions.
```

The bootstrap agent MUST fill in the dispatch table with the actual files it creates. The example rows above are only a template — use what actually exists in the repo. If the repo only has backend, only include backend rows. If it has nothing yet, create a minimal table and expand it as the project grows.

Why this matters:
- Without the dispatch table, Claude either reads everything (wasteful) or guesses what to read (wrong).
- The dispatch table tells Claude exactly which files to load for each task type — saving tokens and ensuring nothing is missed.
- Rules are always loaded in full because they are hard constraints that apply universally.
- Agents and skills are loaded selectively — only the ones relevant to the current task.
- By placing this at the TOP of root `CLAUDE.md`, Claude Code loads it into context at the start of EVERY session.
