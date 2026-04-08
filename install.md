# Claude Bootstrap Installer

Install skills and make them work automatically.

## Skill Installation Patterns

There are 3 types of skills. Each type has a specific install procedure:

### Type 1: GitHub Repo with Setup Script
**Pattern:** Clone → Run setup → Done

**Example:** gstack
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
# Check for setup script
if [ -f .claude/skills/gstack/setup ]; then
  cd .claude/skills/gstack && ./setup
fi
```

**Detection:** Has `setup` file in root (executable script)

---

### Type 2: Plugin with .claude-plugin/
**Pattern:** Clone to global OR use /plugin install

**Example:** superpowers
```bash
# Option A: Clone (project-level)
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers

# Option B: Plugin install (user-level)  
/plugin install superpowers@anthropic-agent-skills
```

**Detection:** Has `.claude-plugin/plugin.json` file

---

### Type 3: Simple Skill (SKILL.md only)
**Pattern:** Clone/copy → No setup needed

**Example:** awesome-claude-skills items
```bash
# Copy individual skill folder
cp -r /tmp/awesome/[skill-name] .claude/skills/
```

**Detection:** Has `SKILL.md` but no `setup` script, no `.claude-plugin/`

---

## Bootstrap Procedure

### Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/`:
- foundation.md
- build.md
- data.md
- create.md
- secure.md
- integrate.md

For each skill, extract:
- Name
- Source (GitHub URL or plugin identifier)
- Type hint (if provided)
- What it provides

### Step 2: Detect Project

Scan project files to determine:
- Language/framework (package.json, requirements.txt, Cargo.toml, etc.)
- Framework (React, Vue, etc.)
- Database (prisma/, migrations/, etc.)
- Testing setup
- GitHub repo (for GitHub automation skills)
- etc.

### Step 3: Categorize Skills

For EACH skill in catalog, determine potential:

**HIGH:** Direct match to project tech
- React project + react-components
- Node project + gstack/superpowers
- GitHub repo + github-automation
- Uses Slack + slack-automation

**MEDIUM:** Adjacent/related
- General debugging skills
- API design for backend projects

**LOW:** Not relevant
- Vue skills for React project
- Database skills when no DB detected

### Step 4: Present Options

Ask user with multi_select:

```
"Select skills to install (grouped by relevance):"

HIGH POTENTIAL (recommended):
[ ] skill-1 (matches your React project)
[ ] skill-2 (matches your Node.js setup)
...

MEDIUM POTENTIAL:
[ ] skill-3 (general debugging)
...

LOW POTENTIAL:
[ ] skill-4 (Vue - not your stack)
...
```

### Step 5: Install Selected Skills

For EACH selected skill:

1. **Determine type by checking source:**
   - Source contains `@` → Plugin (Type 2)
   - Source is GitHub URL → Clone and check for setup (Type 1 or 3)
   - Source is `awesome-claude-skills` → Copy from temp (Type 3)

2. **Execute install based on type:**

   **Type 1 (GitHub with setup):**
   ```bash
   git clone --single-branch --depth 1 [source] .claude/skills/[name]
   cd .claude/skills/[name] && ./setup
   ```

   **Type 2 (Plugin):**
   ```bash
   # Prefer project-level clone
   git clone --single-branch --depth 1 [source] .claude/skills/[name]
   ```

   **Type 3 (Simple/Catalog):**
   ```bash
   # For awesome-claude-skills items
   cp -r /tmp/awesome/[skill-name] .claude/skills/
   
   # For other simple skills
   git clone --single-branch --depth 1 [source] .claude/skills/[name]
   ```

3. **Verify installation:**
   - Check `.claude/skills/[name]/SKILL.md` exists
   - For Type 1: Check setup completed (look for expected files)
   - Log success/failure

### Step 6: Extract Skill Configurations

For EACH installed skill, read configuration:

**From SKILL.md frontmatter:**
```yaml
---
name: skill-name
allowed-tools: Read Write Bash(git *)
hooks:
  SessionStart:
    - type: command
      command: echo "Ready"
---
```

**From .claude-plugin/plugin.json:**
```json
{
  "name": "plugin-name",
  "hooks": { ... }
}
```

**From hooks/hooks.json:**
```json
{
  "hooks": {
    "SessionStart": [...]
  }
}
```

Extract:
- `allowed-tools` → permissions.allow entries
- `hooks` → hooks section
- `paths` → create rules/[skill-name]-paths.md

### Step 7: Generate settings.json

Merge all extracted configs:

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "allow": [
      "Read(.claude/skills/**)",
      "Bash(.claude/skills/**/*.sh)",
      "[from skill-1 allowed-tools]",
      "[from skill-2 allowed-tools]"
    ]
  },
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "echo '[skill-1] Ready'"
      }
    ]
  },
  "_installedSkills": [
    {
      "name": "skill-1",
      "source": "github:user/repo",
      "type": "github-with-setup"
    }
  ]
}
```

### Step 8: Generate Core Files

**CLAUDE.md:**
```markdown
# Installed Skills

## Foundation
- **gstack** — Planning, review, QA, shipping
  - Usage: `/office-hours`, `/review`, `/qa`, `/ship`
  
## Project-Specific
- **[skill-name]** — Description
  - Usage: `/command-name`
```

**context.md:**
```markdown
# Project Context

## Tech Stack
[Detected from files]

## Installed Skills
[List with descriptions]
```

**rules/[skill]-paths.md** (for skills with paths):
```markdown
---
name: skill-paths
paths:
  - "src/**/*.tsx"
---

Auto-load [skill-name] when editing these files.
```

### Step 9: Report

```
Bootstrap Complete ✓

Project: [detected type]

Installed [N] skills:
├── HIGH potential: [list with types]
├── MEDIUM potential: [list]
└── LOW potential: [list]

Generated:
├── .claude/settings.json ([N] permissions, [N] hooks)
├── .claude/CLAUDE.md
├── .claude/context.md
└── .claude/rules/ ([N] path rules)

Next: Restart Claude Code
```

## Important Rules

1. **ALWAYS run setup scripts** for Type 1 skills
2. **ALWAYS verify** skill installed correctly before adding to settings.json
3. **ALWAYS extract** configuration from skill files after install
4. **NEVER skip** verification steps
5. **NEVER assume** - check the actual skill structure
