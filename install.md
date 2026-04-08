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

### What Are Rules?

Rules are markdown files in `.claude/rules/` that auto-load when you work with matching files. They give Claude specific instructions for different parts of your codebase.

**Example:** When you edit `src/components/Button.tsx`, the `frontend.md` rule auto-loads.

### Rule Structure

Every rule MUST have YAML frontmatter with `paths:`

```markdown
---
name: frontend
paths:
  - "src/components/**/*.tsx"
  - "src/components/**/*.jsx"
  - "src/pages/**/*.tsx"
---

# Frontend Rules

## Conventions (observed from actual code)
- Use named exports for components
- Props interface named `Props`
- Default to functional components

## Checklist
- [ ] Component renders without errors
- [ ] TypeScript types are correct
- [ ] Follows existing project patterns
```

### How Rules Work

| Trigger | What Happens |
|---------|--------------|
| Read file matching `paths` | Rule auto-loads into context |
| Work on different files | Rule stays unloaded (saves context) |
| Multiple rules match | All matching rules load |

### Detection Process

1. **Scan directories** — List all folders and file extensions
2. **Identify categories** — Look for:
   - Frontend (React, Vue, Angular)
   - Backend (API routes, handlers)
   - Database (ORM, migrations, models)
   - Testing (test files, specs)
   - Config (configs, scripts)
   - Documentation (docs, markdown)

3. **Sample files** — Read 3-5 files per category to extract actual patterns

4. **Write rules** — Document what you observe, not what you think should be

### Path Patterns

| Pattern | Matches |
|---------|---------|
| `**/*.ts` | All TypeScript files |
| `src/components/**/*.tsx` | React components |
| `src/api/**/*.ts` | API routes |
| `prisma/**` | Prisma files |
| `tests/**/*.test.ts` | Test files |
| `*.{ts,tsx}` | TS and TSX in root |

### Writing Effective Rules

**DO:**
- Use specific paths (not `**/*` which matches everything)
- Extract from actual code patterns
- Be concrete ("Use 2-space indent" not "Format nicely")
- Keep under 30 lines per rule
- One concern per file (frontend ≠ backend rules)

**DON'T:**
- Write generic advice
- Copy style guides from internet
- Create rules for < 5 files
- Mix unrelated concerns

### Categories to Detect

| Category | Detect By | Paths Example |
|----------|-----------|---------------|
| **Frontend** | React/Vue/Angular imports | `src/components/**`, `*.tsx` |
| **Backend** | API handlers, routes | `src/api/**`, `server/**` |
| **Database** | ORM models, migrations | `prisma/**`, `migrations/**` |
| **Testing** | Test files, jest/vitest | `*.test.*`, `tests/**` |
| **TypeScript** | .ts files | `src/**/*.ts` |
| **Styling** | CSS, styled-components | `*.css`, `*.styled.*` |

### Skip If

Do NOT create a rule if:
- Less than 5 files in the category
- Files have inconsistent/no patterns
- Can't determine clear conventions from samples

### Example Rules by Category

**Frontend Rule:**
```markdown
---
name: frontend
paths:
  - "src/components/**/*.tsx"
  - "src/pages/**/*.tsx"
---

- Use named exports
- Props interface: `Props`
- Composition over inheritance
```

**API Rule:**
```markdown
---
name: backend
paths:
  - "src/api/**/*.ts"
---

- Validate all inputs with zod
- Return `{ success, data, error }` format
- Use 200/201/400/404/500 status codes
```

**Testing Rule:**
```markdown
---
name: testing
paths:
  - "**/*.test.ts"
  - "tests/**"
---

- Test description: "should..."
- One assertion per test ideally
- Mock external dependencies
```

## Step 7: Generate Core Files

**CLAUDE.md:**
- List installed skills
- How to load: `Load [skill] and [command]`

**context.md:**
- Project info, tech stack, conventions

## Step 8: Report

Tell user what was installed and to restart Claude Code.
