# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/` to understand available skills. Each file contains:
- **Official** skills from Anthropic
- **Community** skills from awesome-claude-skills
- **Plugins** from Claude marketplace

## Step 2: Detect Project

Scan the current project directory for:
- Technology stack (React, Vue, Node, Python, etc.)
- File patterns and frameworks
- Existing .claude/ configuration

## Step 3: Install Mandatory Skills

Install these three (marked MANDATORY):

1. **gstack** — Clone to .claude/skills/gstack, run ./setup
2. **superpowers** — Clone to .claude/skills/superpowers  
3. **claude-mem** — Follow memory.md instructions

## Step 4: Categorize Optional Skills

Based on project detection, categorize skills from the skills/ files:

**HIGH** — Directly matches detected tech stack  
**MEDIUM** — Related to project type  
**LOW** — Nice to have, specialized

## Step 5: Ask User to Select

Use AskUserQuestion with multi_select:

**Option 1:** "Install ALL recommended (HIGH + MEDIUM)"  
**Option 2:** "Select individually"

If individual, ask by priority with multi_select for each.

## Step 6: Install Selected

For each selected skill, follow its install instructions from the skills/ file:
- Official skills: plugin install or git clone
- Community skills: copy individual folder from awesome-claude-skills
- Plugins: /plugin install

## Step 7: Generate Rules

Analyze project and create `.claude/rules/` files for detected patterns.

## Step 8: Generate Core Files

**CLAUDE.md:**
- List installed mandatory skills
- List installed optional skills  
- Usage instructions

**context.md:**
- Project info, tech stack, conventions

## Step 9: Report

Tell user what was installed and to restart Claude Code.
