# Claude Bootstrap Prompt

> One prompt to give Claude Code a brain for your repo.

Paste this prompt into Claude Code and it builds a complete `.claude/` system — agents, rules, skills, and a smart dispatcher — tailored to your actual codebase. Then it maintains itself forever.

---

## Quick Start

```
1. Open your project in Claude Code
2. Copy the contents of claude-bootstrap-prompt.md
3. Paste it in
4. Done.
```

Claude inspects your repo, detects your stack, and generates everything. No configuration needed.

---

## What Gets Generated

```
.claude/
  CLAUDE.md       # The dispatcher — tells the agent what to load per task
  context.md      # Project overview, stack, architecture, conventions
  agents/         # Specialist agents, matched to tasks by trigger conditions
  rules/          # Hard constraints, loaded before every task
  skills/         # Step-by-step workflows, auto-triggered when matched
  commands/       # User-invoked via /command-name
```

### How Each File Works

| File | Purpose | When It's Used |
|------|---------|---------------|
| `CLAUDE.md` | Dispatch table — maps task types to the right agents, rules, skills | Auto-loaded every session by Claude Code |
| `context.md` | Project knowledge — stack, architecture, directories, conventions | Read before tasks that need project context |
| `agents/*.md` | Role definitions — responsibilities, guardrails, inspection steps | Activated when dispatch table matches task type |
| `rules/*.md` | Hard constraints — things the agent must never violate | **Always** loaded before every task |
| `skills/*.md` | Workflows — step-by-step procedures for recurring tasks | Auto-triggered when dispatch table matches task type |
| `commands/*.md` | On-demand tools — user types `/command-name` to invoke | Only when user triggers them |

---

## How It Works

### The Dispatch Loop

Every Claude Code session follows this loop:

```
                    +-----------------+
                    |   User's Task   |
                    +--------+--------+
                             |
                    +--------v--------+
                    |  Read CLAUDE.md |  (auto-loaded by Claude Code)
                    |  dispatch table |
                    +--------+--------+
                             |
              +--------------+--------------+
              |              |              |
     +--------v---+  +------v------+  +----v-------+
     | Load ALL   |  | Load matched|  | Load matched|
     | rules/     |  | agents/     |  | skills/     |
     | (always)   |  | (selective) |  | (selective) |
     +--------+---+  +------+------+  +----+-------+
              |              |              |
              +--------------+--------------+
                             |
                    +--------v--------+
                    |    Do the work   |
                    +--------+--------+
                             |
              +--------------+--------------+
              |              |              |
     +--------v---+  +------v------+  +----v-------+
     | Validate   |  | Learn new   |  | Update     |
     | all rules  |  | rules from  |  | .claude/   |
     |            |  | user's words|  | if needed  |
     +------------+  +-------------+  +------------+
```

**Rules** are always loaded — they're hard constraints.
**Agents** and **skills** are loaded selectively — only what matches the task type, guided by the dispatch table.

### Rule Learning

When you say something like:

> "Fix the routes — database queries should only go through model classes, not directly in routes"

Claude does two things:
1. Fixes the routes
2. Extracts "database access only through models" and saves it to `.claude/rules/database-access.md`

Every future session enforces that rule automatically. You teach it once, it remembers forever.

### First-Principles Thinking

The agent never assumes. Every rule, agent, skill, and structure is built from verified evidence — files it read, patterns it observed, or things you explicitly said. If it can't verify something, it doesn't write it.

---

## Built-in Commands

| Command | What It Does |
|---------|-------------|
| `/update-claude-docs` | Full audit of every `.claude/` file against the current repo state |
| `/fpt` | First-principles thinking mode — forces deep analysis before acting. For important tasks where getting it right matters more than speed. |

---

## Design Principles

| Principle | What It Means |
|-----------|--------------|
| **First principles** | Every `.claude/` file is backed by evidence. Zero assumptions. |
| **Smart dispatch** | `CLAUDE.md` tells the agent exactly which files to load — no wasted tokens reading everything. |
| **Self-maintaining** | The system updates itself after every task. Rules, agents, and skills evolve with your project. |
| **Rule learning** | User preferences become persistent rules automatically. Say it once, enforced forever. |
| **Minimal** | Blank repos get a lean scaffold. Mature repos get full coverage. Nothing speculative. |

---

## Works With Any Repo

Blank project, backend API, frontend app, full-stack, monorepo, CLI tool, library, mobile app, infra repo — it detects what you have and generates only what's justified.

---

## License

MIT
