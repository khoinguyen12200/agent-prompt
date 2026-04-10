# CLAUDE.local.md - Personal Project Preferences

## Purpose

This file contains YOUR personal preferences for this specific project.
It loads alongside CLAUDE.md but is NOT shared with the team.

## Location

Place this file at: `./CLAUDE.local.md` (project root)

## Commit Status

❌ DO NOT COMMIT - Add to .gitignore!

This file is for personal use only. Add this line to .gitignore:
```
CLAUDE.local.md
```

## What to Include

### 1. Personal Tool Preferences

Your preferred tools for this project:
- Package manager (npm vs yarn vs pnpm)
- Editor (vim vs VS Code)
- Shell (bash vs zsh vs fish)
- Any personal aliases

**Example:**
```markdown
## My Tools
- Package manager: pnpm (faster than npm)
- Editor: vim
- Shell: zsh with oh-my-zsh
```

### 2. Local Development Setup

Your local development configuration:
- Local database URLs
- Local API endpoints
- Port numbers you use
- Local service URLs

**Example:**
```markdown
## Local Setup
- Main app: http://localhost:3001 (I use 3001 instead of 3000)
- Test DB: postgresql://localhost:5433/testdb
- Redis: localhost:6380
- Local API: http://localhost:8000
```

### 3. Personal Shortcuts and Aliases

Shortcuts you commonly use:
- Git aliases
- Command aliases
- Personal scripts

**Example:**
```markdown
## My Aliases
- `nr` = npm run
- `gcm` = git checkout main
- `gpm` = git pull origin main
- `testw` = npm run test:watch
```

### 4. Personal Workflow Preferences

How you like to work:
- Testing approach
- Debugging preferences
- Commit habits
- Branch naming

**Example:**
```markdown
## My Workflow
- I prefer to write tests first (TDD)
- I like small, frequent commits
- My branch naming: feature/description or fix/description
- I use --no-verify sometimes to skip pre-commit hooks when iterating
```

### 5. Personal Overrides

Override team settings for your workflow:
- Different test commands
- Different build approaches
- Personal workarounds

**Example:**
```markdown
## Overrides
- I use `npm run test:fast` instead of full test suite locally
- I skip integration tests locally (run in CI only)
- I use a different docker-compose file for local dev
```

### 6. Notes to Self

Things you forget or want to remember:
- Common debugging steps
- Useful queries
- Gotchas you've encountered

**Example:**
```markdown
## Notes
- If tests fail with "connection refused", check if Docker is running
- The staging API key is in 1Password under "Project Staging"
- Run `source .env.local` before starting the server
- Database migrations need to run in the docker container: docker-compose exec app npm run migrate
```

## How This Differs from CLAUDE.md

| CLAUDE.md | CLAUDE.local.md |
|-----------|-----------------|
| Team-shared | Personal only |
| Project standards | Personal preferences |
| Committed to git | Gitignored |
| Everyone sees it | Only you see it |
| Stable, agreed-upon | Your personal workflow |

## Example Complete File

```markdown
# My Personal Preferences

## Tools
- Package manager: pnpm
- Editor: VS Code with Vim extension
- Terminal: iTerm2 with zsh

## Local Setup
- App runs on http://localhost:3001
- Test database: postgresql://localhost:5433/test
- Redis: localhost:6380

## Aliases I Use
- `nr` = npm run
- `gcm` = git checkout main
- `gst` = git status
- `npm-dev` = pnpm run dev

## My Workflow
- Prefer TDD when possible
- Small commits with descriptive messages
- Use `git add -p` to review changes before committing
- Run lint before every commit

## Useful Commands
- Reset everything: pnpm clean && pnpm install && pnpm migrate
- Debug mode: pnpm dev:debug
- Quick test: pnpm test:unit (faster than full suite)

## Notes
- Docker needs at least 4GB RAM allocated
- The seed script takes about 2 minutes to run
- Staging URL: https://staging.example.com
```

## Setup Instructions

1. Copy this template to `./CLAUDE.local.md`
2. Add `CLAUDE.local.md` to `.gitignore`:
   ```bash
   echo "CLAUDE.local.md" >> .gitignore
   ```
3. Customize with your preferences
4. Restart Claude Code to load it

## Tips

- Keep it concise - this is quick reference for you
- Update it as your preferences change
- Include things you look up repeatedly
- Use it as a personal cheat sheet
- No need to be formal - this is just for you
