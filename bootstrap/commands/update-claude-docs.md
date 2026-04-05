# Manual Update Command

Create a command file at `.claude/commands/update-claude-docs.md`.

Triggered via `/update-claude-docs`.

The command must instruct Claude to:

1. **Scan the full repository:** package manifests, source tree, configs (tsconfig, eslint, docker, CI/CD), env examples, routes/models/services/components, tests, infrastructure.

2. **Compare repo state against every `.claude/` file:**
   - `context.md` — still accurate?
   - `CLAUDE.md` — routing table correct?
   - Each agent — concern still exists? Triggers and file refs correct?
   - Each rule — patterns match current code?
   - Each command/skill — steps still valid?

3. **Decide per file:** KEEP, UPDATE, CREATE (new concern), or RETIRE (gone concern).

4. **Execute all updates** in a single pass.

5. **Output report:**
   ```
   ## .claude/ Audit Report

   **Updated:** [files and what changed]
   **Created:** [files and why]
   **Retired:** [files and why]
   **Unchanged:** [files and why still accurate]
   ```
