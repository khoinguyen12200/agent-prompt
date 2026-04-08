# Claude Bootstrap

Installs skill libraries and configures active skill loading for Claude Code.

## How It Works

1. **User runs 2 commands** (see below)
2. **Claude reads install.md** and follows instructions
3. **Claude installs mandatory skills** (gstack + superpowers)
4. **Claude detects project type** and installs relevant optional skills
5. **Claude generates core files** (CLAUDE.md, settings.json, etc.)
6. **User restarts Claude Code**
7. **UserPromptSubmit hook actively loads skills** when user prompts

## Quick Start (2 Commands)

**Step 1:** Clone this repo to temp
```bash
rm -rf /tmp/claude-bootstrap && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/claude-bootstrap
```

**Step 2:** Tell Claude to install
```
Read /tmp/claude-bootstrap/install.md and follow its instructions to bootstrap .claude/ in this project.
```

**Step 3:** Restart Claude Code when Claude says it's done

## What Gets Installed

### Mandatory (Always)
| Skill | Count | Description |
|-------|-------|-------------|
| gstack | 23 | Specialists: /office-hours, /review, /qa, /ship, etc. |
| superpowers | 12 | Development workflow: debugging, refactoring, planning |

### Optional (Auto-detected by Claude)
| Skill | When Detected |
|-------|---------------|
| anthropics-skills | PDF/Word/Excel work |
| awesome-claude-skills | Web scraping, SaaS integrations |
| frontend-design | React/Vue/Angular projects |
| prisma | Database ORM usage |
| marketing | Marketing content needs |
| firecrawl | Web scraping needs |

## After Restart

When you type a prompt, the hook tells Claude which skill to load:

| You Type | Claude Loads |
|----------|--------------|
| "build feature" | gstack /office-hours |
| "review code" | gstack /review |
| "test this" | gstack /qa |
| "ship it" | gstack /ship |
| "debug error" | superpowers systematic-debugging |
| "refactor" | superpowers subagent-driven-development |

## Skill Catalog (180+ Skills)

See `skills/` folder for complete list:
- Name, source URL, install command, description

## Files

- `install.md` — Instructions for Claude to follow
- `skills/*.md` — Skill catalog by category
- `TEST.md` — Original requirements

## License

MIT
