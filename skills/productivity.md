# Productivity Skills

Install these for file management and workspace utilities.

## Setup

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```

## Available Skills

| Skill | When | What |
|-------|------|------|
| file-organizer | File mgmt | Organize files/folders |
| invoice-organizer | Taxes | Organize receipts for tax prep |
| kaizen | Improvement | Continuous improvement (Lean) |
| n8n-skills | Workflows | Operate n8n workflows |
| raffle-winner-picker | Giveaways | Random winner selection |
| tailored-resume-generator | Resumes | Tailored resume generation |
| ship-learn-next | Planning | Decide what to build/learn |
| tapestry | Documents | Link documents into networks |
| git-pushing | Git | Automate git operations |
| google-workspace-skills | Google apps | Gmail, Calendar, Drive, Docs |
| outline | Wiki | Outline wiki management |

## From gstack

| Command | When | What |
|---------|------|------|
| /retro | Retros | Weekly engineering retro |
| /document-release | Docs | Update docs after release |
| /learn | Memory | Manage learned patterns |

## Intent Mapping

```yaml
organize: Load file-organizer or invoice-organizer
google: Load google-workspace-skills
wiki: Load outline
retro: Load /retro
```
