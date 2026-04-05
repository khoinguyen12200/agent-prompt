# Claude Bootstrap Prompt

> One prompt to give Claude Code a brain for your repo.

Paste two lines into **Claude Code** and it builds a complete `.claude/` system — skills, commands, and a smart dispatcher — tailored to your codebase. Then it maintains itself.

Enforces a **7-step workflow** on every task: **Think → Plan → Build → Review → Test → Ship → Reflect**

---

## Quick Start

1. Open your project in Claude Code
2. Paste this:
   ```
   ! rm -rf /tmp/agent-prompt-install && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/agent-prompt-install
   ```
3. Then paste:
   ```
   Read /tmp/agent-prompt-install/install.md and follow its instructions to bootstrap .claude/ in this project.
   ```
4. Done.

Claude will:
- Clone the bootstrap + community skill repos
- Inspect your codebase
- Generate `.claude/` with workflow, skills, and relevant community skills

---

## What Gets Generated

```
.claude/
  CLAUDE.md              # Auto-loaded every session — workflow + project rules (under 200 lines)
  context.md             # Project overview, stack, architecture, conventions
  skills/                # Auto-triggered skill directories (NATIVE)
    task-execution/      # 7-step workflow (always active)
    [concern-a]/         # Concern-specific guidance (auto-triggers on matching tasks)
    [concern-b]/         # ...
  commands/              # User-invoked via /command-name (NATIVE)
  settings.json          # Permissions and hooks
```

### Native vs Convention

| Feature | Native? | How it works |
|---------|---------|---|
| `CLAUDE.md` | **Yes** — auto-loaded | Read every session, guaranteed |
| `commands/` | **Yes** — `/name` | User types slash command |
| `skills/` | **Yes** — auto-triggered | Claude activates based on SKILL.md description matching the task |
| `context.md` | No — convention | Works because CLAUDE.md tells Claude to read it |

> The old `agents/` and `rules/` directories have been replaced. Agents are now skills (native auto-triggering). Universal rules go in CLAUDE.md directly. Concern-specific rules go inside the relevant skill's SKILL.md.

---

## The 7-Step Workflow

| Step | What Claude Does |
|------|------------------|
| **Think** | Gather context, read files, ask questions |
| **Plan** | Break into subtasks, choose simplest approach |
| **Build** | Implement with clean code following conventions |
| **Review** | Check for bugs, edge cases, regressions |
| **Test** | Run tests, fix failures, add coverage |
| **Ship** | Summarize changes. **STOP — proceed to Reflect.** |
| **Reflect** | Update `.claude/` docs. State what changed or why not. |

A response is **INCOMPLETE** until `## Reflect` is shown.

---

## Key Features

- **Native-first architecture** — uses only Claude Code's native features (CLAUDE.md, skills/, commands/)
- **Concern-specific skills** — auto-triggered, not "frontend skill" but granular per responsibility area
- **Rule learning** — user preferences are persisted into CLAUDE.md or skills automatically
- **Community skills** — installs relevant skills from [anthropics/skills](https://github.com/anthropics/skills) and [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
- **Post-install activation** — after bootstrapping, the agent reads its own CLAUDE.md to start following it immediately
- **Self-maintaining** — `.claude/` updates itself after every task

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
    overview.md                 # Role, workflow, structure, native vs convention
    agent-workflow.md           # The 7-step workflow definitions
    contracts/
      core-contracts.md         # All behavioral contracts
    commands/
      update-claude-docs.md
      fpt.md
    guides/
      decision-making.md
      inspect-repo.md
      create-central-files.md   # CLAUDE.md + context.md
      create-skills.md          # Concern skills + workflow skills
      create-commands.md
      install-community-skills.md
      secrets.md
      output-requirements.md
```

---

## License

MIT
