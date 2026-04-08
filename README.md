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
2. **Recommends skills** — organized into 6 categories
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

### Skill Categories (You Choose)

| Category | Skills |
|----------|--------|
| **Foundation** | gstack, superpowers, claude-mem |
| **Build** | Frontend, backend, database, testing |
| **Data** | Analysis, extraction, research |
| **Create** | Documents, media, design, content |
| **Secure** | Security testing, forensics |
| **Integrate** | App automation, productivity, business |

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
├── context.md             # Project knowledge
├── rules/                 # Project-specific rules
└── skills/                # Installed skills (you selected)
    ├── foundation/
    ├── build/
    ├── data/
    ├── create/
    ├── secure/
    └── integrate/
```

---

## 📚 Files

| File | Purpose |
|------|---------|
| `install.md` | Instructions for Claude to follow |
| `skills/*.md` | Skill catalog by category |

---

## License

MIT © 2024
