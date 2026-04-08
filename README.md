# Claude Bootstrap 🚀

> One command to give Claude Code a brain for your repo.

Installs skill libraries you select and **dynamically configures** Claude based on what you installed.

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
│   Generate  │ ◄── │ Read Config  │ ◄── │   Install   │
│  settings   │     │  from Skills │     │   Selected  │
│    .json    │     │              │     │             │
└─────────────┘     └──────────────┘     └─────────────┘
```

1. **Detects your project** — analyzes tech stack
2. **Recommends skills** — organized into 6 categories
3. **You select** — choose which to install
4. **Installs skills** — clones or installs via `/plugin`
5. **Reads skill configs** — extracts what each skill needs
6. **Generates settings.json** — merges all configurations dynamically

---

## 🚀 Quick Start

**Step 1:** Clone this repo to temp:

```
!rm -rf /tmp/claude-bootstrap && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/claude-bootstrap
```

**Step 2:** Tell Claude to install:

```
Read /tmp/claude-bootstrap/install.md and bootstrap .claude/ in this project.
```

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

## ⚙️ Dynamic Configuration

The bootstrap reads each installed skill's `SKILL.md` frontmatter to extract:

- **Hooks** → Merged into `.claude/settings.json`
- **Permissions** → Added to `permissions.allow`
- **Auto-load paths** → Created as path-scoped rules

**Example:** If you install `gstack`:
```yaml
# From gstack/SKILL.md
hooks:
  SessionStart:
    - command: echo "[gstack] Ready"
allowed-tools: Bash(git *) Bash(gh *)
```

Bootstrap generates:
```json
{
  "permissions": {
    "allow": ["Bash(git *)", "Bash(gh *)"]
  },
  "hooks": {
    "SessionStart": [{
      "type": "command",
      "command": "echo '[gstack] Ready'"
    }]
  }
}
```

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
├── settings.json          # Dynamic config (merged from skills)
├── rules/                 # Path-scoped auto-load rules
└── skills/                # Installed skills (you selected)
    ├── gstack/
    ├── superpowers/
    ├── claude-mem/
    ├── [other-skills-you-selected]/
    └── ...
```

---

## 📚 Files

| File | Purpose |
|------|---------|
| `install.md` | Instructions for Claude to follow |
| `skills/*.md` | Skill catalog with expected configurations |
| `SKILL.md` | How dynamic configuration works |

---

## License

MIT © 2024
