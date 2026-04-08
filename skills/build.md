# Build Skills

Frontend, backend, database, and testing skills.

## Frontend

### react-components
**Type:** Single-skill
**Source:** awesome-claude-skills/react-components

**What It Is:**
React component generation and refactoring patterns.

**Auto-load Paths:**
- src/**/*.tsx
- src/**/*.jsx

### vue-components
**Type:** Single-skill
**Source:** awesome-claude-skills/vue

**What It Is:**
Vue component patterns and best practices.

**Auto-load Paths:**
- src/**/*.vue

### frontend-design
**Type:** Plugin
**Source:** frontend-design@claude-plugins

**What It Is:**
Design system guidance for frontend development.

---

## Backend

### api-design
**Type:** Single-skill
**Source:** awesome-claude-skills/api-design

**What It Is:**
REST API design patterns and conventions.

**Auto-load Paths:**
- src/api/**
- **/routes/**
- **/controllers/**

### nodejs-express
**Type:** Single-skill
**Source:** awesome-claude-skills/nodejs-express

**What It Is:**
Express.js patterns and middleware development.

**Auto-load Paths:**
- **/*.js, **/*.ts (when Express detected)

### python-skills
**Type:** Single-skill
**Source:** awesome-claude-skills/python-best-practices

**What It Is:**
Python best practices and patterns.

**Auto-load Paths:**
- **/*.py

---

## Database

### prisma
**Type:** Plugin
**Source:** prisma@anthropic-agent-skills

**What It Is:**
Prisma schema and query assistance.

**Auto-load Paths:**
- prisma/**
- **/*.prisma

### postgres
**Type:** Single-skill
**Source:** awesome-claude-skills/postgres

**What It Is:**
PostgreSQL query assistance and optimization.

---

## Testing

### playwright
**Type:** Single-skill
**Source:** awesome-claude-skills/playwright

**What It Is:**
E2E test generation with Playwright.

**Auto-load Paths:**
- **/*.spec.ts
- tests/**

### jest
**Type:** Single-skill
**Source:** awesome-claude-skills/jest

**What It Is:**
Jest testing patterns and best practices.

**Auto-load Paths:**
- **/*.test.js
- **/*.test.ts

---

## Awesome Claude Skills Note

awesome-claude-skills is a catalog containing 100+ individual skills. When installing:

1. Clone catalog to temporary location
2. Copy only the specific skill directories needed
3. Place directly in `.claude/skills/` (not nested under awesome/)

Each skill in the catalog is a single-skill directory with its own SKILL.md.
