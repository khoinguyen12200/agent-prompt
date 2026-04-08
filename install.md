# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read All Skills

Read every file in `/tmp/claude-bootstrap/skills/` to understand available skills and their install instructions.

## Step 2: Detect Project

Scan the current project directory:
- List all directories and file patterns
- Identify frameworks from config files
- Note technology stack (React, Vue, Node, Python, etc.)

## Step 3: Install Mandatory Skills

Install these three (marked MANDATORY in their files):

1. **gstack** - Clone to .claude/skills/gstack, run ./setup
2. **superpowers** - Clone to .claude/skills/superpowers  
3. **claude-mem** - Follow memory.md instructions

## Step 4: Categorize Optional Skills

Based on project detection, categorize remaining skills:

**HIGH (Strongly Recommended):**
- Directly matches detected tech stack
- Core to project functionality

**MEDIUM (Useful):**
- Related to project type
- May be needed occasionally

**LOW (Optional):**
- Nice to have
- Specialized use cases

## Step 5: Ask User to Select Skills

Use AskUserQuestion with multi_select: true to let user choose skills.

**First Question - Quick Options:**
Ask: "How would you like to install optional skills?"
Options (single select):
- Install ALL recommended skills (HIGH + MEDIUM)
- Let me select individually by priority

**If individual selection, ask by category with multi_select:**

Ask about HIGH (multi_select: true):
"Select HIGH priority skills to install:"
[LIST HIGH SKILLS AS OPTIONS]

Ask about MEDIUM (multi_select: true):
"Select MEDIUM priority skills to install:"
[LIST MEDIUM SKILLS AS OPTIONS]

Ask about LOW (multi_select: true):
"Select LOW priority (specialized) skills to install:"
[LIST LOW SKILLS AS OPTIONS]

**Alternative - Single Multi-Select:**
Or combine all into one question:
"Select optional skills to install (HIGH = strongly recommended, MEDIUM = useful, LOW = specialized):"
[LIST ALL OPTIONAL SKILLS WITH PRIORITY LABELS]
Use multi_select: true

## Step 6: Install Selected Skills

Install each skill the user selected using instructions from its skills/ file.

## Step 7: Generate Rules

Analyze project and create `.claude/rules/` files based on detected patterns.

## Step 8: Generate Core Files

Create in `.claude/`:

**CLAUDE.md:**
- List all installed skills
- Intent → skill mapping
- Principles

**context.md:**
- Project info
- Technology stack
- Conventions

## Step 8: Report

Tell user what was installed:

```
Bootstrap Complete ✓

Mandatory:
- gstack
- superpowers
- claude-mem

Optional (User Selected):
[LIST INSTALLED OPTIONAL SKILLS]

Generated:
- .claude/CLAUDE.md
- .claude/settings.json
- .claude/context.md
- .claude/intent-map.yaml
- .claude/rules/

Next: Restart Claude Code
```
