# Phase 4 — Create Skills

Skills provide detailed concern-specific knowledge. They are natively auto-triggered by Claude Code based on description and `paths:` matching. Use skills for knowledge and patterns — use `rules/` for constraints.

## How auto-triggering works

Two mechanisms control activation:
1. **`description`** — Claude matches against the user's request (~44% reliable alone)
2. **`paths`** — Glob patterns. Auto-activates when task touches matching files (more reliable)

**Always set both.** Description for intent matching, `paths:` for file-based matching.

## Writing descriptions that trigger

Under 250 characters. Be pushy and specific.

**Bad:** `"Handles frontend concerns"` — too vague, will be skipped
**Good:** `"MUST be used for any change to files in src/components/. Covers React component patterns, Tailwind conventions, and accessibility rules."`

**Pattern:** Start with `"MUST be used for/when [specific trigger]."` Then list what knowledge it provides.

## Skill directory format

```
skills/skill-name/
├── SKILL.md          # required — YAML frontmatter + knowledge
├── scripts/          # optional
├── references/       # optional
└── assets/           # optional
```

### SKILL.md frontmatter

```yaml
---
name: api-design
description: "MUST be used when creating or modifying API endpoints in src/api/. Covers route patterns, error handling, and response format conventions."
paths:
  - src/api/**
  - src/routes/**
---
```

## Skills vs Rules vs CLAUDE.md

| Content type | Where | Why |
|---|---|---|
| Universal rules (all files) | CLAUDE.md | Re-injected every turn |
| Scoped constraints (specific files) | `rules/` with `paths:` | Native, reliable on file access |
| Detailed patterns/knowledge | `skills/` with `paths:` | Auto-triggered, detailed guidance |

Skills provide **knowledge** (patterns, conventions, how-to). Rules enforce **constraints** (must/must-not). Don't put constraints in skills — put them in rules where enforcement is more reliable.

## How to decompose a repo into skills

1. **Map file tree to responsibilities.** Identify clusters of files serving the same purpose.
2. **Check for distinct patterns.** Different conventions from other clusters?
3. **Check for distinct expertise.** Requires knowledge irrelevant elsewhere?
4. **Set the `paths:` boundary.** Each skill must own specific files.

## Scaling

Minimal repo: 0 skills. Small: 1-3. Medium: 3-6. Large: as many as needed. Never create skills for nonexistent concerns.

## What each SKILL.md body must include

- **Patterns in this repo** — actual conventions observed (not generic advice)
- **How to work in this area** — repo-specific guidance
- **Checklist before finishing** — what to verify

For **workflow skills** (deployment, migration, etc.):
- **Step-by-step execution** — repo-specific sequence
- **Checks and risks** — what could go wrong
