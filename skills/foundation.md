# Foundation Skills

Core skills for any software project.

## gstack

**Type:** GitHub + Setup Script
**Source:** https://github.com/garrytan/gstack

**Provides:** 23 specialists — planning, review, QA, shipping, security

**Commands:**
- `/office-hours` — Product planning
- `/review` — Code review
- `/qa` — Browser testing
- `/ship` — Release workflow
- `/cso` — Security audit
- `/browse` — Browser automation

**Install Requirements:**
- bun (will be checked by setup script)
- Must run `./setup` after clone

**Configuration (from SKILL.md):**
- allowed-tools: Bash, Read, AskUserQuestion
- hooks: SessionStart (auto-detects proactive mode)

---

## superpowers

**Type:** Plugin (.claude-plugin/)
**Source:** https://github.com/obra/superpowers

**Provides:** 12 workflow skills — debugging, TDD, collaboration

**Commands:**
- `/systematic-debugging` — 4-phase debugging
- `/test-driven-development` — TDD workflow
- `/subagent-driven-development` — Parallel agents
- Plus 9 more...

**Install Requirements:**
- Clone only (no setup script)

**Configuration:**
- Skills auto-register from skills/ directory
- No special hooks required

---

## claude-mem

**Type:** Plugin (marketplace)
**Source:** claude-mem@thedotmack

**Provides:** Memory persistence across sessions

**Install Requirements:**
- /plugin install claude-mem@thedotmack

**Configuration:**
- Hooks auto-configured by plugin
