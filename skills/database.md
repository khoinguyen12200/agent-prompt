# Database Skills

Install these if project uses databases.

## prisma

**Source:** https://claude.com/plugins/prisma  
**Install:**
```bash
# Plugin (global)
/plugin install prisma

# Or check if standalone skill available
```
**When:** Using Prisma ORM  
**What:** Prisma schema design and queries

## postgres

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```
**When:** PostgreSQL queries needed  
**What:** Safe read-only SQL queries against PostgreSQL

## sql-queries

**Source:** https://github.com/anthropics/skills  
**Install:**
```bash
# Via plugin
/plugin install example-skills@anthropic-agent-skills

# Or clone for project level
git clone --single-branch --depth 1 https://github.com/anthropics/skills.git .claude/skills/anthropics
```
**When:** SQL optimization  
**What:** SQL query optimization and patterns

## database-migrations

**Source:** https://github.com/anthropics/skills  
**Install:** With anthropics skills repo  
**When:** Database migrations  
**What:** Migration strategies and tools

## Intent Mapping

```yaml
database: Load postgres or prisma
sql: Load sql-queries
migrations: Load database-migrations
```
