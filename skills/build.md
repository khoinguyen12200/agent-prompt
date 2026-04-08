# Build Skills

Frontend, backend, database, and testing skills.

## Frontend

### react-components
**Source:** awesome-claude-skills (react-components)
**Type:** Catalog skill

**Provides:**
- React component generation and refactoring

**Configuration:**
- paths: src/**/*.tsx, src/**/*.jsx, *.tsx, *.jsx
- allowed-tools: Read, Write, Edit

### vue-components
**Source:** awesome-claude-skills (vue)
**Type:** Catalog skill

**Provides:**
- Vue component patterns

**Configuration:**
- paths: src/**/*.vue
- allowed-tools: Read, Write, Edit

### frontend-design
**Source:** frontend-design@claude-plugins
**Type:** Plugin

**Provides:**
- Design system guidance

---

## Backend

### api-design
**Source:** awesome-claude-skills (api-design)
**Type:** Catalog skill

**Provides:**
- REST API design patterns

**Configuration:**
- paths: src/api/**, **/routes/**, **/controllers/**
- allowed-tools: Read, Write, Edit

### nodejs-express
**Source:** awesome-claude-skills (nodejs-express)
**Type:** Catalog skill

**Provides:**
- Express.js patterns and middleware

**Configuration:**
- paths: **/*.js, **/*.ts (when package.json has express)
- allowed-tools: Read, Write, Edit, Bash(node *)

### python-skills
**Source:** awesome-claude-skills (python-best-practices)
**Type:** Catalog skill

**Provides:**
- Python best practices

**Configuration:**
- paths: **/*.py
- allowed-tools: Read, Write, Edit, Bash(python *), Bash(pip *)

---

## Database

### prisma
**Source:** prisma@anthropic-agent-skills
**Type:** Plugin

**Provides:**
- Prisma schema and query assistance

**Configuration:**
- paths: prisma/**, **/*.prisma
- allowed-tools: Bash(npx prisma *)

### postgres
**Source:** awesome-claude-skills (postgres)
**Type:** Catalog skill

**Provides:**
- PostgreSQL query help

**Configuration:**
- allowed-tools: Bash(psql *)

---

## Testing

### playwright
**Source:** awesome-claude-skills (playwright)
**Type:** Catalog skill

**Provides:**
- E2E test generation

**Configuration:**
- paths: **/*.spec.ts, **/*.test.ts, tests/**
- allowed-tools: Bash(npx playwright *)

### jest
**Source:** awesome-claude-skills (jest)
**Type:** Catalog skill

**Provides:**
- Jest testing patterns

**Configuration:**
- paths: **/*.test.js, **/*.test.ts
- allowed-tools: Bash(npx jest *)

---

## About Awesome Claude Skills

awesome-claude-skills is a catalog containing 100+ individual skill folders. When installing skills from this catalog:

1. Clone the catalog: `git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome`
2. Copy only the specific skill folders you need to `.claude/skills/`

Do not clone the entire catalog into `.claude/skills/` - Claude won't recognize individual skills.
