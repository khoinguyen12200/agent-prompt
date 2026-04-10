# SKILL.md Template

## Purpose

Skills are reusable workflows invoked with `/skill-name`. They provide
step-by-step instructions for common tasks.

## Location

Place skills in: `.claude/skills/<skill-name>/SKILL.md`

## Directory Structure

```
.claude/skills/<skill-name>/
├── SKILL.md          # Main instructions (REQUIRED)
├── template.md       # Template for Claude to fill (optional)
├── examples/         # Example outputs (optional)
└── scripts/          # Utility scripts (optional)
```

## File Format

Skills have two parts:
1. YAML frontmatter (configuration)
2. Markdown content (instructions)

## Frontmatter Options

### name (optional)
Display name for the skill. Defaults to directory name.

```yaml
name: deploy-app
```

### description (recommended)
What this skill does. Used by Claude to decide when to use it.
Keep under 250 characters.

```yaml
description: Deploy the application to production after running tests
```

### disable-model-invocation (optional)
Set to `true` to prevent Claude from auto-triggering this skill.
Use for workflows you want to control manually.

```yaml
disable-model-invocation: true
```

### user-invocable (optional)
Set to `false` to hide from `/` menu. Only Claude can invoke it.

```yaml
user-invocable: false
```

### allowed-tools (optional)
Pre-approve tools for this skill.

```yaml
allowed-tools: Bash(git *) Bash(docker *) Read
```

### context (optional)
Set to `fork` to run in isolated subagent.

```yaml
context: fork
```

### agent (optional)
Specify subagent type when using `context: fork`.

```yaml
context: fork
agent: Explore
```

### paths (optional)
Auto-load when working with matching files.

```yaml
paths:
  - "src/api/**/*.ts"
```

### model (optional)
Override model for this skill.

```yaml
model: claude-opus-4-6
```

### effort (optional)
Set effort level.

```yaml
effort: high
```

## Content Section

The markdown content is the actual instructions. Use:

### Argument Substitution

- `$ARGUMENTS` - All arguments passed
- `$ARGUMENTS[0]` or `$0` - First argument
- `$ARGUMENTS[1]` or `$1` - Second argument

Example:
```markdown
Deploy $ARGUMENTS to production.
```

### Shell Injection

Dynamic content from commands:

```markdown
Current branch: !`git branch --show-current`
```

Multi-line:
````markdown
```!
git status
git log --oneline -3
```
````

---

## HOW TO DECIDE WHICH SKILLS TO CREATE

Analyze the codebase and identify repetitive workflows:

### 1. Identify Repetitive Workflows

Look for tasks that happen repeatedly:
- **Deployment** - Steps to deploy to staging/production
- **Code review** - PR review process
- **Testing** - Running specific test suites
- **Refactoring** - Common refactoring patterns
- **Setup** - Onboarding new developers
- **Release** - Release process steps

### 2. Analyze Project Lifecycle

What workflows exist in different phases?
- **Development** - Starting new features, debugging
- **Testing** - Running tests, checking coverage
- **Review** - PR preparation, code review
- **Deployment** - Staging deploy, production deploy
- **Maintenance** - Dependency updates, cleanup

### 3. Skill Ideas by Project Type

**Node.js Projects:**
- `commit` - Commit with pre-commit checks
- `deploy` - Deploy to Vercel/Netlify/AWS
- `release` - Version bump, changelog, tag
- `pr` - Create PR with template
- `test-e2e` - Run end-to-end tests
- `update-deps` - Update dependencies safely

**Python Projects:**
- `commit` - Commit with linting
- `deploy` - Deploy to production
- `migrate` - Database migration workflow
- `test-coverage` - Run tests with coverage report
- `release` - Build and publish to PyPI
- `setup-env` - Setup virtual environment

**Rust Projects:**
- `commit` - Commit with cargo check
- `release` - Build release binaries
- `publish` - Publish to crates.io
- `bench` - Run benchmarks
- `audit` - Run security audit

**Mobile Apps:**
- `build-ios` - Build iOS app
- `build-android` - Build Android app
- `deploy-beta` - Deploy to TestFlight/Play Console
- `screenshots` - Generate app screenshots

**Any Project:**
- `commit` - Smart commit workflow
- `pr-review` - Review pull request
- `fix-issue` - Fix GitHub issue
- `add-feature` - Add new feature template
- `refactor` - Refactoring workflow

### 4. Determine Invocation Style

**Manual-only** (disable-model-invocation: true):
- Deployment
- Commits
- Destructive operations
- External notifications

**Auto-invocation** (default):
- Code explanation
- Reference lookups
- Background assistance

### 5. Skill Content Guidelines

Each skill should have:
- Clear purpose statement
- Step-by-step workflow
- Error handling
- Expected outcomes
- Prerequisites (if any)

---

## Example Skills

### Simple Skill (Manual Trigger)

```markdown
---
name: commit
description: Stage and commit changes
disable-model-invocation: true
---

# Commit Changes

Stage all changes and commit with message: $ARGUMENTS

1. Run `git add -A`
2. Run `git commit -m "$ARGUMENTS"`
3. Show commit summary
```

### Research Skill (Forked)

```markdown
---
name: deep-research
description: Research a topic thoroughly
context: fork
agent: Explore
---

# Research Task

Research $ARGUMENTS thoroughly:

1. Find relevant files using Glob and Grep
2. Read and analyze the code
3. Identify patterns and relationships
4. Summarize findings with specific file references

Focus on:
- Implementation details
- Edge cases
- Related functionality
```

### Dynamic Context Skill

```markdown
---
name: pr-summary
description: Summarize a pull request
context: fork
agent: Explore
---

# PR Summary

## Context
PR: $ARGUMENTS

## Data
- Diff: !`gh pr diff $ARGUMENTS`
- Files: !`gh pr diff --name-only $ARGUMENTS`
- Comments: !`gh pr view --comments $ARGUMENTS`

## Task
Summarize this PR focusing on:
1. What changed
2. Why it changed
3. Potential issues
4. Testing considerations
```

---

## When to Create a Skill

Create a skill when:
- You repeat the same workflow multiple times
- A process has multiple steps
- You want to standardize a procedure
- You want to delegate a task to a subagent

Don't create a skill when:
- It's a one-time task
- It's simple enough to type directly
- It changes frequently

---

## Tips

- Write clear descriptions for discoverability
- Use disable-model-invocation for destructive operations
- Pre-approve tools to reduce prompts
- Use fork for complex or isolated tasks
- Include error handling steps
- Reference project conventions from CLAUDE.md
