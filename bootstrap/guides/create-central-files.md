# Phase 2 — Create the Central Files

## 1) `CLAUDE.md` — the only auto-loaded file

**CRITICAL: Must be under 200 lines.** Longer files reduce instruction adherence.

**Required structure (in this order):**
1. **7-step workflow block (INLINE, at top)** — Use the template from `contracts/core-contracts.md`. Do NOT replace with a file reference.
2. **Project Rules** — Universal rules discovered from repo evidence. One line per rule. Concern-specific rules go in skill files, not here.
3. **Project Context pointer** — Reference to `context.md`.
4. **Commands** — List available commands.

Write as direct instructions (imperative sentences). No documentation, no explanations.

**Change impact:** When the repo changes, update CLAUDE.md (rules), context.md (knowledge), or relevant skills (concern-specific guidance). If skills are created/renamed/retired, no dispatch table to update — skills auto-trigger by their description.

## 2) `context.md` — the project knowledge base

Referenced from CLAUDE.md. Must include (all backed by evidence):
- Project overview, repo state, detected stack
- Architecture summary, important directories
- Development/testing/deployment workflows
- Working conventions, current feature status

## 3) `settings.json`

Create only if useful. Keep minimal and safe.
