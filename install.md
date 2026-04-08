# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read All Skills

Read every file in `/tmp/claude-bootstrap/skills/`:
- `skills/gstack.md`
- `skills/superpowers.md`
- `skills/memory.md`
- `skills/frontend.md`
- `skills/database.md`
- `skills/documents.md`
- `skills/scraping.md`
- `skills/marketing.md`
- `skills/automation.md`
- `skills/development.md`
- `skills/security.md`
- `skills/data.md`
- `skills/creative.md`
- `skills/productivity.md`

## Step 2: Detect Project

Scan the current project directory:
- List all directories and subdirectories
- Identify file extensions and patterns
- Check for config files (package.json, requirements.txt, etc.)
- Note any existing .claude/ configuration

## Step 3: Install Mandatory Skills

Install these three skills (marked MANDATORY in their files):

1. **gstack** - Clone and setup
2. **superpowers** - Clone to project (use git clone, not plugin install)
3. **claude-mem** - Follow install instructions in memory.md

## Step 4: Install Optional Skills

For each remaining skills file, decide if project needs it:

- Read the "When to Install" or criteria in each file
- Compare against detected project structure
- If match found → install it
- If no match → skip it

**Decision criteria:**
- frontend.md → React/Vue/Angular files detected?
- database.md → Database/ORM usage detected?
- documents.md → PDF/Word/Excel handling needed?
- scraping.md → Web scraping requirements?
- marketing.md → Marketing content work?
- automation.md → SaaS integrations needed?
- development.md → Additional dev tools needed?
- security.md → Security testing requirements?
- data.md → Data analysis/research work?
- creative.md → Images/video/design work?
- productivity.md → File management/workspace needs?

## Step 5: Generate Rules

Analyze project and create `.claude/rules/` files:

1. Scan codebase for patterns
2. Identify: frontend, backend, database, testing, config, docs
3. For each clear pattern found:
   - Create `{category}.md` in `.claude/rules/`
   - Add YAML frontmatter with `name:` and `paths:`
   - Document actual conventions from code
   - Keep under 30 lines

## Step 6: Generate Core Files

Create in `.claude/`:

**CLAUDE.md:**
- List all installed skills (mandatory + optional)
- Intent → skill mapping
- Principles section

**settings.json:**
```json
{
  "hooks": {
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
- Project name/type
- Technology stack detected
- Key directories
- Conventions observed

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
  [ADD MAPPINGS FOR INSTALLED OPTIONAL SKILLS]
default: "Use available skills based on context"
```

## Step 7: Copy Skills Reference

```bash
mkdir -p .claude/bootstrap-catalog
cp -r /tmp/claude-bootstrap/skills .claude/bootstrap-catalog/
```

## Step 8: Report

Tell user exactly what was installed:

```
Bootstrap Complete ✓

Mandatory Skills Installed:
- gstack (23 specialists)
- superpowers (12 workflow skills)
- claude-mem (memory)

Optional Skills Installed (Based on Project Detection):
[List each with reason why it was selected]

Generated Files:
- .claude/CLAUDE.md
- .claude/settings.json
- .claude/context.md
- .claude/intent-map.yaml
- .claude/rules/ [if any created]
- .claude/bootstrap-catalog/skills/

Next Step: Restart Claude Code to activate.
```
