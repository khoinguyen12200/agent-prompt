# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/` to understand available skills and their install instructions.

## Step 2: Detect Project

Scan current directory to identify technology stack, frameworks, and project needs.

## Step 3: Install Mandatory Skills

Install skills marked as MANDATORY in the skills/ files:

- Read `skills/gstack.md` and install it
- Read `skills/superpowers.md` and install it

## Step 4: Install Optional Skills

Read each remaining file in skills/ and install if the project matches the "When to Install" criteria described in that file.

## Step 5: Generate Rules

Analyze project structure and create `.claude/rules/` files based on detected patterns.

For each detected category:
1. Create a file named `{category}.md` in `.claude/rules/`
2. Add YAML frontmatter with `name:` and `paths:`
3. Document actual conventions found in the codebase
4. Keep under 30 lines

Only create rules where clear patterns exist.

## Step 6: Generate Core Files

Create `.claude/CLAUDE.md` listing:
- Installed mandatory skills
- Installed optional skills
- Intent to skill mapping
- Principles

Create `.claude/settings.json` with UserPromptSubmit hook.

Create `.claude/context.md` with project info.

Create `.claude/intent-map.yaml` mapping intents to skill loading commands.

## Step 7: Copy Skills Reference

Copy skills folder to project:
```bash
cp -r /tmp/claude-bootstrap/skills .claude/
```

## Step 8: Report

Tell user what was installed, what plugins to install after restart, what files were generated, and to restart Claude Code.
