# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## IMPORTANT: About awesome-claude-skills

**awesome-claude-skills is a CATALOG, not a skill.** It contains 100+ individual skill folders.  
**DO NOT** clone the entire repo to `.claude/skills/awesome` — Claude won't recognize it.

**Correct approach:**
```bash
# Clone to temp (one time)
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy ONLY the individual skills you need:
cp -r /tmp/awesome/slack-automation .claude/skills/
cp -r /tmp/awesome/github-automation .claude/skills/
cp -r /tmp/awesome/postgres .claude/skills/
# etc...
```

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/`:
- **foundation.md** — Core skills (HIGHLY RECOMMENDED)
- **build.md** — Frontend, backend, database, testing
- **data.md** — Data analysis, extraction, research
- **create.md** — Documents, media, design, content
- **secure.md** — Security testing, forensics
- **integrate.md** — App automation, productivity, business

## Step 2: Detect Project

Scan current project for:
- Technology stack (React, Vue, Node, Python, etc.)
- File patterns and frameworks
- Existing .claude/ configuration

## Step 3: Select Skills to Install

Ask user:

"Select skills to install:"

**Option 1:** Install ALL individual skills (not recommended — too many)

**Option 2:** Install Recommended (Foundation + skills matching your project type)

**Option 3:** Select Manually (show categories with multi_select)

If Option 3, ask by category:
- Foundation (multi_select, pre-select all — gstack, superpowers, claude-mem)
- Build (multi_select — frontend, backend, database, testing)
- Data (multi_select)
- Create (multi_select)
- Secure (multi_select)
- Integrate (multi_select)

## Step 4: Install Selected

### For Foundation/Official Skills:
```bash
# gstack
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup

# superpowers
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers

# claude-mem — follow instructions in skills/foundation.md
```

### For Official (Anthropics):
```bash
# Plugin approach (recommended)
/plugin install document-skills@anthropic-agent-skills

# OR clone for project level
git clone --depth 1 https://github.com/anthropics/skills.git .claude/skills/anthropics
```

### For Community (Awesome) — COPY INDIVIDUAL SKILLS:
```bash
# Clone catalog to temp (one time)
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy ONLY selected skills:
cp -r /tmp/awesome/[skill-name] .claude/skills/

# Example — if project uses GitHub and Slack:
cp -r /tmp/awesome/github-automation .claude/skills/
cp -r /tmp/awesome/slack-automation .claude/skills/
```

### For Plugins:
```bash
/plugin install [plugin-name]
```

## Step 5: Generate Rules

Analyze project and create `.claude/rules/` files.

### Rule Structure

```markdown
---
name: [category]
paths:
  - "pattern/**"
  - "*.ext"
---

# [Category] Rules

## Conventions (from actual code)
- Convention 1
- Convention 2

## Checklist
- [ ] Check 1
- [ ] Check 2
```

### Path Patterns Reference

| Pattern | Matches |
|---------|---------|
| `**/*.ts` | All TypeScript files |
| `src/components/**/*.tsx` | React components |
| `src/api/**/*.ts` | API routes |
| `prisma/**` | Prisma files |
| `tests/**/*.test.ts` | Test files |

### Best Practices

- Use specific paths (not `**/*` which matches everything)
- Extract from actual code, not generic advice
- Keep under 30 lines
- One concern per file
- Skip if less than 5 files or inconsistent patterns

## Step 6: Generate settings.json

Create `.claude/settings.json` with installed skills:

```json
{
  "permissions": {},
  "hooks": {},
  "enabledSkills": [
    "gstack",
    "superpowers",
    "claude-mem",
    [LIST OTHER INSTALLED SKILLS HERE]
  ]
}
```

Or if skills are in subdirectories:
```json
{
  "permissions": {},
  "hooks": {},
  "enabledSkills": [
    "foundation/gstack",
    "foundation/superpowers", 
    "build/react-components",
    [ETC...]
  ]
}
```

## Step 7: Generate Core Files

**CLAUDE.md:**
- List installed skills
- How to load: `Load [skill] and [command]`

**context.md:**
- Project info, tech stack, conventions

## Step 8: Report

Tell user what was installed:

```
Bootstrap Complete ✓

Foundation (Highly Recommended):
- gstack — 23 specialists
- superpowers — 12 workflow skills  
- claude-mem — memory

Installed for Your Project:
[LIST SELECTED SKILLS WITH CATEGORIES]

Generated:
- .claude/CLAUDE.md
- .claude/context.md
- .claude/rules/

Next: Restart Claude Code
```
