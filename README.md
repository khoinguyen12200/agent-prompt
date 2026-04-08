# Claude Bootstrap 🚀

> One command to give Claude Code a brain for your repo.

Installs skill libraries and configures **active skill loading** — skills automatically load when you need them.

---

## ✨ What It Does

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Install   │ ──► │    Detect    │ ──► │   Select    │
│  Mandatory  │     │    Project   │     │   Skills    │
└─────────────┘     └──────────────┘     └─────────────┘
                                              │
                                              ▼
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Prompt    │ ◄── │  Auto-Load   │ ◄── │   Install   │
│   "build"   │     │    Skills    │     │   Selected  │
└─────────────┘     └──────────────┘     └─────────────┘
```

1. **Installs mandatory skills** — gstack (23 specialists), superpowers, claude-mem
2. **Detects your project** — analyzes tech stack
3. **Lets you select skills** — from 180+ options via interactive prompts
4. **Skills ready to use** — Load manually or mention in prompt

---

## 🚀 Quick Start

```bash
# Step 1: Clone
!rm -rf /tmp/claude-bootstrap && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/claude-bootstrap
```

```
# Step 2: Tell Claude
Read /tmp/claude-bootstrap/install.md and bootstrap .claude/ in this project.
```

```
# Step 3: Restart when done
```

---

## 📦 What Gets Installed

### Mandatory (Always)
| Skill | Count | What |
|-------|-------|------|
| **gstack** | 23 | Planning, review, QA, shipping — YC-style workflow |
| **superpowers** | 12 | Debugging, refactoring, TDD |
| **claude-mem** | 1 | Memory across sessions |

### Optional (You Choose)

Claude detects your project and asks you to select from 180+ skills:

- **Frontend** — React, Vue, design patterns
- **Backend** — APIs, databases, ORMs
- **Automation** — 78+ SaaS app integrations
- **Security** — Testing, forensics
- **Creative** — Images, video, design
- **Productivity** — File mgmt, workspace tools

---

## 🎯 How to Use Skills

After install, tell Claude to load a skill:

```
Load gstack and run /office-hours
```

Or mention it in your prompt:

```
Using superpowers, debug this error...
```

| Skill Library | Commands Available |
|---------------|-------------------|
| gstack | /office-hours, /review, /qa, /ship, etc. |
| superpowers | systematic-debugging, subagent-driven-development, etc. |
| [installed] | See .claude/skills/ for full list |

---

## 📁 Project Structure After

```
.claude/
├── CLAUDE.md              # Skill reference
├── settings.json          # UserPromptSubmit hook
├── context.md             # Project knowledge
├── intent-map.yaml        # Intent → skill mapping
├── rules/                 # Project-specific rules
└── skills/                # Installed skills
    ├── gstack/
    ├── superpowers/
    ├── claude-mem/
    └── [your-selected]/
```

---

## 📚 Files

| File | Purpose |
|------|---------|
| `install.md` | Instructions for Claude to follow |
| `skills/*.md` | Skill catalog (180+ skills) |

---

## License

MIT © 2024
