# Phase 6 — Create Dynamic Skills

Create the `skills/` folder only for repeatable workflows the repo actually needs.

## What is a skill?

A step-by-step workflow Claude follows automatically when triggered by the dispatch table. Unlike commands (user-invoked), skills activate based on task matching.

**Good skill:** Multi-step workflow with repo-specific checks and patterns.
**Bad skill:** Generic process restating common sense.

## Skill directory format

```
skills/skill-name/
├── SKILL.md          # required — with YAML frontmatter (name, description)
├── scripts/          # optional
├── references/       # optional
└── assets/           # optional
```

## When to create a skill

Create when: the workflow is a **specific, repeatable sequence** with **repo-specific details** where wrong order or missed steps cause problems.

Do NOT create when: the workflow is obvious, generic, or the concern doesn't exist yet.

## Mandatory skill

**`skills/task-execution/SKILL.md`** — the 7-step workflow. Always referenced in `CLAUDE.md`.

## Skill creation principles

- One workflow per skill
- Only for workflows that exist — no speculation
- Include repo-specific details Claude couldn't derive alone
- Scale with repo: blank = only `task-execution`; mature = one per complex workflow
- Bundle helper scripts, references, templates alongside SKILL.md

## What each SKILL.md must include

Frontmatter: `name`, `description`

Body:
- **Purpose** — what workflow this governs
- **Trigger conditions** — specific, matchable
- **Inputs required** — what Claude needs before starting
- **Step-by-step execution** — repo-specific sequence
- **Mapping to 7-step workflow** — which steps this covers/modifies
- **Rules to check** — which `rules/*` to validate
- **Checks and risks** — what to verify, what could go wrong
- **Output format** — expected result
- **When to update** — what changes require revision
