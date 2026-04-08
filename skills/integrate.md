# Integrate Skills

Skills for integrating with apps — automation, productivity, business.

## App Automation (SaaS Integrations)

From https://github.com/ComposioHQ/awesome-claude-skills — copy skills you need individually:

```bash
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome

# Copy ONLY the ones you need:
cp -r /tmp/awesome/slack-automation .claude/skills/
cp -r /tmp/awesome/github-automation .claude/skills/
cp -r /tmp/awesome/notion-automation .claude/skills/
# ... etc
```

**Available (78+ apps):**

### Project Management
- asana-automation, basecamp-automation, clickup-automation
- jira-automation, linear-automation, monday-automation
- notion-automation, trello-automation

### Communication
- slack-automation, discord-automation, telegram-automation
- whatsapp-automation, microsoft-teams-automation

### Email
- gmail-automation, outlook-automation, sendgrid-automation

### Code & DevOps
- github-automation, gitlab-automation, bitbucket-automation
- vercel-automation, supabase-automation

### Storage
- google-drive-automation, dropbox-automation

### Social Media
- twitter-automation, linkedin-automation, instagram-automation

### E-commerce
- shopify-automation, stripe-automation

## Productivity

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/file-organizer .claude/skills/
cp -r /tmp/awesome/google-workspace-skills .claude/skills/
cp -r /tmp/awesome/tapestry .claude/skills/
```

### From gstack
- `/retro` — Weekly retrospective
- `/document-release` — Update docs
- `/learn` — Manage learned patterns

## Business & Marketing

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/lead-research-assistant .claude/skills/
cp -r /tmp/awesome/content-research-writer .claude/skills/
cp -r /tmp/awesome/twitter-algorithm-optimizer .claude/skills/
```

### Plugins
- **marketing** — `/plugin install marketing`

## Usage

```
Load slack-automation and send a message
Load github-automation and check issues
```
