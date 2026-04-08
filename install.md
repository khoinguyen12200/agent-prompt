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

Use AskUserQuestion to let user choose which skills to install.

**First Question - Install Level:**
```
"Select skills to install:
- Install ALL optional skills (recommended)
- Select HIGH priority only
- Select HIGH + MEDIUM priority
- Let me choose individually"
```

**If individual selection, ask by category:**

Ask about HIGH recommended:
```
"High priority skills detected for this project:
[LIST HIGH SKILLS]
Select which to install:"
```

Ask about MEDIUM:
```
"Medium priority skills:
[LIST MEDIUM SKILLS]
Select which to install:"
```

Ask about LOW:
```
"Low priority (specialized) skills:
[LIST LOW SKILLS]
Select which to install:"
```

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

**settings.json:**
```json
{
  "hooks": {
    "UserPromptSubmit": [{
      "matcher": "",
      "hooks": [{
        "type": "command",
        "command": "echo '[Claude] Analyzing prompt to load relevant skills...'"
      }]
    }]
  }
}
```

**context.md:**
- Project info
- Technology stack
- Conventions

**intent-map.yaml:**
```yaml
intents:
  build:
    patterns: [build, create, "new feature", implement]
    action: "Load gstack. Run /office-hours"
  review:
    patterns: [review, "check code", audit]
    action: "Load gstack. Run /review"
  test:
    patterns: [test, qa, verify]
    action: "Load gstack. Run /qa"
  ship:
    patterns: [ship, deploy, release]
    action: "Load gstack. Run /ship"
  debug:
    patterns: [debug, fix, error, bug]
    action: "Load superpowers. Use systematic-debugging"
  refactor:
    patterns: [refactor, cleanup, restructure]
    action: "Load superpowers. Use subagent-driven-development"
  plan:
    patterns: [plan, design, architecture]
    action: "Load superpowers. Use brainstorming"
default: "Use available skills based on context"
```

## Step 9: Report

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
