# Claude Bootstrap Installer

Install skills correctly so they actually work.

## How Skills Work in Claude Code

Skills are discovered from `.claude/skills/<name>/SKILL.md`. They are invoked by typing `/<name>`.

Skills do NOT auto-load just by being present. They must be:
1. Manually invoked: `/skill-name`
2. Auto-invoked by Claude when description matches the prompt
3. Referenced in CLAUDE.md so user knows they exist

## Skill Types and Install Methods

### Type A: GitHub Repo with Setup Script (gstack)

**Prerequisites:**
- bun (required for setup)
- Playwright dependencies (for browser features)

**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack

# Try to run setup, but continue even if browser setup fails
cd .claude/skills/gstack && ./setup 2>&1 || true

# CRITICAL: Link sub-skills so they're discoverable
# This creates symlinks like .claude/skills/office-hours -> gstack/office-hours/SKILL.md
if [ -f .claude/skills/gstack/bin/gstack-relink ]; then
  cd ../.. && GSTACK_SKILLS_DIR="$(pwd)/.claude/skills" GSTACK_INSTALL_DIR="$(pwd)/.claude/skills/gstack" ./.claude/skills/gstack/bin/gstack-relink
fi
```

**What gstack provides:**
- `/gstack` - Main browser automation skill
- `/office-hours` - Product planning
- `/review` - Code review
- `/qa` - Browser testing
- `/ship` - Release workflow
- `/cso` - Security audit
- Plus 17 more sub-skills

**If setup fails:** The skills can still work for non-browser features if you manually link them using gstack-relink.

---

### Type B: Plugin (superpowers, claude-mem)

**Install:**
```bash
# For superpowers
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers

# For claude-mem (plugin)
/plugin install claude-mem@thedotmack
```

**What superpowers provides:**
Skills in `skills/` subdirectory. Claude Code should discover them automatically if the directory structure is correct.

---

### Type C: Simple Skill (awesome-claude-skills)

**Install:**
```bash
# Clone catalog to temp (one time)
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy individual skill
# CRITICAL: Must be directly in .claude/skills/, not nested
cp -r /tmp/awesome/[skill-name] .claude/skills/
```

**Result:** `.claude/skills/[skill-name]/SKILL.md` is ready to use.

---

## Bootstrap Procedure

### Step 1: Read Skill Catalog

Read all files in `/tmp/claude-bootstrap/skills/`. For each skill extract:
- Name
- Source URL or identifier
- Type (A, B, or C)
- Prerequisites (bun, playwright, etc.)
- What it provides (commands list)

### Step 2: Detect Project

Scan for:
- package.json, requirements.txt, Cargo.toml, go.mod
- Framework patterns (React, Vue, etc.)
- Database patterns (prisma/, migrations/)
- CI/CD configs (GitHub Actions, etc.)

### Step 3: Categorize by Potential

**HIGH:** Direct match to detected tech
- Any project + gstack, superpowers, claude-mem
- React project + react-components
- Node project + api-design
- GitHub repo + github-automation

**MEDIUM:** Related/utility
- General debugging skills
- Testing skills

**LOW:** Not relevant
- Vue skills for React project
- Database skills when no DB

### Step 4: Present to User

```
"Select skills to install:"

HIGH POTENTIAL:
[ ] gstack (23 specialists - highly recommended)
[ ] superpowers (12 workflow skills - highly recommended)
[ ] claude-mem (memory - highly recommended)
[ ] [other matching skills...]

MEDIUM POTENTIAL:
[ ] [utility skills...]

LOW POTENTIAL:
[ ] [non-matching skills...]
```

### Step 5: Install Selected Skills

For each selected skill:

**Type A (gstack):**
1. Check if bun is installed: `command -v bun`
2. Clone the repo
3. Try to run `./setup` (continue even if browser setup fails)
4. **CRITICAL:** Run `gstack-relink` to create skill symlinks
5. Verify skills are linked: `ls .claude/skills/ | grep -E "office-hours|review|qa"`

**Type B (superpowers):**
1. Clone the repo
2. Verify `.claude/skills/superpowers/skills/` exists
3. Each subdirectory should have SKILL.md

**Type C (awesome-claude-skills):**
1. Ensure `/tmp/awesome` exists (clone if not)
2. Copy specific skill: `cp -r /tmp/awesome/[name] .claude/skills/`
3. Verify `.claude/skills/[name]/SKILL.md` exists

### Step 6: Verify Installation

For each installed skill, verify it's discoverable:

```bash
# List all discoverable skills
ls .claude/skills/*/SKILL.md 2>/dev/null | xargs -I{} dirname {} | xargs -I{} basename {}
```

If gstack skills are missing, manually link them:
```bash
cd .claude/skills
for dir in gstack/*/; do
  if [ -f "$dir/SKILL.md" ]; then
    name=$(basename "$dir")
    case "$name" in bin|browse|lib|node_modules|scripts|test|.git) continue ;; esac
    mkdir -p "$name"
    ln -sf "$(pwd)/gstack/$name/SKILL.md" "$name/SKILL.md"
  fi
done
```

### Step 7: Extract Configurations

Read each skill's SKILL.md frontmatter:
- `allowed-tools:` → Add to permissions.allow
- `hooks:` → Add to settings.json hooks
- `paths:` → Create path-scoped rules

### Step 8: Generate settings.json

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "allow": [
      "Read(.claude/skills/**)",
      "Bash(.claude/skills/**/*.sh)",
      "[from skill allowed-tools]"
    ]
  },
  "hooks": {
    "SessionStart": [
      {
        "type": "command",
        "command": "echo '[Bootstrap] Loaded: gstack, superpowers, etc'"
      }
    ]
  },
  "_installedSkills": [
    {"name": "gstack", "commands": ["/office-hours", "/review", "/qa", "/ship"]},
    {"name": "superpowers", "commands": ["/systematic-debugging", "/tdd"]}
  ]
}
```

### Step 9: Generate CLAUDE.md

**CRITICAL:** This file tells the user HOW to use the installed skills.

```markdown
# Installed Skills

## Foundation (Always Available)

### gstack — 23 Specialists
Use by typing the command:
- `/office-hours` — Product planning and brainstorming
- `/review` — Code review before landing
- `/qa` — Browser testing and verification
- `/ship` — Release workflow
- `/cso` — Security audit
- `/browse` — Browser automation
- Plus 17 more: `/plan-ceo-review`, `/plan-eng-review`, `/retro`, `/learn`, ...

**Note:** Browser features require Playwright. If not installed, non-browser features still work.

### superpowers — 12 Workflow Skills
- `/systematic-debugging` — Debug issues methodically
- `/test-driven-development` — TDD workflow
- `/subagent-driven-development` — Parallel agent tasks
- Plus 9 more...

### claude-mem — Memory
- `/mem` — Recall previous context

## Project-Specific Skills
[List other installed skills with their invoke commands]

## How to Use
1. Type `/` to see all available skills
2. Type `/skill-name` to invoke a specific skill
3. Or mention it: "Using /review, check this PR"
```

### Step 10: Report

```
Bootstrap Complete ✓

Installed Skills:
├── gstack ✓
│   ├── Main skill: /gstack
│   └── Sub-skills: /office-hours, /review, /qa, /ship, /cso, /browse (17 more)
│   └── Note: Run with bun available for full browser features
├── superpowers ✓
│   └── Skills: /systematic-debugging, /tdd, /subagent-development (9 more)
├── claude-mem ✓
│   └── Command: /mem
└── [others...]

Generated:
├── .claude/settings.json
├── .claude/CLAUDE.md (reference for how to use skills)
├── .claude/context.md
└── .claude/rules/

Next Steps:
1. Restart Claude Code
2. Type `/` to see available skills
3. Try `/office-hours` or `/review`
```

## Important Checks

1. **ALWAYS verify sub-skills are linked** (gstack creates 23 skills, not just 1)
2. **ALWAYS generate CLAUDE.md** explaining how to invoke skills
3. **ALWAYS check prerequisites** (bun for gstack)
4. **Skills don't auto-load** - user must type `/<command>`

## Troubleshooting

**Skill not found when typing `/name`:**
- Check skill is in `.claude/skills/<name>/SKILL.md`
- For gstack: Check sub-skills are linked (not nested only under gstack/)
- Restart Claude Code

**gstack browser features don't work:**
- Install Playwright: `npx playwright install chromium`
- Or use non-browser features (work without browser)

**superpowers skills not showing:**
- Check `.claude/skills/superpowers/skills/` exists
- Each subdirectory should have SKILL.md
