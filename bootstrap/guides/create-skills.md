# Phase 3 — Create Skills

Skills are the primary mechanism for concern-specific guidance. They replace the old "agents" and "skills" as separate concepts — everything is now a skill, because skills are **natively auto-triggered** by Claude Code based on their SKILL.md description.

## Two types of skills

### 1. Concern skills (replaces "agents")
Each area of responsibility in the repo gets its own skill. When the task matches the skill's description, Claude Code activates it automatically.

**The test:** If you need "and" to describe a skill's scope, it's too broad — split it.

### 2. Workflow skills
Repeatable multi-step workflows specific to this repo (e.g., deployment, migration review).

## Mandatory skill

**`skills/task-execution/SKILL.md`** — The 7-step workflow. Always active.

## Skill directory format

```
skills/skill-name/
├── SKILL.md          # required — YAML frontmatter + instructions
├── scripts/          # optional — helper scripts
├── references/       # optional — reference docs
└── assets/           # optional — templates, configs
```

### SKILL.md frontmatter

```yaml
---
name: skill-name
description: What this skill does and WHEN to use it. Front-load the trigger — Claude Code uses this to decide activation.
---
```

The `description` is critical — it determines when Claude auto-activates the skill. Be specific.

## How to decompose a repo into concern skills

1. **Map file tree to responsibilities.** Identify clusters of files serving the same purpose.
2. **Check for distinct patterns.** Different conventions from other clusters?
3. **Check for distinct expertise.** Requires knowledge irrelevant elsewhere?
4. **Check the boundary.** Can you define which files this concern owns?

## Good vs bad

**Good:** Owns defined files, repo-specific patterns, description triggers correctly, includes concrete rules.
**Bad:** Covers "everything related to [broad domain]", generic advice, vague description.

## Scaling

Minimal repo: 1 (task-execution only). Small: 2-4. Medium: 4-8. Large: as many as needed. Never create skills for nonexistent concerns.

## Embedding rules in skills

**Universal rules** (apply to ALL tasks) → put in **CLAUDE.md directly** (auto-loaded).
**Concern-specific rules** → put **inside the relevant skill's SKILL.md**. When the skill activates, its rules come with it. This is more reliable than separate rule files.

## What each SKILL.md body must include

For **concern skills**:
- **Purpose** — what concern this governs
- **Owns** — files/folders (glob patterns)
- **Patterns in this repo** — actual conventions observed
- **Rules for this concern** — constraints embedded here, not in separate files
- **Checklist before finishing** — verification steps

For **workflow skills**:
- **Purpose** — what workflow this governs
- **Step-by-step execution** — repo-specific sequence
- **Rules to check** — constraints during this workflow
- **Checks and risks** — what to verify, what could go wrong
