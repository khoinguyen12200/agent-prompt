# Phase 3 — Create Scoped Rules

Rules are scoped constraints that auto-load when Claude accesses matching files. This is a **native** Claude Code feature — more reliable than skills for enforcing constraints.

## ALL rules MUST have `paths:`

Rules without `paths:` only load at session start and drift in long conversations. Rules WITH `paths:` re-load every time Claude touches matching files. Always use `paths:`.

```yaml
---
paths:
  - src/api/**
  - src/routes/**
---

# API Conventions

- All endpoints return JSON with snake_case keys
- Error responses use { error: string, code: number } format
- ...
```

## What is a rule vs what goes in CLAUDE.md?

- **CLAUDE.md** — universal rules that apply to ALL tasks, ALL files (re-injected every turn)
- **rules/** — constraints that apply to SPECIFIC files/folders (auto-load on file access)

If a rule only matters when working on certain files, it belongs in `rules/`. If it matters everywhere, it belongs in CLAUDE.md.

## How to discover rules

Look for:
- **Naming patterns** — consistent conventions across file clusters
- **Linter/formatter configs** — encoded conventions
- **Architectural constraints** — how layers communicate, what's allowed/forbidden

Each consistent, non-obvious pattern is a candidate rule.

## Rule creation principles

- One rule per concern
- Only create rules backed by evidence
- Be specific and enforceable
- Scale with repo complexity

## What each rule file must include

- `paths:` frontmatter (required — no global rules here)
- Clear, enforceable constraint statements
- What compliance looks like
- What violation looks like
