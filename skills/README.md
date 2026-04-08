# Skills Catalog

Complete list of available skills from community sources.

## Sources

| Source | URL | Type |
|--------|-----|------|
| gstack | https://github.com/garrytan/gstack | Agentic workflow (23 specialists) |
| superpowers | https://github.com/obra/superpowers | Development workflow |
| anthropics | https://github.com/anthropics/skills | Official document skills |
| awesome | https://github.com/ComposioHQ/awesome-claude-skills | Community skills (100+) |

## Categories

| File | Description | Skill Count |
|------|-------------|-------------|
| [gstack.md](gstack.md) | 23 specialist skills for end-to-end development | 23 |
| [superpowers.md](superpowers.md) | Development workflow and debugging | 12 |
| [document-processing.md](document-processing.md) | PDF, Word, Excel, PowerPoint | 6 |
| [development.md](development.md) | Coding, testing, architecture | 24 |
| [app-automation.md](app-automation.md) | 78+ SaaS app integrations | 78+ |
| [data-analysis.md](data-analysis.md) | SQL, CSV, databases | 6 |
| [business-marketing.md](business-marketing.md) | Content, leads, research | 13 |
| [creative-media.md](creative-media.md) | Images, video, design | 9 |
| [productivity.md](productivity.md) | File mgmt, workspace, utilities | 14 |
| [security-forensics.md](security-forensics.md) | Security, forensics | 4 |

## Quick Reference

### Most Used Skills

| Intent | Command | Source |
|--------|---------|--------|
| Build feature | `Load gstack. Run /office-hours` | gstack |
| Review code | `Load gstack. Run /review` | gstack |
| Test | `Load gstack. Run /qa` | gstack |
| Ship | `Load gstack. Run /ship` | gstack |
| Debug | `Load superpowers. Use systematic-debugging` | superpowers |
| Refactor | `Load superpowers. Use subagent-driven-development` | superpowers |
| Plan | `Load superpowers. Use brainstorming` | superpowers |
| PDF/Word | `Load anthropics-skills` | anthropics |
| Scrape web | `Load awesome-claude-skills. Use firecrawl` | awesome |
| GitHub | `Load awesome-claude-skills. Use github-automation` | awesome |

## Install Commands

```bash
# GStack (23 specialists)
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup

# Superpowers
/plugin install superpowers@claude-plugins-official

# Anthropics (document skills)
/plugin install document-skills@anthropic-agent-skills

# Awesome (100+ community skills)
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git ~/.claude/skills/awesome
```

## Total: 180+ Skills
