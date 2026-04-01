# Phase 8 — Self-Maintenance Rules

Embed these rules into TWO places to ensure they are never forgotten:

Place 1: Root `CLAUDE.md` (the dispatcher)
- This is what Claude Code loads every session.
- It contains the dispatch table that maps task types to specific agents, skills, and context sections.
- The agent reads this first, then loads only the files relevant to the current task.
- See the MANDATORY AUTO-UPDATE CONTRACT section above for exact content.

Place 2: `.claude/commands/update-claude-docs.md`
- The manual fallback when auto-update was missed.
- Full audit procedure with step-by-step instructions.
- Must produce a structured report of changes.

The rules themselves:
- Before starting any task, read `CLAUDE.md` dispatch table, load all rules, then read only the agents, skills, and context sections the dispatch table points to for this task type.
- Before finishing any task, validate your work against all loaded rules. Fix violations.
- Before finishing any task, scan the user's instructions for rules to extract and persist.
- Before finishing any task, check whether `.claude` is still accurate.
- If the user expressed a preference, convention, or constraint, persist it to `.claude/rules/`.
- If the repository gained a new concern, create the needed agent/rule/command/skill.
- If the repository structure materially changed, update `.claude/context.md` and the affected rules.
- If workflows changed, update the relevant commands/skills.
- If you create, rename, or retire any agent, skill, or rule file, update the dispatch table in `CLAUDE.md` to match.
- If a `.claude/` file is never being used (never matches any task), fix its trigger conditions or retire it.
- If nothing changed, explicitly say why no `.claude` update was needed.
- Never leave `.claude` stale after code changes or user-expressed rules unpersisted.
- Prefer small continuous updates over large delayed rewrites.
