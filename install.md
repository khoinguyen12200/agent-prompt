# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skills and generate dynamic configuration.

## Your Goal

1. Read available skills from `/tmp/claude-bootstrap/skills/`
2. Detect the project type by scanning files
3. Categorize skills by potential value for THIS project
4. Present to user and install selected
5. Read each installed skill's configuration
6. Generate dynamic settings.json

## Step 1: Read Available Skills

Read all files in `/tmp/claude-bootstrap/skills/`:
- foundation.md
- build.md
- data.md
- create.md
- secure.md
- integrate.md

Extract each skill's:
- Name
- Source URL (GitHub repo or plugin identifier)
- Description
- What it provides (commands, hooks, paths, etc.)

## Step 2: Detect Project Type

Scan the project to understand:
- Language/framework (React, Vue, Node, Python, Go, Rust, etc.)
- Database (Prisma, Postgres, Mongo, etc.)
- Testing setup (Jest, Playwright, Pytest, etc.)
- Other patterns (API routes, components, etc.)

## Step 3: Categorize by Potential

Based on project detection, categorize ALL available skills into:

### High Potential
Skills that directly match the project's tech stack and would provide immediate value.

Examples of matching logic:
- React project + react-components skill = High
- Node project + gstack/superpowers = High  
- Any project + foundation skills = High
- Project with GitHub + github-automation = High

### Medium Potential
Skills that could be useful but aren't core to the tech stack, or skills for adjacent workflows.

Examples:
- React project + general debugging skills
- Node backend + API design skills
- Project with testing + advanced testing skills

### Low Potential
Skills that don't match the tech stack or are for completely different use cases.

Examples:
- Frontend-only project + backend database skills
- No Slack integration needed + slack-automation

## Step 4: Present to User

Use AskUserQuestion to let user select skills:

**Question 1:** Select installation approach
- "Recommended: Install High Potential skills only"
- "Balanced: Install High + Medium Potential skills"
- "Manual: I want to choose individually"

**Question 2** (only if Manual): Show skills grouped by potential with multi_select
- High Potential (pre-selected)
- Medium Potential  
- Low Potential

## Step 5: Install Selected Skills

For each selected skill:

1. Determine install method from the skill's source:
   - GitHub repo → `git clone [source] .claude/skills/[name]`
   - Plugin → `/plugin install [identifier]`
   - Awesome catalog → Copy from `/tmp/awesome/`

2. Run any post-install commands if mentioned in skill docs

3. Verify installation succeeded

## Step 6: Extract Skill Configurations

For EACH installed skill, read its files to extract configuration:

Check in order:
1. `SKILL.md` frontmatter (YAML between `---`)
2. `.claude-plugin/plugin.json` (if exists)
3. `hooks/hooks.json` (if exists)

Extract:
- `hooks` → Add to settings.json hooks section
- `allowed-tools` → Convert to permissions.allow rules
- `paths` → Create path-scoped rules in rules/
- `env` → Add to settings.json env section

## Step 7: Generate settings.json

Create `.claude/settings.json` by merging ALL extracted configurations:

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "allow": [
      "Read(.claude/skills/**)",
      "[merged from all installed skills]"
    ]
  },
  "hooks": {
    "[merged from all installed skills]"
  },
  "env": {
    "[merged from all installed skills]"
  }
}
```

Merge rules:
- permissions.allow: Concatenate all, deduplicate
- hooks: Concatenate all arrays by event type
- env: Merge objects, use skill name prefix if conflicts

## Step 8: Generate Core Files

### CLAUDE.md
- List all installed skills with descriptions
- Show how to invoke each skill

### context.md
- Project tech stack summary
- Installed skills reference

### rules/
- For each skill with `paths:` in frontmatter, create a path-scoped rule

## Step 9: Report

Show user what was done:

```
Bootstrap Complete ✓

Project Detected: [type]

Skills Installed: [N]
├── High Potential: [list]
├── Medium Potential: [list]
└── Low Potential: [list]

Configuration Generated:
├── .claude/settings.json
│   ├── permissions: [N] rules
│   ├── hooks: [N] hooks
│   └── env: [N] variables
├── .claude/CLAUDE.md
├── .claude/context.md
└── .claude/rules/ ([N] path-scoped rules)

Next: Restart Claude Code
```

## Key Principles

- **No hardcoded install commands** — Read from skill docs
- **Project-aware** — Match skills to actual project needs
- **Dynamic config** — Extract from skill files after install
- **User choice** — Present options, don't decide unilaterally
