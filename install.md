# Claude Bootstrap Installer

You (Claude) are the Bootstrap Agent. Follow these steps to set up skill libraries for this project.

## Your Tasks

### Step 1: Read Skill Catalog

Read all files in `/tmp/claude-bootstrap/skills/` to understand available skills.

### Step 2: Detect Project

Scan the current working directory and identify:
- Technology stack (React, Vue, Node, Python, Go, Rust, etc.)
- Project type (frontend/backend/full-stack/mobile)
- Key frameworks (Prisma, Django, FastAPI, etc.)
- Needs (documents, scraping, automation, etc.)

### Step 3: Install Mandatory Skills

These are ALWAYS installed:

```bash
mkdir -p .claude/skills

# gstack - 23 specialists (MANDATORY)
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup && cd ../..

# superpowers - development workflow (MANDATORY)
# Install via plugin after restart: /plugin install superpowers@claude-plugins-official
```

### Step 4: Install Optional Skills (Based on Detection)

Based on what you detected in Step 2, install relevant skills:

**If documents detected (.pdf, .docx, .xlsx work):**
```bash
git clone --single-branch --depth 1 https://github.com/anthropics/skills.git .claude/skills/anthropics
```
Install after restart: `/plugin install document-skills@anthropic-agent-skills`

**If web scraping/automation needed:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```

**If specific SaaS integrations detected (Slack, GitHub, Notion, etc.):**
The awesome-claude-skills repo includes 78+ app automation skills.

**If frontend design needed (React/Vue projects):**
Install after restart: `/plugin install frontend-design`

**If Prisma ORM detected:**
Install after restart: `/plugin install prisma`

**If marketing content needed:**
Install after restart: `/plugin install marketing`

**If web scraping needed:**
Install after restart: `/plugin install firecrawl`

### Step 5: Generate Core Files

Create these files in `.claude/`:

**CLAUDE.md:**
```markdown
## .claude/ System

### Mandatory Skills (Always Available)
- **gstack** — 23 specialists: /office-hours, /review, /qa, /ship, /cso
- **superpowers** — debugging, refactoring, planning

### Optional Skills (Project-Specific)
[LIST INSTALLED OPTIONAL SKILLS HERE]

### Quick Reference
| Intent | Command |
|--------|---------|
| build feature | Load gstack. Run /office-hours |
| review code | Load gstack. Run /review |
| test | Load gstack. Run /qa |
| ship | Load gstack. Run /ship |
| debug | Load superpowers. Use systematic-debugging |
| refactor | Load superpowers. Use subagent-driven-development |
| plan | Load superpowers. Use brainstorming |

### Full Catalog
See .claude/skills/README.md for complete list.

### Principles
- Reply short — lead with answer
- Reflect optional

@import .claude/context.md
```

**settings.json:**
```json
{
  "hooks": {
    "SessionStart": [{
      "matcher": "",
      "hooks": [{
        "type": "command",
        "command": "echo '[Claude] Skill libraries active'"
      }]
    }],
    "UserPromptSubmit": [{
      "matcher": "",
      "hooks": [{
        "type": "command",
        "command": "echo '[Claude] Analyzing prompt to load relevant skills...'"
      }]
    }]
  }
}
```

**context.md:**
Generate based on project detection from Step 2:
- Project name and type
- Technology stack
- Key directories
- Observed conventions

**intent-map.yaml:**
```yaml
intents:
  build:
    patterns: [build, create, "new feature", implement]
    action: "Load gstack. Run /office-hours"
  review:
    patterns: [review, "check code", audit]
    action: "Load gstack. Run /review"
  test:
    patterns: [test, qa, verify]
    action: "Load gstack. Run /qa"
  ship:
    patterns: [ship, deploy, release]
    action: "Load gstack. Run /ship"
  debug:
    patterns: [debug, fix, error, bug]
    action: "Load superpowers. Use systematic-debugging"
  refactor:
    patterns: [refactor, cleanup, restructure]
    action: "Load superpowers. Use subagent-driven-development"
  plan:
    patterns: [plan, design, architecture]
    action: "Load superpowers. Use brainstorming"
  [ADD OTHER INTENTS BASED ON INSTALLED SKILLS]
default: "Use available skills based on context"
```

### Step 6: Copy Skills Reference

Copy skill catalog to project:
```bash
cp -r /tmp/claude-bootstrap/skills .claude/
```

### Step 7: Report to User

Tell the user what you installed:

```
Bootstrap Complete ✓

Mandatory Skills Installed:
- gstack (23 specialists)
- superpowers (development workflow)

Optional Skills Installed (Based on Project):
[LIST WHAT YOU INSTALLED]

Plugins to Install After Restart:
- /plugin install superpowers@claude-plugins-official
[LIST OTHER PLUGINS IF NEEDED]

Generated Files:
- .claude/CLAUDE.md
- .claude/settings.json
- .claude/context.md
- .claude/intent-map.yaml
- .claude/skills/ (full catalog)

Next Step: Restart Claude Code to activate.
```

## Skill Selection Guide

Use this to decide what to install:

| If Project Has... | Install |
|-------------------|---------|
| Any code | gstack + superpowers (mandatory) |
| React/Vue/Angular | frontend-design plugin |
| Node + Database | prisma plugin |
| PDF/Word/Excel work | anthropics-skills + document-skills plugin |
| Web scraping | awesome-claude-skills + firecrawl plugin |
| Marketing content | marketing plugin |
| Memory needs | claude-mem (user decides) |
| SaaS integrations | awesome-claude-skills (78+ apps) |

## Reference

- gstack: https://github.com/garrytan/gstack
- superpowers: https://github.com/obra/superpowers
- anthropics: https://github.com/anthropics/skills
- awesome: https://github.com/ComposioHQ/awesome-claude-skills
