# Phase 3 — Create Dynamic Agents

Create the `agents/` folder, but do NOT force a fixed agent list.

Instead:
- detect the current repository concerns
- generate agent files only for concerns that are justified now
- if the repo is blank, create only the minimum useful agent set
- if the repo is mature, create the agent set needed immediately

Agent creation rules:

1. Every agent must be concern-based, not trend-based.
Examples of concerns:
- project documentation maintenance
- backend/service architecture
- frontend/UI architecture
- database/data integrity
- security review
- testing/quality
- release/deployment
- library/API design
- monorepo/package boundaries
- data pipeline/workflow ownership
These are examples, not a required list.

2. Each agent file must include:
- Purpose
- Trigger conditions (specific, matchable patterns — e.g., "task touches files in src/api/", "user mentions database", "task involves authentication"). These must be concrete enough for auto-matching, not vague descriptions.
- When not to use
- Inputs required
- What files/folders to inspect first
- Responsibilities
- Which `.claude/rules/*` it must enforce (list specific rule files)
- Which `.claude/skills/*` it should auto-apply when relevant
- Guardrails
- Output format
- Which `.claude` docs it must update when behavior changes
- How this agent should evolve if the repository grows

3. Agent naming must match the repo concern.
Use clear names like:
- `docs-keeper.md`
- `backend-architect.md`
- `frontend-wizard.md`
- `database-guardian.md`
- `security-auditor.md`
- `test-engineer.md`
- `release-manager.md`
- `monorepo-governor.md`
- `sdk-maintainer.md`
- `cli-architect.md`
These are only naming examples. Choose what fits the repo.

4. Minimum blank-repo rule
If the repo is blank or nearly blank:
- create only the smallest sensible agent set
- usually at least one maintenance/governance-style agent that ensures future `.claude` expansion
- do not create agents for concerns that do not yet exist — no placeholders, no speculation
- agents are created when evidence justifies them, not before

5. Future regeneration rule
On future tasks:
- if a new concern appears and no suitable agent exists, create one
- if an existing agent is too generic, expand it
- if multiple agents overlap too much, refine or merge them
- if the architecture changes, update agent routing and responsibilities
