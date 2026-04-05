# Core Contracts

## 1. CLAUDE.md Template

Generate root `CLAUDE.md` using this template. Fill in project rules for this repo.

```
## .claude/ System

FIRST PRINCIPLES: Every statement must be backed by evidence — code you read, patterns you observed, or explicit user statements.

### MANDATORY 8-STEP WORKFLOW — DO NOT SKIP

**Every task MUST follow these 8 steps. This is not optional.**

**Think → Load → Plan → Build → Review → Test → Ship → Reflect**

1. **Think** — Read the request. Identify goal, constraints, success criteria. Gather context by reading relevant files. Ask clarifying questions if ambiguous. Do NOT jump to code.
2. **Load** — Check all available skills and plugins. Invoke every one that matches this task. List what you loaded (e.g., "Loaded: /ui-components, /api-design"). If none match, state "No matching skills." Do NOT proceed without completing this step.
3. **Plan** — Break into subtasks. Identify affected files. Choose the simplest approach. Consider edge cases and regressions. For significant changes, get user approval first. No coding yet.
4. **Build** — Execute the plan. Write clean, minimal code following project conventions. Handle blockers by pausing and reassessing.
5. **Review** — Re-read requirements vs implementation. Check for bugs, edge cases, security issues. Review diffs holistically. Remove debug code. Fix issues before testing.
6. **Test** — Run relevant tests. Fix failures. Add tests for new behavior. Failing tests are blockers.
7. **Ship** — Summarize what changed, why, and how. List key files modified. Confirm it works. **STOP — you are not done. Proceed to Reflect.**
8. **Reflect** — Check if `.claude/` needs updating (CLAUDE.md, context.md, rules, skills). Extract any user-expressed rules. State what `.claude/` files changed or why none needed updating.

**Show each step label in your response. Your response is INCOMPLETE until ## Reflect is shown.** Trivial tasks may abbreviate steps 5-8, but steps 1-4 are NEVER skippable.

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
            "command": "echo 'Session started. The 8-step workflow is active: Think → Load → Plan → Build → Review → Test → Ship → Reflect. Load matching skills before coding.'"
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
            "command": "echo 'Check: Did your response include ## Reflect? If not, your response is INCOMPLETE. Add ## Reflect with .claude/ status on your next message.'"
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
            "command": "echo 'Context was compacted. Reminder: Follow the 8-step workflow (Think → Load → Plan → Build → Review → Test → Ship → Reflect). Load skills before coding. Show ## Reflect before finishing.'"
          }
        ]
      }
    ]
  }
}
```

**Why these hooks:**
- `SessionStart` — sets expectations at the start of every session
- `Stop` — checks for ## Reflect after every response (catches the most common skip)
- `PostCompact` — re-injects workflow after context compaction in long conversations (fixes drift)

The bootstrap agent MUST generate this settings.json. Hooks are harness-executed — Claude cannot ignore them.

## 3. Per-Task Behavior

Before starting any task:
1. Read `CLAUDE.md` and follow the 8-step workflow.
2. Claude Code will auto-activate matching skills (by description and `paths:`).
3. Path-scoped rules in `rules/` auto-load when matching files are accessed.

Before finishing any task:
1. Scan user instructions for preferences/constraints; persist to CLAUDE.md (universal), `rules/` (scoped), or relevant skill (concern-specific).
2. Check whether `.claude/` needs updating. Update in the same task.
3. State what changed or why nothing did.

## 4. Rule Learning

Scan every user message for implicit preferences, constraints, or conventions.

**Procedure:**
1. Separate the TASK (what to do now) from the RULE (how things should always be).
2. Universal rules → add to CLAUDE.md "Project Rules" section.
3. Scoped rules (apply to specific files) → add to `rules/` with `paths:` frontmatter.
4. Concern-specific patterns → add to the relevant skill's SKILL.md.
5. Tell the user what you persisted and where.

**Constraints:** Do not ask permission — just persist. Only persist project-specific decisions. If the user contradicts an existing rule, update it.

## 5. Self-Maintenance

- New concern → create a new skill and/or rule.
- Repo structure changed → update `context.md` and affected skills/rules.
- Unused skill/rule → fix its trigger conditions or retire it.
- Never leave `.claude/` stale. Prefer small continuous updates.

## 6. Core Principles

**First-principles thinking.** Every `.claude/` file must be backed by evidence. If unverifiable, do not include it.

**Living system.** Skills, rules, and agents evolve with the repo — never left as static templates.

**User instructions are a source of truth.** When a user expresses a rule, persist it immediately.

## 7. Post-Install

After the bootstrap completes, **tell the user to restart Claude Code** (start a new session). CLAUDE.md is auto-loaded at session start — it does NOT activate mid-session.
