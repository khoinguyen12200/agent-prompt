# Phase 3 — Create Skills

Skills are natively auto-triggered by Claude Code. When a task matches a skill's description or file paths, Claude activates it automatically. This is the primary mechanism for concern-specific guidance.

## How auto-triggering works

Claude reads ONLY the `name` and `description` from each SKILL.md frontmatter. If the user's request matches, Claude loads the full skill body. Two mechanisms control triggering:

1. **`description`** — Claude matches this against the user's request. This is the #1 trigger.
2. **`paths`** — Glob patterns. If the task touches files matching these patterns, the skill activates regardless of description matching.

**If triggering fails, the description is wrong.** Fix the description first.

## Writing descriptions that actually trigger

The description is under 250 characters. It MUST be specific and pushy. Claude skips vague descriptions.

**Bad descriptions (will NOT trigger):**
- `"Handles frontend concerns"` — too vague
- `"Use when working on the API"` — too passive
- `"Database patterns and conventions"` — describes content, not trigger

**Good descriptions (WILL trigger):**
- `"MUST be used for any change to files in src/components/ or src/pages/. Covers React component patterns, Tailwind conventions, and accessibility rules for this project."`
- `"MUST be used when creating, modifying, or debugging API endpoints in src/api/. Covers route structure, error handling, and response format rules."`
- `"MUST be used for any database schema change, migration, or query in src/models/. Covers ORM patterns, naming conventions, and migration safety rules."`

**Pattern:** Start with `"MUST be used for/when [specific trigger]."` Then list what knowledge it provides.

## Using `paths:` for reliable triggering

Always set `paths:` to the files/folders the skill owns. This ensures activation even if the description doesn't match:

```yaml
---
name: api-design
description: "MUST be used when creating or modifying API endpoints in src/api/. Covers route patterns, error handling, validation, and response format conventions."
paths:
  - src/api/**
  - src/routes/**
---
```

With `paths:` set, any task touching `src/api/` activates this skill — no description matching needed.

## Skill directory format

```
skills/skill-name/
├── SKILL.md          # required — YAML frontmatter + instructions
├── scripts/          # optional
├── references/       # optional
└── assets/           # optional
```

## No task-execution skill

The 8-step workflow lives in **CLAUDE.md directly** (auto-loaded every session). Do NOT create a separate task-execution skill — it duplicates CLAUDE.md and Claude never invokes it anyway.

## How to decompose a repo into skills

1. **Map file tree to responsibilities.** Identify clusters of files serving the same purpose.
2. **Check for distinct patterns.** Different conventions from other clusters?
3. **Check for distinct expertise.** Requires knowledge irrelevant elsewhere?
4. **Set the `paths:` boundary.** Each skill must own specific files via glob patterns.

## Good vs bad

**Good:** Has `paths:` set, pushy description with "MUST be used", repo-specific patterns, embedded rules.
**Bad:** No `paths:`, vague description, generic advice, no concrete trigger.

## Scaling

Minimal repo: 0 skills (workflow is in CLAUDE.md). Small: 1-3. Medium: 3-6. Large: as many as needed. Never create skills for nonexistent concerns.

## Embedding rules in skills

**Universal rules** → CLAUDE.md directly (auto-loaded every task).
**Concern-specific rules** → inside the relevant skill's SKILL.md (loaded when skill triggers).

## What each SKILL.md body must include

- **Patterns in this repo** — actual conventions observed (not generic advice)
- **Rules for this concern** — constraints specific to this area
- **Checklist before finishing** — what to verify for work in this area

For **workflow skills** (e.g., deployment, migration):
- **Step-by-step execution** — repo-specific sequence
- **Checks and risks** — what could go wrong
