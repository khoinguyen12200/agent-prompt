# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/` to understand available skills.

## Step 2: Detect Project

Scan current project for:
- Technology stack (React, Vue, Node, Python, etc.)
- File patterns and frameworks
- Existing .claude/ configuration

## Step 3: Organize Skills for User

Categorize all skills into:

**Highly Recommended:**
- gstack, superpowers, claude-mem

**Detected for Project:**
- Skills matching detected tech stack

**Other Potentially Useful:**
- Skills that might be helpful based on project type

## Step 4: Ask User

Present organized skills and ask:

"Select skills to install:"

**Option 1:** Install ALL (180+ skills)

**Option 2:** Install Recommended + Detected (highly recommended + skills matching your project)

**Option 3:** Select Manually (show organized list with multi_select)

If Option 3, show:
- Highly Recommended (multi_select)
- Detected for Project (multi_select)
- Other Skills (multi_select)

## Step 5: Install Selected

Install each selected skill using instructions from its skills/ file.

## Step 6: Generate Rules

Analyze project structure and create `.claude/rules/` files with path-scoped constraints.

### Rule Structure

Each rule file must have YAML frontmatter with `paths:` to scope it to specific files:

```markdown
---
name: [category]
paths:
  - "pattern/**"
  - "*.ext"
---

# [Category] Rules

## Conventions
- Convention 1 (observed from actual code)
- Convention 2 (observed from actual code)

## Checklist
- [ ] Check 1
- [ ] Check 2
```

### Detection Process

1. **Scan codebase** — List all directories, identify file extensions
2. **Identify patterns** — Look for: frontend, backend, database, tests, config, docs
3. **Read sample files** — Read 3-5 files per category to extract actual conventions
4. **Document patterns** — Write rules based on observed code, not generic advice

### Categories to Detect

| Category | File Pattern | What to Extract |
|----------|--------------|-----------------|
| Frontend | `src/components/**`, `*.tsx`, `*.jsx`, `*.vue` | Component patterns, naming, imports |
| Backend | `src/api/**`, `src/routes/**`, `server/**` | API patterns, error handling |
| Database | `prisma/**`, `migrations/**`, `models/**` | Schema patterns, naming |
| Testing | `*.test.*`, `*.spec.*`, `tests/**` | Test structure, assertions |
| TypeScript | `*.ts`, `*.tsx` | Type patterns, interfaces |
| Config | `*.config.*`, `config/**` | Config structure |
| Styling | `*.css`, `*.scss`, `*.styled.*` | Class naming, organization |

### Best Practices

- **One concern per file** — Don't mix frontend and backend rules
- **Use specific paths** — `src/components/**/*.tsx` not `**/*.tsx`
- **Extract from code** — Document what you actually see, not what you think should be
- **Keep it short** — Under 30 lines per rule file
- **Skip if unclear** — If files are inconsistent, don't create a rule
- **Use checklists** — End with 3-5 verification checklists

### Example Rule File

```markdown
---
name: frontend
paths:
  - "src/components/**/*.tsx"
  - "src/pages/**/*.tsx"
---

# Frontend Rules

## Conventions
- Use named exports for components
- Props interface named `Props`
- Use composition over inheritance

## Checklist
- [ ] Component renders without errors
- [ ] TypeScript types are correct
- [ ] Follows existing naming pattern
```

### Skip Conditions

Do NOT create a rule if:
- Less than 5 files in the category
- Files have inconsistent patterns
- No clear convention emerges from sample files

## Step 7: Generate Core Files

**CLAUDE.md:**
- List installed skills
- How to load and use them

**context.md:**
- Project info and conventions

## Step 8: Report

Tell user what was installed and to restart Claude Code.
