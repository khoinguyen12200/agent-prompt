# Claude Bootstrap 🚀

> One command to give Claude Code a brain for your repo.

Installs skill libraries you select. All skills are optional — you choose what to install.

---

## ✨ What It Does

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Detect    │ ──► │   Recommend  │ ──► │   Select    │
│   Project   │     │    Skills    │     │   Skills    │
└─────────────┘     └──────────────┘     └─────────────┘
                                               │
                                               ▼
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Prompt    │ ◄── │  Load Skill  │ ◄── │   Install   │
│   "build"   │     │              │     │   Selected  │
└─────────────┘     └──────────────┘     └─────────────┘
```

1. **Detects your project** — analyzes tech stack
2. **Recommends skills** — suggests highly recommended + optional
3. **You select** — choose which to install via interactive prompts
4. **Skills ready to use** — Load manually when needed

---

## 🚀 Quick Start

**Step 1:** Clone this repo to temp:

!rm -rf /tmp/claude-bootstrap && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/claude-bootstrap

**Step 2:** Tell Claude to install:

Read /tmp/claude-bootstrap/install.md and bootstrap .claude/ in this project.

**Step 3:** Restart Claude Code when done.

---

## 📦 What Gets Installed

### Highly Recommended
Claude will strongly suggest these 3 for any project:

| Skill | Count | What |
|-------|-------|------|
| **gstack** | 23 | Planning, review, QA, shipping — YC-style workflow |
| **superpowers** | 12 | Debugging, refactoring, TDD |
| **claude-mem** | 1 | Memory across sessions |

### Optional Categories (You Choose)

| Category | Skills |
|----------|--------|
| **Workflow** | gstack, superpowers |
| **Memory** | claude-mem |
| **Frontend** | React, Vue, design patterns |
| **Backend** | APIs, databases, ORMs |
| **Documents** | PDF, Word, Excel |
| **Automation** | 78+ SaaS app integrations |
| **Security** | Testing, forensics |
| **Creative** | Images, video, design |
| **Productivity** | File mgmt, workspace tools |

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

| Skill | Commands Available |
|-------|-------------------|
| gstack | /office-hours, /review, /qa, /ship, etc. |
| superpowers | systematic-debugging, subagent-driven-development, etc. |
| [installed] | See .claude/skills/ for full list |

---

## 📁 Project Structure After

```
.claude/
├── CLAUDE.md              # Skill reference
├── context.md             # Project knowledge
├── rules/                 # Project-specific rules
└── skills/                # Installed skills (you selected)
    ├── [workflow]/
    ├── [memory]/
    ├── [frontend]/
    └── ...
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
