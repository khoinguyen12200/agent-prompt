# Command File Template

## Purpose

Commands are single-file skills - simpler than the full skills/ directory structure.
They live in `.claude/commands/` and work like quick shortcuts.

## Location

Place command files in: `.claude/commands/*.md`

## Difference from Skills

| Skills | Commands |
|--------|----------|
| Directory structure | Single file |
| Can have supporting files | Just the .md file |
| Complex workflows | Quick actions |
| `.claude/skills/name/SKILL.md` | `.claude/commands/name.md` |

Use commands for simple, single-purpose actions.
Use skills for complex workflows that might need templates/examples/scripts.

## File Format

Commands have the same format as skills:
1. YAML frontmatter (configuration)
2. Markdown content (instructions)

## Frontmatter Options

Same as skills:
- `description` - What this command does
- `disable-model-invocation` - Manual trigger only
- `allowed-tools` - Pre-approved tools
- `model` - Override model
- `effort` - Set effort level

## Content Section

The instructions - what to do when this command is invoked.

---

## HOW TO DECIDE WHICH COMMANDS TO CREATE

Analyze the codebase and identify frequently-needed quick actions:

### 1. Discover Common Commands

Look for patterns in:
- **package.json scripts** - Which scripts run most often?
- **Makefile targets** - Common development tasks?
- **Developer workflow** - What do developers type repeatedly?
- **Documentation** - README mentions common commands?

### 2. Identify Quick Status Needs

What status information would be useful?
- Git status overview
- Build status
- Test status
- Dependency status
- Server health

### 3. Identify Quick Action Needs

What simple actions happen frequently?
- Clean build artifacts
- Reset database
- Restart server
- Run quick checks

### 4. Command Ideas by Project Type

**Node.js Projects:**
- `status.md` - Git status + npm outdated
- `clean.md` - Clean node_modules/.cache
- `lint.md` - Run linter with auto-fix
- `test-changed.md` - Test only changed files
- `deps-check.md` - Check for outdated dependencies

**Python Projects:**
- `status.md` - Git status + pip list outdated
- `clean.md` - Clean __pycache__, .pyc files
- `lint.md` - Run flake8/black
- `test.md` - Run pytest with coverage
- `venv-check.md` - Verify virtualenv status

**Rust Projects:**
- `status.md` - Git status + cargo tree overview
- `clean.md` - Cargo clean
- `check.md` - Cargo check (fast compilation check)
- `fmt.md` - Cargo fmt
- `clippy.md` - Run clippy lints

**Docker Projects:**
- `status.md` - Container status
- `clean.md` - Remove stopped containers, dangling images
- `rebuild.md` - Rebuild containers
- `logs.md` - Show recent logs

**Any Project:**
- `status.md` - Overall project status
- `todo.md` - Find TODOs in code
- `stats.md` - Project statistics (lines of code, files, etc.)
- `pr-ready.md` - Check if branch is ready for PR

### 5. Naming Conventions

Name files descriptively:
- `status.md` - Show project status
- `clean.md` - Clean build artifacts
- `lint.md` - Run linter
- `test-quick.md` - Run quick tests
- `deps-check.md` - Check dependencies
- `setup-check.md` - Verify local setup

### 6. Command Content Guidelines

Each command should:
- Do ONE thing well
- Be immediately useful
- Save typing/common operations
- Have a clear, descriptive name
- Include helpful output formatting

---

## Example Commands

### Status Command

```markdown
---
description: Show project status
---

Show current project status:

1. Git status
2. Recent commits (last 5)
3. Any uncommitted changes
4. Current branch
```

### Lint Command

```markdown
---
description: Run linter and fix issues
disable-model-invocation: true
---

Run the linter and auto-fix issues:

1. Run `npm run lint`
2. If errors found, run `npm run lint:fix`
3. Show summary of changes
```

### Clean Command

```markdown
---
description: Clean build artifacts
---

Clean build artifacts and dependencies:

1. Remove node_modules/.cache
2. Remove dist/ or build/
3. Remove .tmp files
4. Show disk space freed
```

---

## Tips

- Keep instructions concise
- Use for frequently run actions
- Name clearly for discoverability
- Consider disabling auto-invocation for side effects
- Use argument substitution if needed ($ARGUMENTS)
- Reference CLAUDE.md for project-specific details
