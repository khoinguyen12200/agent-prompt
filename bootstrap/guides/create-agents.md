# Phase 5 — Create Subagents

Subagents are specialized AI assistants with isolated 200K-token context windows. They run in isolation — their exploration noise doesn't pollute the main conversation. This is a **native** Claude Code feature.

## When to create a subagent

Create when the repo has tasks that benefit from:
- **Isolation** — complex analysis that would consume too much main context
- **Tool restrictions** — read-only review that shouldn't be able to edit
- **Specialization** — recurring tasks with specific expertise needs

Do NOT create subagents for simple concerns — use skills instead. Subagents are for heavier, isolated work.

## Agent file format

`.claude/agents/agent-name.md` with YAML frontmatter:

```yaml
---
name: code-reviewer
description: "Reviews code changes for bugs, security issues, and convention violations. Delegate when PR review or code audit is needed."
model: claude-sonnet-4-6
allowed-tools:
  - Read
  - Grep
  - Glob
---

# Code Reviewer

Reply as short as possible. Only include essential findings. No preamble.

Review all changed files for:
- Logic errors and edge cases
- Security vulnerabilities
- Convention violations (check rules/ for project conventions)
- Missing test coverage

Output a structured review with severity levels.
```

**Agent body must be concise.** Every line costs tokens on every delegation. Include only what the agent specifically needs — no workflow restatement, no generic advice. Add `Reply as short as possible. Only include essential findings. No preamble.` to every agent body.

## Key frontmatter fields

- **`name`** — identifier
- **`description`** — when Claude should delegate to this agent (same importance as skill descriptions)
- **`model`** — override model (e.g., use sonnet for speed, opus for quality)
- **`allowed-tools`** / **`deny-tools`** — restrict what the agent can do
- **`isolation: worktree`** — run in isolated git worktree
- **`skills: [skill-name]`** — preload specific skills into the agent

## Scaling

Most repos need 0 subagents. Only create them when isolation or tool restriction adds real value. Common useful subagents:
- Read-only code reviewer (can't edit, only analyze)
- Security auditor (scoped to auth/security files)
- Documentation writer (isolated context for large doc tasks)

## Good description pattern

Same as skills — be pushy and specific:
```
"Delegate to this agent when reviewing PRs, auditing code quality, or checking for security issues. Read-only — cannot modify files."
```
