# Foundation Skills

Core skills valuable for any software project.

## gstack

**Source:** github:garrytan/gstack
**Type:** GitHub repository
**Setup:** Has `./setup` script to run after clone

**Provides:**
- 23 specialist commands: /office-hours, /review, /qa, /ship, /cso, /browse, etc.
- Planning, code review, testing, security audit, shipping workflows

**Configuration:**
- hooks.SessionStart: Announces availability
- allowed-tools: Bash(git *), Bash(gh *), Read, Grep, Edit, Write

---

## superpowers

**Source:** github:obra/superpowers
**Type:** GitHub repository

**Provides:**
- 12 workflow skills: systematic-debugging, test-driven-development, etc.
- Debugging, refactoring, TDD patterns

**Configuration:**
- hooks.SessionStart: Announces availability
- allowed-tools: Bash(npm *), Bash(yarn *), Bash(node *)

---

## claude-mem

**Source:** claude-mem@thedotmack
**Type:** Plugin

**Provides:**
- Memory persistence across sessions

**Configuration:**
- hooks.SessionStart: Loads memory
