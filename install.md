# Claude Bootstrap Installer

Install skills correctly so they are discoverable and invocable.

## How Skills Work

Claude Code discovers skills from `.claude/skills/<name>/SKILL.md`. User invokes by typing `/<skill-name>`.

**Requirement:** Each skill must have `SKILL.md` at `.claude/skills/<name>/SKILL.md`

## Universal Installation Method

This method works for ALL skill types:

```bash
# Step 1: Install skill source to .claude/skills/
# (git clone for repos, cp -r for catalog items, /plugin install for plugins)

# Step 2: Discover and link ALL sub-skills
# For each subdirectory with SKILL.md, ensure it's accessible at top level

for skill_dir in .claude/skills/*/; do
  [ -d "$skill_dir" ] || continue
  
  # Check if this directory has SKILL.md (it's a skill)
  if [ -f "$skill_dir/SKILL.md" ]; then
    name=$(basename "$skill_dir")
    
    # Skip non-skill directories (bin, lib, scripts, etc.)
    case "$name" in
      bin|lib|scripts|node_modules|.git|.github|docs|test|tests|dist|build|contrib|agents)
        continue
        ;;
    esac
    
    # Skill is already at top level - verify it works
    echo "Skill found: $name"
  fi
  
  # Check for nested skills (superpowers/skills/, etc.)
  for nested in "$skill_dir"/*/; do
    [ -d "$nested" ] || continue
    
    if [ -f "$nested/SKILL.md" ]; then
      nested_name=$(basename "$nested")
      
      # Skip common non-skill directories
      case "$nested_name" in
        bin|lib|scripts|node_modules|.git|.github|docs|test|tests|dist|build)
          continue
          ;;
      esac
      
      # Link nested skill to top level
      mkdir -p ".claude/skills/$nested_name"
      ln -sf "$(pwd)/.claude/skills/$(basename "$skill_dir")/$nested_name/SKILL.md" \
             ".claude/skills/$nested_name/SKILL.md"
      
      echo "Linked sub-skill: $nested_name"
    fi
  done
done
```

## Installation by Source

### GitHub Repositories

```bash
# Clone to .claude/skills/
git clone --single-branch --depth 1 <repo-url> .claude/skills/<repo-name>

# Run setup if exists
if [ -f .claude/skills/<repo-name>/setup ]; then
  (cd .claude/skills/<repo-name> && ./setup) || true
fi

# Link all sub-skills (use universal method above)
```

### Awesome Claude Skills (Catalog)

```bash
# Clone catalog once to temp
if [ ! -d /tmp/awesome ]; then
  git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
fi

# Copy selected skill
cp -r /tmp/awesome/<skill-name> .claude/skills/
```

### Plugins

```bash
/plugin install <plugin-id>
```

## Complete Bootstrap Procedure

### Step 1: Read Catalog

Read `/tmp/claude-bootstrap/skills/*.md` for available skills.

### Step 2: Detect Project

Scan for tech stack indicators (package.json, requirements.txt, src/**/*.tsx, etc.)

### Step 3: Categorize Skills

| Potential | Criteria |
|-----------|----------|
| **HIGH** | Direct match to detected tech stack |
| **MEDIUM** | Related utilities |
| **LOW** | General purpose (superpowers), wrong tech |

### Step 4: User Selection

Present skills grouped by potential with multi_select.

### Step 5: Install Skills

For EACH selected skill:

1. **Clone/copy source** to `.claude/skills/`
2. **Run setup** if present (continue on failure)
3. **Link sub-skills** using universal method
4. **Verify** each skill has `SKILL.md` at top level

### Step 6: Verify Installation

```bash
# Count total skills installed
echo "Total skills: $(ls .claude/skills/*/SKILL.md 2>/dev/null | wc -l)"

# List all installed skills
for skill_md in .claude/skills/*/SKILL.md; do
  [ -f "$skill_md" ] && echo "✓ $(basename $(dirname $skill_md))"
done
```

### Step 7: Generate CLAUDE.md

```markdown
# Installed Skills

## Usage

Type `/` to see all skills. Type `/<skill-name>` to invoke.

## Installed Skills

[List each installed skill with description]
```

### Step 8: Report

```
Bootstrap Complete ✓

Installed Skills: [N] total
├── [skill-1]: [count] sub-skills ✓
├── [skill-2]: [count] sub-skills ✓
└── ...

Verify: ls .claude/skills/*/SKILL.md

Next:
1. Restart Claude Code
2. Type `/` to see all skills
3. Type `/<skill>` to use
```

## Troubleshooting

**Skill not found:**
```bash
# Check if SKILL.md exists
ls .claude/skills/<skill-name>/SKILL.md

# If missing, re-run linking
```

**Sub-skills not linked:**
- Re-run the universal linking method
- Check for errors in symlink creation
