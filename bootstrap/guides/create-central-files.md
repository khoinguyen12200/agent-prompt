# Phase 2 — Create the Central Files

1) Create root `CLAUDE.md` — the central dispatcher

**CRITICAL: Must be under 200 lines.** Longer files reduce instruction adherence.

**Required structure (in this order):**
1. **7-step workflow block (INLINE, at top)** — Full steps with descriptions, before the dispatch table. Do NOT replace with a file reference — the skill file provides extra detail, but enforcement lives here.
2. **Dispatch table** — Maps task types to agents, rules, skills, and context sections.
3. **Post-task validation** — Rule compliance, rule learning, `.claude/` updates.

Write as direct instructions (imperative sentences). Example:
- DO: "If the task involves [concern X], read `agents/[concern-x].md`."
- DO NOT: "This section describes..." (that's documentation, not instruction)

After the dispatch table, include a Change Impact Mapping:
- structure changes -> update `context.md` and relevant `rules/*`
- new layer introduced -> create/expand relevant agent(s)
- API/contract changes -> update relevant rules and command docs
- user expresses preference -> extract and persist to `rules/*`
- any `.claude/` file created/renamed/retired -> update dispatch table

Do NOT put project overview, stack, or conventions in `CLAUDE.md` — that belongs in `context.md`.

2) Create `.claude/context.md` — the project overview

The project knowledge base. Must include (all backed by evidence):
- Project overview, repo state, detected stack
- Architecture summary, important directories
- Development/testing/deployment workflows
- Working conventions, current feature status

3) Create `.claude/settings.json`
Create only if useful. Keep minimal and safe. No speculative config.
