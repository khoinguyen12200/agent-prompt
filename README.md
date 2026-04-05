# Claude Bootstrap Prompt

> One prompt to give Claude Code a brain for your repo.

Paste two lines into **Claude Code** and it builds a complete `.claude/` system — agents, rules, skills, and a smart dispatcher — tailored to your codebase. Then it maintains itself.

Enforces a **7-step workflow** on every task: **Think → Plan → Build → Review → Test → Ship → Reflect**

---

## Quick Start

1. Open your project in Claude Code
2. Paste this:
   ```
   ! git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/agent-prompt-install
   ```
3. Then paste:
   ```
   Read /tmp/agent-prompt-install/install.md and follow its instructions to bootstrap .claude/ in this project.
   ```
4. Done.

Claude will:
- Clone the bootstrap + community skill repos
- Inspect your codebase
- Generate `.claude/` with the 7-step workflow, agents, rules, and relevant skills

---

## What Gets Generated

```
.claude/
  CLAUDE.md              # Dispatcher (under 200 lines) — auto-loaded every session
  context.md             # Project overview, stack, architecture, conventions
  agents/                # Concern-specific agents with YAML frontmatter
  rules/                 # Hard constraints with optional paths: scoping
  skills/                # Skill directories (SKILL.md + optional scripts/references/assets)
  commands/              # User-invoked via /command-name
```

| File | Native? | Purpose |
|------|---------|---------|
| `CLAUDE.md` | **Yes** — auto-loaded | 7-step workflow inline + dispatch table |
| `commands/*.md` | **Yes** — `/name` | On-demand tools |
| `agents/*.md` | Via CLAUDE.md | Concern-specific role definitions |
| `rules/*.md` | Via CLAUDE.md | Hard constraints, always loaded |
| `skills/*/SKILL.md` | Via CLAUDE.md | Repeatable workflows |
| `context.md` | Via CLAUDE.md | Project knowledge base |

> Only `CLAUDE.md` and `commands/` are native Claude Code features. Everything else works because `CLAUDE.md` instructs Claude to read them.

---

## The 7-Step Workflow

| Step | What Claude Does |
|------|------------------|
| **Think** | Gather context, read files, ask questions |
| **Plan** | Break into subtasks, choose simplest approach |
| **Build** | Implement with clean code following conventions |
| **Review** | Check for bugs, edge cases, regressions |
| **Test** | Run tests, fix failures, add coverage |
| **Ship** | Summarize changes, confirm it works |
| **Reflect** | Note improvements, auto-update `.claude/` |

Enforced by: inline block in `CLAUDE.md` (primary) + `skills/task-execution/SKILL.md` (detail) + `rules/workflow-step-enforcement.md` (hard rule).

---

## Key Features

- **Smart dispatch** — `CLAUDE.md` maps tasks to specific agents/rules/skills. No wasted tokens.
- **Concern-specific agents** — not "frontend agent" but granular agents per responsibility area.
- **Rule learning** — user preferences become persistent rules automatically.
- **Community skills** — installs relevant skills from [anthropics/skills](https://github.com/anthropics/skills) and [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills).
- **Self-maintaining** — `.claude/` updates itself after every task.
- **First principles** — every file backed by evidence, zero assumptions.

---

## Built-in Commands

| Command | What It Does |
|---------|-------------|
| `/update-claude-docs` | Full audit of `.claude/` against current repo |
| `/fpt` | First-principles thinking mode |

---

## Repository Structure

```
agent-prompt/
  install.md                    # Installer — the entry point
  bootstrap/
    overview.md                 # Role, assumptions, workflow, structure
    agent-workflow.md           # The 7-step workflow definitions
    contracts/
      core-contracts.md         # All behavioral contracts (merged)
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
      install-community-skills.md  # Phase 6b: community skills
      secrets.md                # Phase 7: gitignore and secrets
      output-requirements.md    # Phase 9: output requirements
```

---

## License

MIT
