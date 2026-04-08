# superpowers

**Status:** MANDATORY  
**Source:** https://github.com/obra/superpowers

## Install

### Option 1: Plugin (Global)
```bash
/plugin install superpowers@claude-plugins-official
```

### Option 2: Project Level (Git Clone)
```bash
git clone --single-branch --depth 1 https://github.com/obra/superpowers.git .claude/skills/superpowers
```

Then add to CLAUDE.md: "Load skills from .claude/skills/superpowers/skills/"

## What It Is

Development workflow skills with systematic debugging, planning, and subagent-driven development.

## Available Skills

| Skill | When to Use |
|-------|-------------|
| brainstorming | Planning phase |
| writing-plans | Implementation planning |
| executing-plans | Batch execution |
| subagent-driven-development | Complex multi-task work |
| dispatching-parallel-agents | Concurrent subagents |
| test-driven-development | RED-GREEN-REFACTOR |
| systematic-debugging | Debugging errors |
| root-cause-tracing | Deep error tracing |
| using-git-worktrees | Isolated branches |
| finishing-a-development-branch | Complete work |
| requesting-code-review | Pre-review checklist |
| receiving-code-review | Handle feedback |

## Intent Mapping

```yaml
debug: Load superpowers systematic-debugging
refactor: Load superpowers subagent-driven-development
plan: Load superpowers brainstorming
```
