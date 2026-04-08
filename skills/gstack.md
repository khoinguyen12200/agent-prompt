# gstack

**Status:** MANDATORY  
**Source:** https://github.com/garrytan/gstack

## Install

### Option 1: Global (Recommended)
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup
```

### Option 2: Project Level
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup
```

## What It Is

23 specialist skills for end-to-end software development. YC-style workflow with planning, review, QA, and shipping.

## Available Commands

| Command | When to Use |
|---------|-------------|
| /office-hours | Building new feature - 6 forcing questions |
| /plan-ceo-review | Strategic decisions |
| /plan-eng-review | Technical planning |
| /plan-design-review | UI/UX decisions |
| /autoplan | Full pipeline (CEO→Eng→Design) |
| /review | Code complete |
| /qa | Ready to test |
| /ship | Ready to release |
| /cso | Security audit |
| /browse | Need browser |
| /design-html | Mockup to production HTML |
| /retro | Weekly retro |
| + 10 more... |

## Intent Mapping

```yaml
build: Load gstack /office-hours
review: Load gstack /review
test: Load gstack /qa
ship: Load gstack /ship
```
