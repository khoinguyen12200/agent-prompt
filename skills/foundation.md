# Foundation Skills

Core skills valuable for any software project.

## gstack

**Type:** Multi-skill repository
**Source:** https://github.com/garrytan/gstack

**What It Is:**
A collection of 23 specialist skills for end-to-end software development. Each skill is a subdirectory with its own `SKILL.md`.

**Skills Provided:**
- office-hours — Product planning and brainstorming
- review — Code review before landing changes
- qa — Browser testing and verification
- ship — Release and deployment workflow
- cso — Security audit (OWASP + STRIDE)
- browse — Browser automation
- plan-ceo-review — Strategic review
- plan-eng-review — Architecture planning
- plan-design-review — Design critique
- design-html — Convert mockups to HTML
- design-shotgun — Generate mockups
- retro — Weekly retrospective
- investigate — Systematic debugging
- learn — Pattern documentation
- health — Project health check
- document-release — Documentation updates
- freeze/unfreeze — Code freeze management
- checkpoint — Save progress
- canary — Canary deployment
- benchmark — Performance testing
- land-and-deploy — Landing workflow
- setup-deploy — Deployment setup
- pair-agent — Pair programming

**Prerequisites:**
- bun (for building browser binary)
- Playwright dependencies (for browser automation features)

**Installation Notes:**
- Has setup script that builds browser binary
- Has `bin/gstack-relink` to link sub-skills for discovery
- Browser features require Playwright; non-browser features work without it
- Sub-skills must be linked to be discoverable as individual commands

**Configuration:**
- Each sub-skill has own `allowed-tools` in its SKILL.md
- Main skill has SessionStart hooks

---

## superpowers

**Type:** Multi-skill repository  
**Source:** https://github.com/obra/superpowers

**What It Is:**
12 workflow skills for debugging, TDD, and collaboration patterns.

**Skills Provided:**
systematic-debugging — 4-phase debugging methodology
test-driven-development — TDD workflow
subagent-driven-development — Parallel agent tasks
brainstorming — Design refinement
writing-plans — Plan creation
executing-plans — Plan execution
receiving-code-review — Handle review feedback
requesting-code-review — Request review
finishing-a-development-branch — Branch completion
using-git-worktrees — Worktree management
verification-before-completion — Pre-completion checks
dispatching-parallel-agents — Agent orchestration

**Structure:**
Skills are in `skills/` subdirectory, each with own `SKILL.md`.

**Configuration:**
Each skill has its own frontmatter with allowed-tools and hooks.

---

## claude-mem

**Type:** Plugin
**Source:** claude-mem@thedotmack

**What It Is:**
Memory persistence across Claude Code sessions.

**Installation:**
Via plugin marketplace.

**Configuration:**
Auto-configured by plugin.
