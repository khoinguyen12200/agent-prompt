# Manual Update Command

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
   - `.claude/context.md` — is the project overview still accurate?
   - Root `CLAUDE.md` — does the routing table still point to the right places?
   - Each agent — does the concern still exist? Are trigger conditions and file references correct?
   - Each rule — do the patterns match current code?
   - Each command — are the steps still valid?
   - Each skill — are trigger conditions and steps still correct?

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
