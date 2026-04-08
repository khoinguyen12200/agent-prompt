# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/`:
- **foundation.md** — Core workflow skills (HIGHLY RECOMMENDED)
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

## Step 3: Organize Skills

Categorize skills for user selection:

| Category | Skills |
|----------|--------|
| **Foundation** | gstack, superpowers, claude-mem (HIGHLY RECOMMENDED) |
| **Build** | Frontend, backend, database, testing |
| **Data** | Analysis, extraction, research |
| **Create** | Documents, media, design, writing |
| **Secure** | Security testing, forensics |
| **Integrate** | App automation, productivity, business tools |

## Step 4: Ask User

"Select skills to install:"

**Option 1:** Install ALL  
**Option 2:** Install Recommended (Foundation + matching Build/Data/Create/Secure/Integrate)  
**Option 3:** Select Manually (show categories with multi_select)

If Option 3, ask by category:
- Foundation (multi_select, pre-select all)
- Build (multi_select)
- Data (multi_select)
- Create (multi_select)
- Secure (multi_select)
- Integrate (multi_select)

## Step 5: Install Selected

For each selected skill, follow install instructions from its skills/ file:
- Official: plugin install or git clone
- Community: copy individual folder
- Plugins: /plugin install

## Step 6: Generate Rules

Analyze project and create `.claude/rules/` files with path-scoped constraints.

### Rule Structure

```markdown
---
name: [category]
paths:
  - "pattern/**"
  - "*.ext"
---

# [Category] Rules

## Conventions
- Convention 1 (observed from code)
- Convention 2 (observed from code)

## Checklist
- [ ] Check 1
- [ ] Check 2
```

### Detection

| Category | Detect By | Paths Pattern |
|----------|-----------|---------------|
| Frontend | React/Vue/Angular files | `src/components/**`, `*.tsx` |
| Backend | API routes, server files | `src/api/**`, `server/**` |
| Database | ORM, migration files | `prisma/**`, `migrations/**` |
| Testing | Test files | `*.test.*`, `tests/**` |
| Styling | CSS, styled files | `*.css`, `*.scss` |

### Best Practices

- One concern per file
- Use specific paths (not `**/*`)
- Extract from actual code, not generic advice
- Keep under 30 lines
- Skip if less than 5 files or inconsistent patterns

## Step 7: Generate Core Files

**CLAUDE.md:**
- List installed skills
- How to load: `Load [skill] and [command]`

**context.md:**
- Project info, tech stack, conventions

## Step 8: Report

Tell user what was installed and to restart Claude Code.
