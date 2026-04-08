# Build Skills

Skills for building applications — frontend, backend, database, APIs.

## Foundation (Highly Recommended)

### gstack
**Source:** https://github.com/garrytan/gstack  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup
```
**What:** 23 specialists — planning, review, QA, shipping

### superpowers
**Source:** https://github.com/obra/superpowers  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers
```
**What:** Debugging, TDD, planning, subagent-driven dev

## Frontend

### Official
- **react-components** — From https://github.com/anthropics/skills
- **vue-components** — From https://github.com/anthropics/skills

### From awesome-claude-skills catalog (copy individually):
```bash
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
cp -r /tmp/awesome/artifacts-builder .claude/skills/
cp -r /tmp/awesome/d3-visualization .claude/skills/
```
- **artifacts-builder** — HTML/React/Tailwind artifacts
- **d3-visualization** — D3 charts

### Plugins
- **frontend-design** — `/plugin install frontend-design`

## Backend

### Official
- **api-design** — From https://github.com/anthropics/skills
- **nodejs-express** — From https://github.com/anthropics/skills
- **python-skills** — From https://github.com/anthropics/skills

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/aws-skills .claude/skills/
cp -r /tmp/awesome/mcp-builder .claude/skills/
cp -r /tmp/awesome/software-architecture .claude/skills/
cp -r /tmp/awesome/prompt-engineering .claude/skills/
```

## Database

### Official
- **sql-queries** — From https://github.com/anthropics/skills
- **database-migrations** — From https://github.com/anthropics/skills

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/postgres .claude/skills/
```
- **postgres** — PostgreSQL queries

### Plugins
- **prisma** — `/plugin install prisma`

## Testing

### From superpowers
- `test-driven-development` — TDD workflow

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/playwright .claude/skills/
cp -r /tmp/awesome/webapp-testing .claude/skills/
cp -r /tmp/awesome/pypict-testing .claude/skills/
```

## Usage

```
Load gstack and run /office-hours
Load react-components
Load postgres and query the database
```
