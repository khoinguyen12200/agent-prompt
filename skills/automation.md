# App Automation Skills

Install these if project needs SaaS app integrations.

## How to Install

**Source:** https://github.com/ComposioHQ/awesome-claude-skills

This is a catalog of 78+ skills. Copy individual skill folders you need:

```bash
# Clone to temp location
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy specific skill folders (examples):
cp -r /tmp/awesome/slack-automation .claude/skills/
cp -r /tmp/awesome/github-automation .claude/skills/
cp -r /tmp/awesome/notion-automation .claude/skills/
```

## Available Automations (78+ apps)

### Project Management
- asana-automation — Asana tasks, projects
- basecamp-automation — Basecamp to-dos, messages
- clickup-automation — ClickUp tasks, lists
- jira-automation — Jira issues, boards
- linear-automation — Linear issues, cycles
- monday-automation — Monday.com boards
- notion-automation — Notion pages, databases
- trello-automation — Trello boards, cards

### Communication
- slack-automation — Slack messages, channels
- discord-automation — Discord messages, servers
- telegram-automation — Telegram messages, groups
- whatsapp-automation — WhatsApp messages
- microsoft-teams-automation — Teams messages

### Email
- gmail-automation — Gmail send/reply, search
- outlook-automation — Outlook emails, folders
- sendgrid-automation — SendGrid campaigns

### Code & DevOps
- github-automation — GitHub issues, PRs, actions
- gitlab-automation — GitLab issues, MRs
- bitbucket-automation — Bitbucket repos, PRs
- vercel-automation — Vercel deployments
- supabase-automation — Supabase SQL, edge functions

### Storage
- google-drive-automation — Drive upload, download
- dropbox-automation — Dropbox files, folders

### Social Media
- twitter-automation — Tweets, search, engagement
- linkedin-automation — LinkedIn posts, profiles
- instagram-automation — Instagram posts, stories
- youtube-automation — YouTube videos, channels

### E-commerce
- shopify-automation — Products, orders, customers
- stripe-automation — Charges, customers, subscriptions

## Usage

After copying a skill folder to `.claude/skills/`, load it:
```
Load slack-automation skill
```
