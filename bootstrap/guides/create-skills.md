# Phase 6 — Create Dynamic Skills

Create the `skills/` folder only for repeatable workflows that the repo actually has now or clearly needs as a minimal scaffold.

**MANDATORY skill:**
- `task-execution.md` — defines the Think → Plan → Build → Review → Test → Ship → Reflect workflow. This skill must be referenced in `CLAUDE.md` for "Any task (always)".

Examples of other skills:
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
- Trigger conditions (specific, matchable patterns — e.g., "user asks to deploy", "task adds a new API endpoint", "migration files are created"). Must be concrete enough for auto-matching.
- Inputs required
- Step-by-step execution (Claude follows this automatically when the skill triggers — no user invocation needed)
- Mapping to the 7-step workflow (which steps this skill covers or modifies)
- Which `.claude/rules/*` must be checked during this workflow
- Checks
- Risks
- Output format
- `.claude` docs to update if the workflow changes
