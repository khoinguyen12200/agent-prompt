# Core Contracts

## 1. CLAUDE.md Template

Generate root `CLAUDE.md` using this template. Fill in project rules for this repo.

```
## .claude/ System

### WORKFLOW — Think → Load → Plan → Build → Review → Test → Ship → Reflect

1. **Think** — understand the request
2. **Load** — invoke matching skills, list them
3. **Plan** — subtasks, simplest approach
4. **Build** — execute
5. **Review** — bugs, edge cases, security
6. **Test** — run, fix, add tests
7. **Ship** — what changed and why
8. **Reflect** — update `.claude/` if needed. State what changed or why not.

Show each step label. Reply short — lead with answer, no preamble. INCOMPLETE without ## Reflect. Steps 1-4 never skippable. Evidence only — no assumptions.

### Project Rules

[Insert universal rules discovered from repo evidence here. One line per rule. Concern-specific rules go in rules/ or skills/.]

### Project Context

@.claude/context.md

### Commands
- `/update-claude-docs` — full `.claude/` audit
- `/fpt` — first-principles thinking mode
```

**CLAUDE.md must stay under 200 lines.** Use `@import` syntax to pull in context.md instead of telling Claude to read it.

## 2. settings.json Template

Generate `.claude/settings.json` with these hooks:

```json
{
  "hooks": {
    "SessionStart": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "echo '[Hook] 8-step workflow active. Load skills before coding. Reply short — lead with the answer, no preamble.'"
          }
        ]
      }
    ],
    "Stop": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "echo '[Hook] Missing ## Reflect? Add it. Reply short — lead with the answer, no preamble.'"
          }
        ]
      }
    ],
    "PostCompact": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "echo '[Hook] Context compacted. Re-apply 8-step workflow. Load skills. Show ## Reflect. Reply short.'"
          }
        ]
      }
    ]
  }
}
```

The bootstrap agent MUST generate this settings.json. Hooks are harness-executed — Claude cannot ignore them.

## 3. Per-Task Behavior

Before: follow 8-step workflow, auto-activated skills and path-scoped rules apply.
After: scan user message for rules → persist to CLAUDE.md (universal), `rules/` (scoped), or skill (concern). Update `.claude/` in same task. State what changed.

## 4. Rule Learning

- Separate TASK (do now) from RULE (always applies)
- Universal → CLAUDE.md. Scoped → `rules/` with `paths:`. Concern → skill
- No permission needed — just persist. Update if user contradicts existing rule.

## 5. Self-Maintenance

- New concern → new skill/rule
- Repo changed → update `context.md` + affected files
- Unused skill/rule → fix trigger or retire

## 6. Core Principles

**First-principles thinking.** Every `.claude/` file must be backed by evidence. If unverifiable, do not include it.

**Brevity.** Every loaded file costs tokens every turn. Write the minimum that enforces correct behavior. No explanations — only directives.

**Living system.** Skills, rules, and agents evolve with the repo — never left as static templates.

**User instructions are a source of truth.** When a user expresses a rule, persist it immediately.

## 7. Post-Install

After the bootstrap completes, **tell the user to restart Claude Code** (start a new session). CLAUDE.md is auto-loaded at session start — it does NOT activate mid-session.
