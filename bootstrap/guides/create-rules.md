# Phase 4 — Create Dynamic Rules

Create the `rules/` folder. Rules are hard constraints Claude must never violate.

## What is a rule?

A specific, enforceable decision about how things must be done — backed by evidence.

**Good:** "All API responses must use snake_case keys" (specific, verifiable)
**Bad:** "Write clean code" (vague, generic)

## Rule scoping

- **Global** (no `paths:` frontmatter) — loaded for every task.
- **Scoped** (with `paths:`) — loaded only when task touches matching files.

```yaml
---
paths:
  - src/api/**
  - src/routes/**
---
```

Use scoped rules for subset-specific conventions; global rules for universal constraints.

## Where rules come from

1. **Repository evidence** — consistent patterns observed in code.
2. **User statements** — preferences, constraints, corrections expressed during any task.

## How to discover rules

Look for:
- **Naming/structural patterns** — consistent file, function, variable naming; where each type of logic lives
- **Convention enforcement** — linter configs, formatter configs, CI checks
- **Architectural decisions and constraints** — how layers communicate; what must always/never happen

Each consistent, non-obvious pattern is a candidate rule. If breaking it would cause problems, it's a rule.

## Rule creation principles

- One rule per concern
- Only create rules backed by evidence
- Be specific and enforceable — Claude must be able to check compliance
- Scale with the repo
- ALWAYS create `rules/workflow-step-enforcement.md`

## What each rule file must include

- **Source** — detected from code OR expressed by user (with evidence)
- **Scope** — which files, folders, or task types this applies to
- **Rule** — clear, enforceable constraint statement
- **Evidence** — what backs this rule
- **Patterns to follow** — what compliance looks like
- **Anti-patterns** — what violation looks like
- **Enforcement checkpoint** — what to verify before finishing
- **When to update** — what changes require revision
