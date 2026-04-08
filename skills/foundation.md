# Foundation Skills

## gstack

**Type:** A (GitHub + Setup)
**Source:** https://github.com/garrytan/gstack
**Prerequisites:** bun (for build), Playwright (for browser)

**What It Is:**
A collection of 23 specialist skills for end-to-end development, packaged as subdirectories each with their own SKILL.md.

**Sub-Skills (23 total):**
| Command | Purpose |
|---------|---------|
| `/office-hours` | Product planning, brainstorming |
| `/review` | Pre-landing code review |
| `/qa` | Browser testing, verification |
| `/ship` | Release workflow |
| `/cso` | Security audit (OWASP + STRIDE) |
| `/browse` | Browser automation |
| `/plan-ceo-review` | Strategic review |
| `/plan-eng-review` | Architecture planning |
| `/plan-design-review` | Design critique |
| `/design-html` | Mockup to HTML |
| `/design-shotgun` | Generate mockups |
| `/retro` | Weekly retrospective |
| `/investigate` | Systematic debugging |
| `/learn` | Pattern documentation |
| `/health` | Project health check |
| `/ship` | Deployment workflow |
| Plus 7 more... |

**Install Process:**
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup || true
# CRITICAL: Link sub-skills
cd ../.. && GSTACK_SKILLS_DIR="$(pwd)/.claude/skills" GSTACK_INSTALL_DIR="$(pwd)/.claude/skills/gstack" ./.claude/skills/gstack/bin/gstack-relink
```

**Post-Install Verification:**
```bash
ls .claude/skills/office-hours/SKILL.md  # Should exist
ls .claude/skills/review/SKILL.md        # Should exist
ls .claude/skills/qa/SKILL.md            # Should exist
```

---

## superpowers

**Type:** B (Plugin)
**Source:** https://github.com/obra/superpowers
**Prerequisites:** None

**What It Is:**
12 workflow skills in the `skills/` subdirectory.

**Sub-Skills (12 total):**
| Command | Purpose |
|---------|---------|
| `/systematic-debugging` | 4-phase debugging |
| `/test-driven-development` | TDD workflow |
| `/subagent-driven-development` | Parallel agents |
| `/brainstorming` | Design refinement |
| `/writing-plans` | Plan creation |
| `/executing-plans` | Plan execution |
| `/receiving-code-review` | Handle review feedback |
| `/requesting-code-review` | Request review |
| Plus 3 more... |

**Install Process:**
```bash
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers
```

**Structure:**
- `.claude/skills/superpowers/skills/<name>/SKILL.md` - Each subdirectory is a skill

---

## claude-mem

**Type:** B (Plugin)
**Source:** claude-mem@thedotmack
**Prerequisites:** None

**What It Is:**
Memory persistence across Claude Code sessions.

**Command:**
- `/mem` - Recall and manage memory

**Install Process:**
```bash
/plugin install claude-mem@thedotmack
```
