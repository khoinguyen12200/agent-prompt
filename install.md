# Claude Bootstrap Installer

Install skills so they are discoverable, invocable, and auto-load correctly.

## Critical Requirements

For a skill to work, ALL of these must be true:

1. **Location**: `.claude/skills/<skill-name>/SKILL.md` must exist
2. **Name**: The skill name matches the directory name (or `name:` in frontmatter)
3. **Discovery**: Claude Code scans `.claude/skills/` at startup
4. **Invocation**: User types `/<skill-name>` OR description matches prompt
5. **Permissions**: Skill has necessary tool permissions

## How Skills Auto-Load

Skills become available when:

**Manual invocation:**
- User types `/<skill-name>`
- Skill loads immediately

**Auto-invocation (model decides):**
- Skill's `description` matches user's prompt
- Claude loads the skill automatically
- Example: "review my code" → loads `/review` skill

**Path-based auto-load:**
- Skill has `paths:` in frontmatter
- User edits a file matching those paths
- Skill loads automatically

## Skill Installation by Type

### Type A: Multi-Skill Repository (gstack)

**Structure:** One repo contains multiple skill subdirectories

**Example:** gstack has 23 skills in subdirectories:
```
gstack/
├── office-hours/SKILL.md
├── review/SKILL.md
├── qa/SKILL.md
├── ship/SKILL.md
└── ... (19 more)
```

**Installation Steps:**

1. **Clone to correct location:**
   ```
   git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
   ```

2. **Run setup if prerequisites exist:**
   - Check for bun: `command -v bun`
   - If bun exists: `cd .claude/skills/gstack && ./setup`
   - If bun missing: Note that browser features won't work, but continue

3. **CRITICAL: Link sub-skills for discovery:**
   
   Claude Code only looks one level deep. Each sub-skill needs to be at `.claude/skills/<name>/SKILL.md`.
   
   Use gstack's built-in relinker:
   ```
   cd .claude/skills/gstack && ./bin/gstack-relink
   ```
   
   OR manually create directories and symlinks:
   ```
   cd .claude/skills
   for dir in gstack/*/; do
     if [ -f "$dir/SKILL.md" ]; then
       name=$(basename "$dir")
       # Skip non-skill directories
       case "$name" in bin|lib|scripts|node_modules|.git) continue ;; esac
       mkdir -p "$name"
       ln -sf "$(pwd)/gstack/$name/SKILL.md" "$name/SKILL.md"
     fi
   done
   ```

4. **Verify all skills are discoverable:**
   ```
   ls .claude/skills/*/SKILL.md | wc -l  # Should show ~23 for gstack
   ls .claude/skills/office-hours/SKILL.md  # Should exist
   ls .claude/skills/review/SKILL.md        # Should exist
   ls .claude/skills/qa/SKILL.md            # Should exist
   ```

5. **Extract configurations from each sub-skill:**
   - Read each `SKILL.md` frontmatter
   - Collect `allowed-tools`, `hooks`, `paths`
   - Note: Each sub-skill may have different permissions

**Post-Install State:**
```
.claude/skills/
├── gstack/                    # Main repo
│   ├── office-hours/SKILL.md
│   ├── review/SKILL.md
│   └── ...
├── office-hours/              # LINKED
│   └── SKILL.md → gstack/office-hours/SKILL.md
├── review/                    # LINKED
│   └── SKILL.md → gstack/review/SKILL.md
├── qa/                        # LINKED
│   └── SKILL.md → gstack/qa/SKILL.md
└── ... (20 more linked skills)
```

---

### Type B: Plugin with .claude-plugin/ (superpowers)

**Structure:** Plugin manifest + skills in subdirectory

**Example:** superpowers has skills in `skills/` subdirectory

**Installation Steps:**

1. **Clone to correct location:**
   ```
   git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers
   ```

2. **Check structure:**
   ```
   ls .claude/skills/superpowers/skills/  # Should show subdirectories
   ```

3. **CRITICAL: Link sub-skills OR copy them:**
   
   Option A - Link (preferred):
   ```
   cd .claude/skills
   for dir in superpowers/skills/*/; do
     if [ -f "$dir/SKILL.md" ]; then
       name=$(basename "$dir")
       mkdir -p "$name"
       ln -sf "$(pwd)/superpowers/skills/$name/SKILL.md" "$name/SKILL.md"
     fi
   done
   ```
   
   Option B - Copy (if linking doesn't work):
   ```
   cd .claude/skills
   for dir in superpowers/skills/*/; do
     if [ -f "$dir/SKILL.md" ]; then
       name=$(basename "$dir")
       cp -r "$dir" "$name"
     fi
   done
   ```

4. **Verify all skills:**
   ```
   ls .claude/skills/systematic-debugging/SKILL.md
   ls .claude/skills/test-driven-development/SKILL.md
   ```

5. **Extract configurations:**
   - Each sub-skill has its own `SKILL.md` with frontmatter
   - Read and merge all configurations

---

### Type C: Simple Skill (awesome-claude-skills)

**Structure:** Single `SKILL.md` at root

**Installation Steps:**

1. **Clone catalog (once):**
   ```
   git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
   ```

2. **Copy selected skills (NOT the whole catalog):**
   ```
   cp -r /tmp/awesome/[skill-name] .claude/skills/
   ```

3. **Verify:**
   ```
   ls .claude/skills/[skill-name]/SKILL.md  # Should exist
   ```

4. **Extract frontmatter:**
   - Read `SKILL.md` for `allowed-tools`, `hooks`, `paths`

---

### Type D: Plugin via Marketplace (claude-mem)

**Installation:**
```
/plugin install claude-mem@thedotmack
```

**Note:** This installs to user-level, not project-level. Skills should still be available.

---

## Complete Bootstrap Procedure

### Step 1: Read Skill Catalog

Read all catalog files in `/tmp/claude-bootstrap/skills/`:
- foundation.md
- build.md
- data.md
- create.md
- secure.md
- integrate.md

For each skill, note:
- Type (multi-skill repo, simple skill, plugin)
- Source URL
- Prerequisites
- What skills/commands it provides

### Step 2: Detect Project

Scan for:
- `package.json` → Node.js project
- `requirements.txt` / `pyproject.toml` → Python project
- `Cargo.toml` → Rust project
- `go.mod` → Go project
- `src/**/*.tsx` → React
- `src/**/*.vue` → Vue
- `prisma/` → Prisma/Database
- `.github/workflows/` → Uses GitHub

### Step 3: Categorize Skills

**HIGH Potential:**
- gstack (any project)
- superpowers (any project)
- claude-mem (any project)
- React + react-components
- Node + api-design
- GitHub repo + github-automation
- Uses Slack + slack-automation

**MEDIUM Potential:**
- Debugging skills
- Testing skills

**LOW Potential:**
- Wrong framework
- Wrong domain

### Step 4: User Selection

Present with multi_select:
```
"Select skills to install (grouped by relevance):"

HIGH POTENTIAL:
[ ] gstack - 23 specialists (HIGHLY RECOMMENDED)
[ ] superpowers - 12 workflows (HIGHLY RECOMMENDED)
[ ] claude-mem - Memory (HIGHLY RECOMMENDED)
[ ] [matching skills...]

MEDIUM POTENTIAL:
[ ] [debugging skills...]

LOW POTENTIAL:
[ ] [non-matching skills...]
```

### Step 5: Install Each Skill

For EACH selected skill:

**Determine type and install:**
- Multi-skill repo (gstack, superpowers) → Follow Type A/B steps
- Simple skill (awesome) → Follow Type C steps
- Plugin → Follow Type D steps

**Link sub-skills:**
- MUST create individual directories for each sub-skill
- MUST have SKILL.md accessible at `.claude/skills/<name>/SKILL.md`

**Run setup if applicable:**
- Check prerequisites first
- Run setup script if present
- Continue even if setup partially fails

### Step 6: Verify Installation

**CRITICAL VERIFICATION STEPS:**

1. **Count installed skills:**
   ```
   ls .claude/skills/*/SKILL.md | wc -l
   ```

2. **Verify key skills exist:**
   ```
   ls .claude/skills/office-hours/SKILL.md  # gstack
   ls .claude/skills/review/SKILL.md        # gstack
   ls .claude/skills/systematic-debugging/SKILL.md  # superpowers
   ```

3. **Check SKILL.md content:**
   - Has valid frontmatter (starts with `---`)
   - Has `description:` field
   - Has skill instructions

4. **Note any failures:**
   - Missing prerequisites
   - Failed setup steps
   - Missing sub-skills

### Step 7: Extract Configurations

For EACH installed skill, read `SKILL.md` and extract:

**Frontmatter fields:**
```yaml
---
name: skill-name
description: What this skill does
allowed-tools: Read Write Bash(git *)
hooks:
  SessionStart:
    - type: command
      command: echo "Ready"
paths:
  - "src/**/*.tsx"
---
```

**Extract:**
- `allowed-tools` → permissions.allow entries
- `hooks` → hooks configuration
- `paths` → create path-scoped rules

### Step 8: Generate settings.json

Create valid `.claude/settings.json`:

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "allow": [
      "Read(.claude/skills/**)",
      "Bash(.claude/skills/**/*.sh)",
      "[all extracted allowed-tools from skills]"
    ]
  },
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "echo '[Bootstrap] Skills loaded: [list]'"
      }
    ]
  },
  "_installedSkills": [
    {
      "name": "office-hours",
      "source": "gstack",
      "type": "sub-skill"
    },
    {
      "name": "review",
      "source": "gstack",
      "type": "sub-skill"
    }
  ]
}
```

### Step 9: Generate CLAUDE.md

Create comprehensive skill reference:

```markdown
# Installed Skills

## Foundation Skills

### /office-hours
Source: gstack
Description: Product planning and brainstorming
When to use: When you have a new product idea or want to think through design decisions

### /review
Source: gstack
Description: Code review before landing changes
When to use: Before merging PRs or landing code

### /qa
Source: gstack
Description: Browser testing and verification
When to use: To test a deployment or verify a user flow

### /systematic-debugging
Source: superpowers
Description: 4-phase debugging methodology
When to use: When you encounter a bug or test failure

## Project-Specific Skills

[List other installed skills with usage]

## How to Use

1. Type `/` to see all available skills
2. Type `/<skill-name>` to invoke a specific skill
3. Or describe what you want: "review my code" will auto-load /review
```

### Step 10: Generate Path-Based Rules

For skills with `paths:` in frontmatter, create rules:

`.claude/rules/react-skills.md`:
```markdown
---
name: react-auto-load
paths:
  - "src/**/*.tsx"
  - "src/**/*.jsx"
---

Auto-load react-components skill when editing React files.
```

### Step 11: Final Verification

**Test that skills work:**

1. **Check skill discovery:**
   - List all skill directories: `ls .claude/skills/`
   - Count SKILL.md files: `ls .claude/skills/*/SKILL.md | wc -l`

2. **Verify gstack specifically:**
   - Check all 23 sub-skills are linked: `ls .claude/skills/office-hours/ && ls .claude/skills/review/`

3. **Verify superpowers:**
   - Check 12 skills are linked: `ls .claude/skills/systematic-debugging/`

4. **Validate settings.json:**
   - Must be valid JSON
   - Must have `$schema`
   - Permissions must be array of strings

### Step 12: Report to User

```
Bootstrap Complete ✓

Installation Summary:
├── Total skills installed: [N]
├── Foundation:
│   ├── gstack ✓ (23 sub-skills linked)
│   │   ├── /office-hours
│   │   ├── /review
│   │   ├── /qa
│   │   ├── /ship
│   │   └── 19 more...
│   ├── superpowers ✓ (12 sub-skills linked)
│   │   ├── /systematic-debugging
│   │   ├── /test-driven-development
│   │   └── 10 more...
│   └── claude-mem ✓
└── Project-specific: [list]

Configuration:
├── .claude/settings.json ([N] permissions, [N] hooks)
├── .claude/CLAUDE.md (skill reference)
├── .claude/context.md (project info)
└── .claude/rules/ ([N] path-based rules)

Verification:
├── All skills discoverable: ✓
├── All sub-skills linked: ✓
├── Settings valid: ✓
└── Ready to use: ✓

Next Steps:
1. Restart Claude Code
2. Type `/` to see available skills
3. Try `/office-hours` or `/review`

Notes:
- [Any warnings about missing prerequisites]
- [Any partial installations explained]
```

## Common Failures and Fixes

**"Skill not found" when typing `/name`:**
- Check: `ls .claude/skills/<name>/SKILL.md` exists
- Fix: Link sub-skill directory properly

**gstack only shows `/gstack`, not sub-skills:**
- Cause: Sub-skills not linked
- Fix: Run gstack-relink or manually link each sub-skill

**superpowers skills not showing:**
- Cause: Skills buried in `skills/` subdirectory
- Fix: Link or copy from `superpowers/skills/` to `.claude/skills/`

**Settings.json rejected:**
- Check JSON is valid
- Check permissions entries are strings
- Check hooks structure matches schema

## Validation Checklist

Before reporting success, verify:

- [ ] All selected skills installed
- [ ] Multi-skill repos have sub-skills linked
- [ ] Each skill has SKILL.md in expected location
- [ ] settings.json is valid and has $schema
- [ ] CLAUDE.md explains how to use skills
- [ ] User knows to type `/<skill-name>` to invoke
- [ ] Any failures are documented in report
