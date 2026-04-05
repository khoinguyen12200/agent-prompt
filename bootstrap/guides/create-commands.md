# Phase 5 — Create Dynamic Commands

Create the `commands/` folder. Commands are user-invoked workflows triggered via `/command-name` (native Claude Code feature).

## What is a command?

An on-demand tool the user explicitly triggers. Unlike skills (auto-triggered), commands run only when the user types `/command-name`.

**Good:** Recurring workflow with specific steps and checks.
**Bad:** One-time action or something too simple to document.

## Mandatory commands

Always create:
- **`update-claude-docs.md`** — full `.claude/` audit
- **`fpt.md`** — first-principles thinking mode

## When to create additional commands

Create when: the repo has a **recurring, multi-step workflow** with repo-specific details easy to forget.

Do NOT create when: the workflow should auto-trigger (that's a skill), is trivial, or the concern doesn't exist yet.

## Command creation principles

- One workflow per command
- Only for workflows that exist
- Include repo-specific steps
- Simple repos: only the two mandatory commands

## What each command file must include

- **Purpose** and **when to use**
- **Inputs required**
- **Step-by-step workflow**
- **Validation steps**
- **Required `.claude` updates**
- **Output format**
