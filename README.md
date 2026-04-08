# Claude Bootstrap 🚀

> One command to give Claude Code a brain for your repo.

Installs skill libraries and **makes them actually work** with proper linking and configuration.

---

## ✨ What It Does

```
1. Detect project type
2. Categorize skills by relevance (High/Medium/Low potential)
3. User selects skills
4. Install with CORRECT linking:
   - gstack: Links all 23 sub-skills individually
   - superpowers: Installs 12 workflow skills
   - Others: Copy to proper location
5. Generate CLAUDE.md with HOW to use each skill
6. Create dynamic settings.json
```

**Key Difference:** We don't just clone repos. We ensure skills are discoverable and usable.

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

## 🎯 How to Use Installed Skills

After install, **you must type the command** to invoke a skill:

```
/office-hours     ← Product planning
/review           ← Code review
/qa               ← Browser testing
/ship             ← Release workflow
/cso              ← Security audit
/systematic-debugging  ← Debug issues
```

Or type `/` to see all available skills.

---

## 📦 What Gets Installed

### Foundation (Highly Recommended)

| Skill | Commands | Count |
|-------|----------|-------|
| **gstack** | `/office-hours`, `/review`, `/qa`, `/ship`, `/cso`, `/browse`, etc. | 23 |
| **superpowers** | `/systematic-debugging`, `/tdd`, `/subagent-development`, etc. | 12 |
| **claude-mem** | `/mem` | 1 |

### By Category

| Category | Examples |
|----------|----------|
| **Build** | `/react-components`, `/api-design`, `/prisma`, `/playwright` |
| **Data** | `/csv-data-summarizer`, `/deep-research` |
| **Create** | `/docx`, `/creative-art`, `/imagen` |
| **Secure** | `/ffuf-web-fuzzing`, `/threat-hunting` |
| **Integrate** | `/github-automation`, `/slack-automation`, `/notion-automation` |

---

## 📁 Project Structure After

```
.claude/
├── CLAUDE.md              # HOW to use installed skills (reference)
├── context.md             # Project knowledge
├── settings.json          # Dynamic config from skills
├── rules/                 # Path-scoped auto-load rules
└── skills/
    ├── gstack/            # Main gstack repo
    │   ├── setup          # Setup script
    │   ├── bin/           # Utilities
    │   └── office-hours/  # Sub-skill
    │   └── review/        # Sub-skill
    │   └── qa/            # Sub-skill
    │   └── ... (20 more)
    │
    ├── office-hours/ → gstack/office-hours/SKILL.md  # LINKED
    ├── review/ → gstack/review/SKILL.md              # LINKED
    ├── qa/ → gstack/qa/SKILL.md                      # LINKED
    ├── ship/ → gstack/ship/SKILL.md                  # LINKED
    ├── cso/ → gstack/cso/SKILL.md                    # LINKED
    ├── ... (18 more linked skills)
    │
    ├── superpowers/
    │   └── skills/
    │       ├── systematic-debugging/SKILL.md
    │       ├── test-driven-development/SKILL.md
    │       └── ... (10 more)
    │
    └── [other skills]/
```

**Why link gstack sub-skills?** Claude Code looks for `SKILL.md` one level under `.claude/skills/`. Without linking, the 23 sub-skills would be hidden inside `gstack/`.

---

## 📚 Files

| File | Purpose |
|------|---------|
| `install.md` | Instructions for Claude to follow |
| `skills/*.md` | Skill catalog with install details |

---

## License

MIT © 2024
