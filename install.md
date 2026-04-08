# Claude Bootstrap Installer

Install skills correctly so they are discoverable and invocable.

## How Skills Work

Skills are discovered from `.claude/skills/<name>/SKILL.md`. User invokes them by typing `/<skill-name>`.

**For skills to work:**
1. `SKILL.md` must exist at `.claude/skills/<name>/SKILL.md`
2. Skill name matches directory name (or `name:` in frontmatter)
3. User types `/<skill-name>` to invoke

## Skill Installation

### Type A: Multi-Skill Repository (gstack)

**Structure:** One repo with multiple skill subdirectories

**Example:** gstack has 23 skills (office-hours/, review/, qa/, ship/, etc.)

**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack

# Run setup if bun available
if command -v bun >/dev/null 2>&1; then
  cd .claude/skills/gstack && ./setup
fi

# Link sub-skills (CRITICAL - Claude only looks 1 level deep)
for dir in .claude/skills/gstack/*/; do
  if [ -f "$dir/SKILL.md" ]; then
    name=$(basename "$dir")
    case "$name" in bin|lib|scripts|node_modules|.git) continue ;; esac
    mkdir -p ".claude/skills/$name"
    ln -sf "$(pwd)/.claude/skills/gstack/$name/SKILL.md" ".claude/skills/$name/SKILL.md"
  fi
done
```

**Verify:**
```bash
ls .claude/skills/office-hours/SKILL.md
ls .claude/skills/review/SKILL.md
ls .claude/skills/qa/SKILL.md
```

---

### Type B: Plugin with Sub-skills (superpowers)

**Structure:** Skills in `skills/` subdirectory

**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers

# Link sub-skills
for dir in .claude/skills/superpowers/skills/*/; do
  if [ -f "$dir/SKILL.md" ]; then
    name=$(basename "$dir")
    mkdir -p ".claude/skills/$name"
    ln -sf "$(pwd)/.claude/skills/superpowers/skills/$name/SKILL.md" ".claude/skills/$name/SKILL.md"
  fi
done
```

**Verify:**
```bash
ls .claude/skills/systematic-debugging/SKILL.md
ls .claude/skills/test-driven-development/SKILL.md
```

---

### Type C: Simple Skill (awesome-claude-skills)

**Structure:** Single SKILL.md at root

**Install:**
```bash
# Ensure catalog exists
if [ ! -d /tmp/awesome ]; then
  git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
fi

# Copy skill
cp -r /tmp/awesome/[skill-name] .claude/skills/
```

**Verify:**
```bash
ls .claude/skills/[skill-name]/SKILL.md
```

---

### Type D: Plugin (claude-mem)

**Install:**
```bash
/plugin install claude-mem@thedotmack
```

---

## Bootstrap Procedure

### Step 1: Read Catalog

Read `/tmp/claude-bootstrap/skills/*.md` to understand available skills.

### Step 2: Detect Project

Scan for:
- package.json, requirements.txt, Cargo.toml, go.mod
- src/**/*.tsx (React), src/**/*.vue (Vue)
- prisma/ (database)
- .github/ (uses GitHub)

### Step 3: Categorize Skills

**HIGH:** Foundation skills (gstack, superpowers, claude-mem) + tech matches
**MEDIUM:** General utilities
**LOW:** Wrong tech stack

### Step 4: User Selects

Present skills grouped by potential with multi_select.

### Step 5: Install Each Skill

For each selected skill:

1. **Determine type** from skill info
2. **Execute correct install** (Type A/B/C/D)
3. **Verify SKILL.md exists** at `.claude/skills/<name>/SKILL.md`
4. **Note failures** and continue

### Step 6: Generate CLAUDE.md

Create skill reference:

```markdown
# Installed Skills

## Foundation

### /office-hours
Source: gstack | 23 specialists total
Product planning and brainstorming

### /review
Source: gstack
Code review before landing changes

### /qa
Source: gstack
Browser testing and verification

### /ship
Source: gstack
Release workflow

### /cso
Source: gstack
Security audit (OWASP + STRIDE)

### /browse
Source: gstack
Browser automation

### /systematic-debugging
Source: superpowers | 12 workflows total
4-phase debugging methodology

### /test-driven-development
Source: superpowers
TDD workflow

### /subagent-driven-development
Source: superpowers
Parallel agent tasks

### /mem
Source: claude-mem
Memory persistence

## Usage

Type `/` to see all skills.
Type `/<skill-name>` to invoke.
```

### Step 7: Report

```
Bootstrap Complete ✓

Installed [N] skills:
├── gstack (23 sub-skills linked)
│   ├── /office-hours ✓
│   ├── /review ✓
│   ├── /qa ✓
│   ├── /ship ✓
│   ├── /cso ✓
│   ├── /browse ✓
│   └── 17 more...
├── superpowers (12 sub-skills linked)
│   ├── /systematic-debugging ✓
│   ├── /test-driven-development ✓
│   └── 10 more...
├── claude-mem ✓
└── [others...]

Generated:
└── .claude/CLAUDE.md (skill reference)

Next:
1. Restart Claude Code
2. Type `/` to see skills
3. Try `/office-hours` or `/review`
```

## Common Issues

**Skill not found with `/name`:**
- Check: `ls .claude/skills/<name>/SKILL.md`
- Fix: Sub-skills not linked properly

**gstack shows only `/gstack`:**
- Run linking step to expose sub-skills

**superpowers skills missing:**
- Link from `superpowers/skills/` to `.claude/skills/`
