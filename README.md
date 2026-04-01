# Claude Bootstrap Prompt

> One line of text to give Claude Code a brain for your repo.

Paste a single sentence into **Claude Code** and it automatically builds a complete `.claude/` system — agents, rules, skills, and a smart dispatcher — tailored to your actual codebase. Then it maintains itself forever.

This system also enforces a **7-step workflow** on every task:

**Think → Plan → Build → Review → Test → Ship → Reflect**

---

## Quick Start

1. Open your project in Claude Code
2. Paste this **one line**:
   ```
   Read and execute the instructions from https://raw.githubusercontent.com/khoinguyen12200/agent-prompt/main/install.md
   ```
3. Done.

Claude will:
- Fetch the installer from this repo
- Inspect your codebase
- Generate the `.claude/` system with the 7-step workflow baked in

No manual copying. No configuration.

---

## What Gets Generated

```
.claude/
  CLAUDE.md              # The dispatcher — tells the agent what to load per task
  context.md             # Project overview, stack, architecture, conventions
  agents/                # Specialist agents, matched to tasks by trigger conditions
  rules/                 # Hard constraints, loaded before every task
  skills/                # Step-by-step workflows, auto-triggered when matched
  commands/              # User-invoked via /command-name
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

## The 7-Step Workflow

Every task — no matter how small — follows this workflow:

| Step | What Claude Does |
|------|------------------|
| **Think** | Understand the problem, gather context, research, ask questions |
| **Plan** | Break into subtasks, identify files, choose the simplest approach |
| **Build** | Implement with minimal, clean code following project conventions |
| **Review** | Critically examine code for bugs, edge cases, and regressions |
| **Test** | Run tests, fix failures, add coverage for new behavior |
| **Ship** | Summarize changes, confirm it works, leave the codebase clean |
| **Reflect** | Assess the outcome, note improvements for next time |

These steps are enforced by:
- `.claude/skills/task-execution.md` — the master workflow skill
- `.claude/rules/workflow-step-enforcement.md` — a hard rule loaded on every task

---

## How It Works

### The Dispatch Loop

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
                    |  Follow 7-step  |
                    |    workflow     |
                    +--------+--------+
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
| `/fpt` | First-principles thinking mode — forces deep analysis before acting. Maps directly to the **Think** step. |

---

## Repository Structure

```
agent-prompt/
  bootstrap/
    overview.md                 # Entry point: role, assumptions, workflow, structure, dispatcher
    agent-workflow/             # The 7 step-by-step workflow docs
      01-think.md
      02-plan.md
      03-build.md
      04-review.md
      05-test.md
      06-ship.md
      07-reflect.md
    contracts/
      auto-update.md            # Mandatory auto-update contract
      rule-learning.md          # Rule learning from user instructions
      core-behavior.md          # Core behavior contract
      self-maintenance.md       # Self-maintenance rules
    commands/
      update-claude-docs.md     # Manual update command
      fpt.md                    # First-principles thinking command
    guides/
      decision-making.md        # How to decide what to create
      inspect-repo.md           # Phase 1: inspect repository
      create-central-files.md   # Phase 2: create central files
      create-agents.md          # Phase 3: create dynamic agents
      create-rules.md           # Phase 4: create dynamic rules
      create-commands.md        # Phase 5: create dynamic commands
      create-skills.md          # Phase 6: create dynamic skills
      secrets.md                # Phase 7: gitignore and secrets
      output-requirements.md    # Phase 9: output requirements
  install.md                    # Remote installer — fetched by the one-line prompt
  README.md
```

---

## Design Principles

| Principle | What It Means |
|-----------|--------------|
| **One-line install** | Users paste a single sentence. Everything else is automatic. |
| **7-step workflow** | Every task follows Think → Plan → Build → Review → Test → Ship → Reflect. |
| **First principles** | Every `.claude/` file is backed by evidence. Zero assumptions. |
| **Smart dispatch** | `CLAUDE.md` tells the agent exactly which files to load — no wasted tokens. |
| **Self-maintaining** | The system updates itself after every task. Rules, agents, and skills evolve with your project. |
| **Rule learning** | User preferences become persistent rules automatically. Say it once, enforced forever. |
| **Minimal** | Blank repos get a lean scaffold. Mature repos get full coverage. Nothing speculative. |

---

## Works With Any Repo

Blank project, backend API, frontend app, full-stack, monorepo, CLI tool, library, mobile app, infra repo — it detects what you have and generates only what's justified.

---

## License

MIT
