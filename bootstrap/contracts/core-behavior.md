# Core Behavior Contract

From now on, `.claude/` is the repository's living operating system for Claude.

That means:

A. On initialization
- Inspect the repository thoroughly. Read files. Verify facts.
- Determine what currently exists based on evidence only.
- Create the `.claude` system appropriate for the current repo — grounded in what you verified.
- If the repo is blank or very early, create only a minimal scaffold for what you can confirm. Do not speculate about what the project might become.

B. On every future task (ENFORCED via root CLAUDE.md)
Before starting any task:
1. Read the user's task and match it against the dispatch table in `CLAUDE.md`.
2. Read ALL files in `.claude/rules/` — these are always loaded as hard constraints.
3. Read the specific agent(s) the dispatch table points to for this task type. Adopt their role.
4. Read the specific skill(s) the dispatch table points to for this task type. Follow their workflow.
5. Read `skills/task-execution.md` and follow the 7-step workflow: Think → Plan → Build → Review → Test → Ship → Reflect.
6. Read the relevant sections of `.claude/context.md` for project context.

Before finishing any task, you must:
- Validate your work against ALL loaded rules. Fix any violations.
- Scan the user's instructions for implicit or explicit rules, preferences, conventions, or constraints. Extract and persist any found to `.claude/rules/`.
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

E. User instructions are a source of truth
- When a user expresses a rule, preference, or constraint, it has the same weight as a pattern detected in code.
- User-expressed rules must be persisted to `.claude/rules/` immediately, not just followed for one task.
- If a user contradicts a previously persisted rule, update the rule file — do not silently ignore either the old or new instruction.
- Rule extraction is automatic and silent. Do not ask permission to create rule files.

F. First-principles thinking — no assumptions, ever
- Every statement you write in any `.claude/` file must be backed by evidence: a file you read, a command you ran, a pattern you observed, or something the user explicitly said.
- If you are not sure about something, verify it first. If you cannot verify it, do not include it.
- Never use phrases like "likely", "probably", "should be", "might be", "presumably", or "it seems" in `.claude/` files. Either you know it or you don't.
- When building rules, agents, skills, or structure: decompose the problem to its fundamental truths. What do you actually know? What does the code actually do? What did the user actually say?
- This applies to ALL `.claude/` output: rules, agents, skills, commands, context.md, CLAUDE.md — everything.
