# Phase 3 — Create Dynamic Agents

Create the `agents/` folder. Do NOT force a fixed agent list.

## Core principle: one agent per concern, not per domain

A "concern" is a specific area of responsibility with its own files, patterns, and expertise. If two things need different knowledge, they are different concerns.

**The test:** If you need "and" to describe an agent's job, it's too broad — split it.

**Wrong:** One agent per tech layer (frontend, backend, database) — vague, covers everything, guides nothing.
**Right:** One focused agent per actual area of responsibility found in the codebase.

## How to decompose a repository into concerns

1. **Map file tree to responsibilities.** Identify clusters of files serving the same purpose — each is a candidate concern.
2. **Check for distinct patterns.** Does the cluster follow conventions that differ from other clusters?
3. **Check for distinct expertise.** Would working here require knowledge irrelevant elsewhere?
4. **Check the boundary.** Can you clearly define which files this concern owns? If not, refine or merge.
5. **Name by what it governs.** Not a persona — a concern area.

## Good vs bad agents

Good: owns defined files/folders, has repo-specific patterns, concrete trigger conditions, provides guidance beyond generic prompts.

Bad: owns "everything related to [broad domain]", repeats generic advice, vague triggers like "when working on the frontend", replaceable by one sentence in CLAUDE.md.

## Scaling rules

Match agent count to repo complexity: minimal repo (0-1), small (2-4), medium (4-8), large (as many as needed). Never create agents for concerns that don't exist yet.

## What each agent file must include

YAML frontmatter:

```yaml
---
name: concern-name
description: One-line description of what this agent governs
tools:              # optional
  - Read
  - Edit
  - Bash
paths:              # optional
  - src/models/**
---
```

Body must include:
- **Purpose** — one sentence
- **Owns** — exact files/folders (glob patterns)
- **Trigger conditions** — specific, matchable (e.g., "task touches files in src/models/")
- **When not to use** — prevents overlap
- **Inspect first** — files to read before starting
- **Patterns in this repo** — actual conventions observed
- **Rules to enforce** — which `rules/*` apply
- **Skills to apply** — which `skills/*` are relevant
- **Guardrails** — what this agent must never do
- **Checklist before finishing** — verification steps
- **When to update this agent** — what changes require revision

## Future regeneration

On future tasks: create agents for new concerns, split overly broad agents, refine overlapping boundaries, retire agents for disappeared concerns, update agents when architecture changes.
