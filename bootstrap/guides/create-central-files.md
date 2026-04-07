# Phase 2 — Create the Central Files

## 1) `CLAUDE.md` — the only auto-loaded file

**CRITICAL: Must be under 200 lines.** Re-injected as system-reminder every turn — every extra line costs tokens on every message.

**Required structure:**
1. **8-step workflow block (INLINE, at top)** — Use the template from `contracts/core-contracts.md`.
2. **Project Rules** — Universal rules. One line per rule. Scoped rules go in `rules/`.
3. **`@.claude/context.md`** — imports context directly (native @import, not an instruction to read it).
4. **Commands** — List available commands.

**Write directives only. No prose, no explanations, no examples.** Bullet points over sentences. Each workflow step must fit on one line. If a rule needs explanation, it belongs in `rules/` or `skills/`, not here.

## 2) `settings.json` — hooks and permissions

**MUST generate this file.** Use the template from `contracts/core-contracts.md` section 2.

Three hooks are required:
- `SessionStart` — workflow reminder at session start
- `Stop` — checks for ## Reflect after every response
- `PostCompact` — re-injects workflow after context compaction

Add project-specific permissions if justified (e.g., deny destructive commands).

## 3) `context.md` — project knowledge base

Imported by CLAUDE.md via `@.claude/context.md`. Must include (all backed by evidence):
- Project overview, repo state, detected stack
- Architecture summary, important directories
- Development/testing/deployment workflows
- Working conventions, current feature status

## Change impact

When the repo changes:
- Universal rules changed → update CLAUDE.md
- Scoped constraints changed → update `rules/`
- Concern knowledge changed → update relevant skill
- Project overview changed → update `context.md`
- Skills/rules created or retired → no dispatch table (auto-triggered by paths/description)
