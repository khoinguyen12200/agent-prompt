# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/` to understand available skills.

## Step 2: Detect Project

Scan current project for:
- Technology stack (React, Vue, Node, Python, etc.)
- File patterns and frameworks
- Existing .claude/ configuration

## Step 3: Organize Skills for User

Categorize all skills into:

**Highly Recommended:**
- gstack, superpowers, claude-mem

**Detected for Project:**
- Skills matching detected tech stack

**Available:**
- All other skills

## Step 4: Ask User

Present organized skills and ask:

"Select skills to install:"

**Option 1:** Install ALL (180+ skills)

**Option 2:** Install Recommended + Detected (highly recommended + skills matching your project)

**Option 3:** Select Manually (show organized list with multi_select)

If Option 3, show:
- Highly Recommended (multi_select)
- Detected for Project (multi_select)
- Other Skills (multi_select)

## Step 5: Install Selected

Install each selected skill using instructions from its skills/ file.

## Step 6: Generate Rules

Analyze project and create `.claude/rules/` files.

## Step 7: Generate Core Files

**CLAUDE.md:**
- List installed skills
- How to load and use them

**context.md:**
- Project info and conventions

## Step 8: Report

Tell user what was installed and to restart Claude Code.
