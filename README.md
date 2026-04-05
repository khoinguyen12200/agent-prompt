# Claude Bootstrap Prompt

> One prompt to give Claude Code a brain for your repo.

Paste two lines into **Claude Code** and it builds a complete `.claude/` system — rules, skills, agents, hooks, and commands — tailored to your codebase. Then it maintains itself.

Enforces an **8-step workflow** on every task: **Think → Load → Plan → Build → Review → Test → Ship → Reflect**

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
4. **Restart Claude Code** after it finishes.

---

## What Gets Generated

```
.claude/
  CLAUDE.md              # Auto-loaded every turn — workflow + universal rules (under 200 lines)
  settings.json          # Hooks: SessionStart, Stop, PostCompact
  rules/                 # Scoped constraints with paths: (native, auto-load on file access)
  skills/                # Concern knowledge with paths: (native, auto-triggered)
  agents/                # Subagents for isolated specialized tasks (native)
  commands/              # User-invoked via /command-name (native)
  context.md             # Project knowledge (@imported by CLAUDE.md)
```

### Enforcement Stack

| Layer | Mechanism | Reliability |
|---|---|---|
| CLAUDE.md | Re-injected every turn | High |
| `Stop` hook | Checks for ## Reflect after every response | Guaranteed |
| `PostCompact` hook | Re-injects workflow after context compaction | Guaranteed |
| `rules/` with `paths:` | Auto-loads when matching files accessed | High (native) |
| `skills/` with `paths:` | Auto-triggered on file/description match | Medium (~44%) |
| `agents/` | Isolated context, tool-restricted | High |

---

## The 8-Step Workflow

| Step | What Claude Does |
|------|------------------|
| **Think** | Gather context, read files, ask questions |
| **Load** | Invoke all matching skills and plugins. List what was loaded. |
| **Plan** | Break into subtasks, choose simplest approach |
| **Build** | Implement with clean code following conventions |
| **Review** | Check for bugs, edge cases, regressions |
| **Test** | Run tests, fix failures, add coverage |
| **Ship** | Summarize changes. **STOP — proceed to Reflect.** |
| **Reflect** | Update `.claude/` docs. State what changed or why not. |

Response is **INCOMPLETE** until `## Reflect` is shown. `Stop` hook enforces this.

---

## Key Features

- **Native-first** — uses CLAUDE.md, hooks, rules/, skills/, agents/, commands/ (all native)
- **Three enforcement layers** — CLAUDE.md (every turn) + hooks (guaranteed) + rules (per-file)
- **Long-conversation fix** — `PostCompact` hook re-injects workflow after context compaction
- **Concern-specific** — skills/rules decomposed per responsibility area, not generic domains
- **Community skills** — installs from [anthropics/skills](https://github.com/anthropics/skills) and [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
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
    overview.md                 # Role, native features, workflow, structure
    contracts/
      core-contracts.md         # CLAUDE.md template, settings.json template, behavior contracts
    commands/
      update-claude-docs.md
      fpt.md
    guides/
      decision-making.md
      inspect-repo.md
      create-central-files.md   # CLAUDE.md + settings.json + context.md
      create-rules.md           # Scoped rules with paths:
      create-skills.md          # Concern skills with paths:
      create-agents.md          # Subagents
      create-commands.md
      install-community-skills.md
      secrets.md
      output-requirements.md
```

---

## License

MIT
