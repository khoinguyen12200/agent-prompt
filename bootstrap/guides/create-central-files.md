# Phase 2 — Create the Central Files

1) Create root `CLAUDE.md` — the central guidance / dispatcher

This is the file Claude Code loads automatically every session.
It must contain the dispatch table from the MANDATORY AUTO-UPDATE CONTRACT section above.
The dispatch table must map task types to specific agent files, skill files, and context sections — so the agent knows exactly what to load without reading everything.

Write `CLAUDE.md` as direct instructions to the agent — like you are giving orders to a worker. Use imperative sentences. Example:
- DO: "If the task involves backend work, read `agents/backend-architect.md` and `rules/api-conventions.md`."
- DO: "Always read all files in `rules/` before starting any task."
- DO NOT: "This section describes the project's backend architecture..." (that's documentation, put it in `context.md`)
- DO NOT: "The rules folder contains project conventions..." (that's explaining, not instructing)

After the dispatch table, include a Change Impact Mapping:
- structure/architecture changes -> update `.claude/context.md` and relevant `rules/*`
- new application layer introduced -> create or expand relevant agent(s)
- API or contract changes -> update relevant rules and command docs
- data/model/schema changes -> update relevant rules and skills
- test strategy changes -> update testing-related rules/docs
- deploy/runtime/CI changes -> update deploy/release-related docs
- workflow or team convention changes -> update the relevant rules/commands
- user expresses a preference, convention, or constraint -> extract and persist to `rules/*`
- if a new concern appears and no agent exists for it -> create one
- if any agent, rule, or skill is created, renamed, or retired -> update the dispatch table in `CLAUDE.md`

Do NOT put project overview, stack, architecture, or conventions in `CLAUDE.md`. That belongs in `context.md`.

2) Create `.claude/context.md` — the project overview

This is the project knowledge base. The agent reads this in step 4 of pre-task loading.
It must include:

- Project Overview
- Current Repository State
- Detected Stack
- Architecture Summary (backend and frontend separately if both exist)
- Important Directories
- Development Workflow
- Testing Workflow
- Deployment/Runtime Overview if applicable
- Working Conventions (backend, frontend, general — separated)
- Current Feature Status

Every section must be backed by evidence (files you read, patterns you observed). No speculation.

3) Create `.claude/settings.json`
Create only if useful.
Keep it minimal and safe.
Do not invent speculative config structure.
