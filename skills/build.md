# Build Skills

Frontend, backend, database, and testing.

## Frontend

### react-components
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/react-components

**Provides:** React component patterns

**Configuration:**
- paths: src/**/*.tsx, src/**/*.jsx

### vue-components
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/vue

**Provides:** Vue component patterns

**Configuration:**
- paths: src/**/*.vue

---

## Backend

### api-design
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/api-design

**Provides:** REST API patterns

**Configuration:**
- paths: src/api/**, **/routes/**

### python-skills
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/python-best-practices

**Provides:** Python patterns

**Configuration:**
- paths: **/*.py

---

## Database

### prisma
**Type:** Plugin (marketplace)
**Source:** prisma@anthropic-agent-skills

**Provides:** Prisma schema assistance

**Configuration:**
- paths: prisma/**, **/*.prisma

### postgres
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/postgres

**Provides:** PostgreSQL queries

---

## Testing

### playwright
**Type:** Simple Skill (SKILL.md)
**Source:** awesome-claude-skills/playwright

**Provides:** E2E test generation

**Configuration:**
- paths: **/*.spec.ts, tests/**

---

## Awesome Claude Skills Note

awesome-claude-skills is a catalog with 100+ individual skills. Install by copying specific folders:

```bash
# Clone catalog to temp (once)
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy only needed skills
cp -r /tmp/awesome/[skill-name] .claude/skills/
```

Do NOT clone entire catalog to .claude/skills/
