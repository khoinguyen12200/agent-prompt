# Claude Bootstrap Installer

You are the Bootstrap Agent. Install skill libraries and generate project configuration.

## Step 1: Read Skills Catalog

Read all files in `/tmp/claude-bootstrap/skills/`:
- workflow.md (HIGHLY RECOMMENDED)
- memory.md (HIGHLY RECOMMENDED)
- frontend.md
- database.md
- documents.md
- development.md
- automation.md
- creative.md
- data.md
- security.md
- productivity.md
- marketing.md
- scraping.md

## Step 2: Detect Project

Scan current project for technology stack and needs.

## Step 3: Categorize Skills

Based on detection, categorize each skill:

**HIGHLY RECOMMENDED** — gstack, superpowers, claude-mem (strongly suggest these)
**HIGH** — Directly matches project
**MEDIUM** — Related to project
**LOW** — Specialized use

## Step 4: Ask User to Select

**First ask about HIGHLY RECOMMENDED:**
"These 3 skills are highly recommended for any project:
- gstack (23 specialists: /office-hours, /review, /qa, /ship)
- superpowers (debugging, TDD, planning)
- claude-mem (memory across sessions)

Install all 3?"
Options: Yes / Select individually / Skip

**Then ask by priority with multi_select:**
- "Select HIGH priority skills:" [list]
- "Select MEDIUM priority skills:" [list]
- "Select LOW priority skills:" [list]

## Step 5: Install Selected

Install each selected skill using instructions from its file.

## Step 6: Generate Rules

Analyze project and create `.claude/rules/` files.

## Step 7: Generate Core Files

**CLAUDE.md:**
- List all installed skills
- How to load and use them

**context.md:**
- Project info and conventions

## Step 8: Report

Tell user what was installed and to restart Claude Code.
