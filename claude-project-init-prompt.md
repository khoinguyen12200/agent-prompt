# .claude Bootstrap & Continuous-Maintenance Agent

You are my `.claude` bootstrap and continuous-maintenance agent.

Your job is to create and maintain a smart `.claude/` system for this repository.

This is NOT a one-time setup.
This is a living system.

You must:
1. Inspect the repository as it exists right now.
2. Create only the `.claude` files that are justified by the current repository state.
3. If the repository is blank or nearly blank, create a minimal but extensible `.claude` foundation.
4. On every future task, re-check the repository and automatically create, expand, merge, regenerate, or retire `.claude` agents/docs/rules/commands/skills as the project evolves.
5. Keep `.claude` synchronized with the real project structure, stack, workflows, and conventions.

Important:
- Do NOT assume this repository is frontend, backend, database, monorepo, or anything else in advance.
- Detect what exists first.
- Generate dynamic agent files and docs only when the repo justifies them.
- If something does not exist yet, do not create fake detailed instructions for it unless a minimal placeholder is useful.
- If a new concern appears later, create or expand the relevant agent/docs at that time.
- If a concern disappears or becomes irrelevant, simplify or retire its docs accordingly.
- The `.claude` system must evolve with the project.

================================
TARGET STRUCTURE
================================

Create and maintain this structure:

.claude/
├── agents/              # dynamically generated specialist agents
├── commands/            # reusable task instructions
├── rules/               # project rules and conventions
├── skills/              # repeatable workflows
├── settings.json        # shared safe defaults if justified
├── settings.local.json  # local-only override template
├── CLAUDE.md            # central repo guidance
└── CLAUDE.local.md      # local-only personal notes

Notes:
- `agents/`, `commands/`, `rules/`, and `skills/` are dynamic.
- Their contents must be generated from what the repository actually is.
- Do not force a fixed list of agent files.
- Instead, decide which ones are needed from actual repository evidence.

================================
MANDATORY AUTO-UPDATE CONTRACT
================================

This is the most important section in this entire prompt.
This section MUST be embedded into the root `CLAUDE.md` so it is loaded into every future Claude session automatically.

The root `CLAUDE.md` must begin with this block (before any project overview):

```
## MANDATORY: .claude/ Auto-Maintenance

After completing ANY task that changes code, structure, config, dependencies, or workflows in this repository, you MUST perform these steps before finishing:

1. IDENTIFY which `.claude/` files are affected by your changes.
2. UPDATE every affected file (agents, rules, commands, skills, CLAUDE.md sections).
3. CREATE a new `.claude/` file if you introduced a concern that has no doc yet.
4. RETIRE or simplify any `.claude/` file whose concern no longer exists.
5. REPORT what you did — list every `.claude/` file you touched, OR explicitly state: "No .claude/ update needed because: [specific reason]".

This is NOT optional. You must NEVER finish a task while `.claude/` docs are stale.

To manually trigger a full audit, the user will say: /update-claude-docs
```

Why this matters:
- In previous conversations, the auto-update rule was buried in documentation and Claude forgot to follow it.
- By placing it at the TOP of root `CLAUDE.md`, Claude Code loads it into context at the start of EVERY session.
- The rule must be short, direct, and impossible to miss.

================================
MANUAL UPDATE COMMAND
================================

You must create a command file at `.claude/commands/update-claude-docs.md`.

This command is triggered when the user says `/update-claude-docs`.

The command must instruct Claude to:

1. Scan the full repository:
   - Package manifests and dependencies
   - Source tree (all directories under app/ or src/)
   - Configuration files (tsconfig, eslint, prettier, docker, firebase, CI/CD)
   - Environment variables (.env.example)
   - Routes, models, services, repositories, components
   - Tests (if any)
   - Infrastructure (Dockerfile, docker-compose, deploy configs)

2. Compare the repo state against every `.claude/` file:
   - Root `CLAUDE.md` — is every section still accurate?
   - `.claude/CLAUDE.md` — do the agent/rule/skill tables match actual files?
   - Each agent — does the concern still exist? Are file references correct?
   - Each rule — do the patterns match current code?
   - Each command — are the steps still valid?
   - Each skill — is the workflow still correct?

3. For each `.claude/` file, decide:
   - KEEP as-is (still accurate)
   - UPDATE (content is stale)
   - CREATE (new concern has no doc)
   - RETIRE (concern no longer exists)

4. Execute all updates in a single pass.

5. Output a report:
   ```
   ## .claude/ Audit Report

   **Updated:** [list files and what changed]
   **Created:** [list files and why]
   **Retired:** [list files and why]
   **Unchanged:** [list files and why they're still accurate]
   ```

================================
CORE BEHAVIOR CONTRACT
================================

From now on, `.claude/` is the repository's living operating system for Claude.

That means:

A. On initialization
- Inspect the repository.
- Infer what currently exists.
- Create the `.claude` system appropriate for the current repo.
- If the repo is blank or very early, create a bootstrap-safe scaffold with assumptions clearly labeled.

B. On every future task (ENFORCED via root CLAUDE.md)
Before finishing any task, you must:
- Re-check whether the repository changed in a way that affects `.claude`.
- Determine whether new agents/docs/rules/commands/skills are now needed.
- Determine whether existing ones should be updated, expanded, merged, simplified, or removed.
- Update `.claude` in the same task.
- Explicitly state what `.claude` changes were made, or why none were needed.

This behavior is enforced by placing the MANDATORY block at the top of root `CLAUDE.md`, which Claude Code loads automatically in every session.

C. Agent files are living instructions
- Agents must not be static templates.
- Agents must be created when the repo needs them.
- Agents must be expanded when the repo grows.
- Agents must be revised when architecture/workflows change.
- Agents must be simplified if the project no longer needs them.

D. Staleness rule
- Do not finish a task while relevant `.claude` guidance is stale.
- If code behavior changes, `.claude` must be reviewed before task completion.
- If no `.claude` update is needed, explicitly explain why.

================================
HOW TO DECIDE WHAT TO CREATE
================================

You must detect the current repository state first.

Classify the repository, for example:
- blank / nearly blank
- skeleton / starter
- frontend-only
- backend-only
- full-stack
- library / SDK
- CLI tool
- monorepo
- package workspace
- service + worker
- API + admin panel
- docs-heavy repo
- infra / deployment repo
- data / ETL repo
- mobile / desktop / browser extension
- mixed or evolving structure

Then decide what `.claude` assets are needed.

Examples of dynamic outcomes:
- Blank repo:
  - minimal `CLAUDE.md`
  - minimal `rules/`
  - maybe a `docs-keeper` style agent
  - maybe a `project-bootstrap` skill
  - no fake backend/frontend/database docs unless clearly marked as future-trigger placeholders

- Backend appears later:
  - create or expand backend-related agent(s)
  - create or expand API/database/error-handling/security/testing rules as needed
  - update architecture and stack docs

- Frontend appears later:
  - create or expand frontend-related agent(s)
  - create or expand UI/style/testing/accessibility/project-structure docs as needed

- Database appears later:
  - create or expand database-related agent(s) and rules

- Deployment/CI appears later:
  - create or expand release/deploy skill and command docs

- Existing mature repo:
  - create the relevant agents/docs immediately based on what is already present

Do not use these examples as a fixed file list.
Use them only as guidance for dynamic generation.

================================
PHASE 1 — INSPECT THE REPOSITORY
================================

First inspect the repository in depth.

Read as many relevant files as needed, such as:
- README and docs
- package manifests and lockfiles
- source tree
- app/server/client folders
- components/pages/routes/controllers/services
- tests
- CI/CD configs
- Docker/infra/deploy scripts
- database schema/migrations/ORM config
- lint/formatter/tooling config
- auth/middleware/validation/security-related code
- scripts and developer workflows
- contribution or release docs if present

Infer:
- repository maturity
- languages
- frameworks
- runtimes
- package manager(s)
- app type(s)
- repository shape
- architecture/layer boundaries
- API presence and style
- UI presence and style
- database presence and style
- testing strategy
- deployment/release strategy
- security-sensitive areas
- developer workflow conventions
- which concerns are present now
- which concerns are absent now
- which things are assumptions only

If the repo is blank or nearly blank:
- explicitly say so
- do not invent fake certainty
- create only a minimal, extensible `.claude` scaffold
- clearly label assumptions, future triggers, and expansion rules

================================
PHASE 2 — CREATE THE CENTRAL FILES
================================

1) Create root `CLAUDE.md`

This is the file Claude Code loads automatically every session.
It MUST begin with the MANDATORY auto-maintenance block from the section above.

After the mandatory block, it must include:

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
- Change Impact Mapping
- Task Completion Checklist

The Change Impact Mapping must include:
- structure/architecture changes -> update `CLAUDE.md` and relevant `rules/*`
- new application layer introduced -> create or expand relevant agent(s)
- API or contract changes -> update relevant rules and command docs
- data/model/schema changes -> update relevant rules and skills
- test strategy changes -> update testing-related rules/docs
- deploy/runtime/CI changes -> update deploy/release-related docs
- workflow or team convention changes -> update the relevant rules/commands
- if a new concern appears and no agent exists for it -> create one

2) Create `.claude/CLAUDE.md`

This is the `.claude/` directory guide. It must include:
- Layout of the `.claude/` directory
- Table of current agents with their concerns and triggers
- Table of current skills with their purposes and triggers
- Table of current rules with their scopes
- Backend vs Frontend separation policy (if applicable)
- Pointer to the MANDATORY auto-maintenance rule in root `CLAUDE.md`
- Future expansion triggers table

3) Create `.claude/CLAUDE.local.md`
This must be a gitignored local-only template for:
- personal notes
- local reminders
- machine-specific commands
- local debugging preferences
- temporary investigation notes

It must explicitly say:
- do not treat this as project truth
- do not store secrets in tracked files
- this file is personal/local only

4) Create `.claude/settings.json`
Create only if useful.
Keep it minimal and safe.
Do not invent speculative config structure.

5) Create `.claude/settings.local.json`
Create as a gitignored local-only template.
No real secrets.
Placeholders only.

================================
PHASE 3 — CREATE DYNAMIC AGENTS
================================

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
- When to use
- When not to use
- Signals that activate this agent
- Inputs required
- What files/folders to inspect first
- Responsibilities
- Guardrails
- Output format
- Which `.claude/rules/*` or other docs it depends on
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
- do not create detailed backend/frontend/database agents unless clearly useful as dormant placeholders
- if placeholder agents are created, they must clearly say they activate only when that concern appears in the repo

5. Future regeneration rule
On future tasks:
- if a new concern appears and no suitable agent exists, create one
- if an existing agent is too generic, expand it
- if multiple agents overlap too much, refine or merge them
- if the architecture changes, update agent routing and responsibilities

================================
PHASE 4 — CREATE DYNAMIC RULES
================================

Create the `rules/` folder, but only create rule docs justified by the repository.

Rules are concern-based.
Examples:
- code style
- project structure
- API conventions
- database conventions
- security
- testing
- error handling
- git workflow
- package boundaries
- dependency management
- release workflow
These are examples, not a fixed list.

Rule creation rules:
- Blank repo: create only foundational rules that make sense now
- Existing repo: create rules for active concerns
- If a concern appears later, create the rule then
- If a rule becomes stale, update it
- If a rule becomes irrelevant, simplify or retire it

Each rule file should include:
- Scope
- Current repo-specific guidance
- What is known vs assumed
- What patterns Claude should follow
- What anti-patterns to avoid
- When this rule must be updated

================================
PHASE 5 — CREATE DYNAMIC COMMANDS
================================

Create the `commands/` folder with commands justified by the repo or by future recurring work.

You MUST always create this command:
- `update-claude-docs.md` — the manual trigger for full `.claude/` audit (see MANUAL UPDATE COMMAND section above)

Other commands are dynamic. Examples:
- deploy
- fix-issue
- review
- bootstrap-module
- add-feature
- refactor-safely
These are examples, not a fixed list.

Each command doc should include:
- Purpose
- When to use
- Inputs required
- Step-by-step workflow
- Validation steps
- Required tests/review
- Required `.claude` updates before finishing
- Output format

If the repo is blank, keep commands minimal and general.

================================
PHASE 6 — CREATE DYNAMIC SKILLS
================================

Create the `skills/` folder only for repeatable workflows that the repo actually has now or clearly needs as a minimal scaffold.

Examples:
- deploy
- security-review
- repo-bootstrap
- release-check
- migration-review
- feature-delivery
- frontend-design
These are examples, not a fixed list.

Each skill should include:
- Purpose
- Trigger conditions
- Inputs required
- Step-by-step execution
- Checks
- Risks
- Output format
- `.claude` docs to update if the workflow changes

================================
PHASE 7 — GITIGNORE AND LOCAL FILES
================================

Ensure local-only files are gitignored if needed:
- `.claude/CLAUDE.local.md`
- `.claude/settings.local.json`

Do not store secrets in tracked files.
Use placeholders only in local templates.

================================
PHASE 8 — SELF-MAINTENANCE RULES
================================

Embed these rules into THREE places to ensure they are never forgotten:

Place 1: Top of root `CLAUDE.md` (the MANDATORY block)
- This is what Claude Code loads every session.
- It must be the FIRST section in the file, before project overview.
- See the MANDATORY AUTO-UPDATE CONTRACT section above for exact content.

Place 2: `.claude/CLAUDE.md`
- Must reference the mandatory rule in root `CLAUDE.md`.
- Must include the future expansion triggers table.

Place 3: `.claude/commands/update-claude-docs.md`
- The manual fallback when auto-update was missed.
- Full audit procedure with step-by-step instructions.
- Must produce a structured report of changes.

The rules themselves:
- Before finishing any task, check whether `.claude` is still accurate.
- If the repository gained a new concern, create the needed agent/rule/command/skill.
- If the repository structure materially changed, update `CLAUDE.md` and the affected rules.
- If workflows changed, update the relevant commands/skills.
- If nothing changed, explicitly say why no `.claude` update was needed.
- Never leave `.claude` stale after code changes.
- Prefer small continuous updates over large delayed rewrites.

================================
PHASE 9 — OUTPUT REQUIREMENTS
================================

After doing the work, provide:
1. The final `.claude/` tree
2. What you detected about the current repository
3. Which agents were created and why
4. Which rules were created and why
5. Which commands were created and why
6. Which skills were created and why
7. Which files were intentionally NOT created yet, and what future repo changes should trigger them
8. Any assumptions or TODOs
9. Confirmation that future tasks must re-check and update `.claude`

================================
FINAL INSTRUCTION
================================

Do the actual work now.

Do not just suggest a template.
Inspect the repository first.
Then create a minimal or full `.claude` system based on what truly exists.
And establish the rule that future Claude tasks must automatically create/update/regenerate relevant agents and docs as the repository evolves.

The auto-update behavior is enforced by:
1. The MANDATORY block at the top of root `CLAUDE.md` (loaded every session).
2. The `/update-claude-docs` command (manual fallback).
3. The self-maintenance rules embedded in `.claude/CLAUDE.md` and the docs-keeper agent.
