# Foundation Skills

Skills that provide value for any software project.

## gstack

**Type:** Multi-skill repository  
**Source:** https://github.com/garrytan/gstack  
**Install Type:** Type A (GitHub + Setup + Sub-skill linking)

### What It Is
A collection of 23 specialist skills for end-to-end software development. Each subdirectory contains a separate skill with its own SKILL.md.

### Sub-Skills (23 total)
Each subdirectory is a standalone skill:

| Directory | Command | Description | Auto-invoke Keywords |
|-----------|---------|-------------|---------------------|
| office-hours | /office-hours | Product planning, brainstorming | "brainstorm", "product idea", "worth building" |
| review | /review | Code review before landing | "review code", "check PR", "pre-landing" |
| qa | /qa | Browser testing, verification | "test site", "verify deployment", "dogfood" |
| ship | /ship | Release workflow | "release", "deploy", "ship this" |
| cso | /cso | Security audit (OWASP + STRIDE) | "security audit", "security review" |
| browse | /browse | Browser automation | "open browser", "test in browser" |
| plan-ceo-review | /plan-ceo-review | Strategic review | "CEO review", "strategy review" |
| plan-eng-review | /plan-eng-review | Architecture planning | "eng review", "architecture review" |
| plan-design-review | /plan-design-review | Design critique | "design review", "critique design" |
| design-html | /design-html | Mockup to HTML | "design to HTML", "convert mockup" |
| design-shotgun | /design-shotgun | Generate mockups | "generate mockups", "design ideas" |
| retro | /retro | Weekly retrospective | "retrospective", "retro", "weekly review" |
| investigate | /investigate | Systematic debugging | "investigate", "debug this" |
| learn | /learn | Pattern documentation | "document pattern", "learning" |
| health | /health | Project health check | "health check", "project status" |
| document-release | /document-release | Documentation updates | "document release", "update docs" |
| freeze | /freeze | Code freeze | "freeze code", "lock branch" |
| unfreeze | /unfreeze | Remove code freeze | "unfreeze", "unlock branch" |
| checkpoint | /checkpoint | Save progress | "checkpoint", "save progress" |
| canary | /canary | Canary deployment | "canary", "gradual rollout" |
| benchmark | /benchmark | Performance testing | "benchmark", "performance test" |
| land-and-deploy | /land-and-deploy | Landing workflow | "land changes", "deploy to prod" |
| setup-deploy | /setup-deploy | Deployment setup | "setup deploy", "configure deployment" |
| pair-agent | /pair-agent | Pair programming | "pair program", "work together" |
| setup-browser-cookies | /setup-browser-cookies | Browser auth setup | "browser cookies", "auth setup" |
| gstack-upgrade | /gstack-upgrade | Update gstack | "upgrade gstack", "update gstack" |

### Prerequisites
- bun (checked by setup script, optional)
- Playwright dependencies (optional, for browser features)

### Installation Requirements
1. Clone to `.claude/skills/gstack/`
2. Run `./setup` if bun is available (continues if fails)
3. **CRITICAL:** Run `./bin/gstack-relink` to link all sub-skills
4. Verify sub-skills exist at `.claude/skills/<sub-skill>/SKILL.md`

### Configuration Notes
- Each sub-skill has its own frontmatter
- Main skill has SessionStart hooks
- Browser features require Playwright
- Non-browser features work without Playwright

### Potential Detection
- **HIGH for any project** - Foundation skills valuable everywhere

---

## superpowers

**Type:** Multi-skill repository  
**Source:** https://github.com/obra/superpowers  
**Install Type:** Type B (GitHub + Sub-skill linking)

### What It Is
12 workflow skills for debugging, TDD, and collaboration patterns. Skills are in `skills/` subdirectory.

### Sub-Skills (12 total)

| Directory | Command | Description | Auto-invoke Keywords |
|-----------|---------|-------------|---------------------|
| systematic-debugging | /systematic-debugging | 4-phase debugging | "debug this", "find bug", "what's wrong" |
| test-driven-development | /test-driven-development | TDD workflow | "TDD", "test first", "write tests" |
| subagent-driven-development | /subagent-driven-development | Parallel agents | "parallel", "multiple agents", "concurrent" |
| brainstorming | /brainstorming | Design refinement | "brainstorm", "ideas", "explore options" |
| writing-plans | /writing-plans | Plan creation | "write plan", "create plan", "plan this" |
| executing-plans | /executing-plans | Plan execution | "execute plan", "do the plan" |
| receiving-code-review | /receiving-code-review | Handle review feedback | "address feedback", "review comments" |
| requesting-code-review | /requesting-code-review | Request review | "request review", "ask for review" |
| finishing-a-development-branch | /finishing-a-development-branch | Branch completion | "finish branch", "wrap up", "complete" |
| using-git-worktrees | /using-git-worktrees | Worktree management | "worktree", "isolate work" |
| verification-before-completion | /verification-before-completion | Pre-completion checks | "verify before", "double check", "validate" |
| dispatching-parallel-agents | /dispatching-parallel-agents | Agent orchestration | "dispatch agents", "run in parallel" |

### Prerequisites
- None

### Installation Requirements
1. Clone to `.claude/skills/superpowers/`
2. **CRITICAL:** Link sub-skills from `superpowers/skills/` to `.claude/skills/`
3. Verify each sub-skill has SKILL.md at top level

### Configuration Notes
- Each sub-skill has its own frontmatter with allowed-tools
- No global setup script required

### Potential Detection
- **HIGH for any project** - Debugging and TDD patterns valuable everywhere

---

## claude-mem

**Type:** Plugin  
**Source:** claude-mem@thedotmack  
**Install Type:** Type D (Plugin marketplace)

### What It Is
Memory persistence across Claude Code sessions.

### Command
- /mem — Recall and manage memory

### Installation Requirements
- Install via `/plugin install claude-mem@thedotmack`
- Plugin handles its own configuration

### Configuration Notes
- Auto-configured by plugin
- User-level installation (available across projects)

### Potential Detection
- **HIGH for any project** - Memory useful everywhere
