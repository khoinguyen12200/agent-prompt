# Manual Update Command

Create `.claude/commands/update-claude-docs.md`. Triggered via `/update-claude-docs`.

The command must instruct Claude to:

1. **Scan repo** — manifests, source tree, configs, routes, tests, infra
2. **Audit every `.claude/` file** — context.md, CLAUDE.md, rules, skills, agents, commands — still accurate?
3. **Decide per file** — KEEP, UPDATE, CREATE, or RETIRE
4. **Execute all updates** in one pass
5. **Report:**
   ```
   ## .claude/ Audit Report
   Updated / Created / Retired / Unchanged — with reasons
   ```
