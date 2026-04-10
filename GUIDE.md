# Claude Code Project Setup Guide

This guide instructs AI agents on how to set up the `.claude/` directory structure in any project.

## Quick Start for AI Agents

**Your task**: Read this guide, then read all template files in `project.example/`, and create the `.claude/` directory structure adapted for this project.

### Step-by-Step Process

1. **Read this guide** (GUIDE.md) - Understand the overall structure
2. **Read all templates** in `project.example/` - Understand each file's purpose
3. **Explore the project** - Discover technology stack, build commands, patterns
4. **Create directories** - Set up `.claude/` structure
5. **Create adapted files** - Customize each file for this project
6. **Update .gitignore** - Add Claude-specific files
7. **Report completion** - Tell user what was created and what to customize

---

## Template Files Location

All templates are in `project.example/`:

```
project.example/
├── CLAUDE.example.md                    # Main project instructions
├── CLAUDE.local.example.md              # Private preferences template
├── settings.json.example                # Team-shared configuration
├── settings.local.json.example          # Personal overrides
├── dot.mcp.json.example                 # MCP server configurations
├── dot.worktreeinclude.example          # Worktree inclusions
├── rules/
│   └── example-rule.example.md          # Topic-scoped rules
├── skills/
│   └── example-skill/
│       └── SKILL.example.md             # Reusable workflows
├── commands/
│   └── example-command.example.md       # Quick commands
├── agents/
│   └── example-agent.example.md         # Subagent definitions
├── agent-memory/
│   └── example-agent/
│       └── MEMORY.example.md            # Agent persistent memory
└── output-styles/
    └── example-style.example.md         # Output styles
```

**Action**: Read each `.example` file to understand what to create.

---

## Project Discovery Checklist

Before creating files, discover:

### Technology Stack
- [ ] Primary language(s) - check file extensions
- [ ] Framework - React, Express, Django, etc.
- [ ] Runtime - Node.js, Python, Rust, Go, etc.
- [ ] Package manager - npm, yarn, pnpm, pip, cargo, etc.

### Build System
- [ ] Build command - check package.json scripts, Makefile, etc.
- [ ] Test command - how to run tests
- [ ] Lint command - how to run linting
- [ ] Dev server command - how to start locally

### Project Structure
- [ ] Source directory - src/, lib/, app/, etc.
- [ ] Test directory - tests/, __tests__, spec/, etc.
- [ ] Configuration files - where configs live
- [ ] Entry points - main files

### Coding Standards
- [ ] Linter config - .eslintrc, .pylintrc, etc.
- [ ] Formatter config - .prettierrc, .editorconfig
- [ ] Style guide - any documented conventions
- [ ] Existing patterns - check sample code

### Security Considerations
- [ ] Secret files - .env, credentials, keys
- [ ] Sensitive directories - where secrets live
- [ ] Safe commands - what can be auto-approved
- [ ] Dangerous commands - what should be blocked

---

## Directory Structure to Create

Create this structure in the project:

```
.claude/                        # Project configuration (committed to git)
├── CLAUDE.md                  # Main project instructions
├── settings.json              # Team-shared settings
├── settings.local.json        # Personal overrides (auto-gitignored)
├── rules/                     # Topic-scoped instructions (*.md files)
├── skills/                    # Reusable prompts (/skill-name)
│   └── <name>/
│       ├── SKILL.md          # Main skill file
│       ├── template.md       # Optional template
│       ├── examples/         # Optional examples
│       └── scripts/          # Optional scripts
├── commands/                  # Quick single-file skills (*.md files)
├── agents/                    # Subagent definitions (*.md files)
├── agent-memory/              # Subagent persistent memory
│   └── <name>/
│       └── MEMORY.md         # Agent memory index
└── output-styles/             # Custom output styles (*.md files)

CLAUDE.local.md                # Private preferences (add to .gitignore!)
.mcp.json                      # MCP server configs (always create)
.worktreeinclude               # Worktree inclusions (always create)
```

---

## File Creation Guide

### 1. CLAUDE.md

**Location**: `./CLAUDE.md` OR `./.claude/CLAUDE.md`
**Commit**: ✅ Yes

**What to include**:
- Project overview (discover from README, package.json)
- Build commands (discover from scripts, Makefile)
- Coding standards (discover from linter configs, existing code)
- Architecture (discover from directory structure)
- Testing approach (discover from test configs)

**Read template**: `project.example/CLAUDE.example.md`

---

### 2. settings.json

**Location**: `./.claude/settings.json`
**Commit**: ✅ Yes

**What to configure**:
- **allow**: Safe, frequently-used commands
  - Git read operations (status, log, diff)
  - Build commands (npm run build, make)
  - Test commands (npm test, pytest)
  - Lint commands (npm run lint)

- **deny**: Sensitive files and dangerous operations
  - Secret files (.env, credentials)
  - Destructive commands

- **ask**: Operations with side effects
  - Git push
  - File deletion
  - Network requests

- **env**: Project environment variables

**Read template**: `project.example/settings.json.example`

**Security**: Be conservative. Start restrictive.

---

### 3. settings.local.json

**Location**: `./.claude/settings.local.json`
**Commit**: ❌ No (auto-gitignored)

**What to include**: Empty template for personal overrides

**Read template**: `project.example/settings.local.json.example`

---

### 4. CLAUDE.local.md

**Location**: `./CLAUDE.local.md`
**Commit**: ❌ No (must add to .gitignore)

**What to include**: Template explaining it's for personal preferences

**Read template**: `project.example/CLAUDE.local.example.md`

**Action**: Also add `CLAUDE.local.md` to `.gitignore`

---

### 5. Rules Directory

**Location**: `./.claude/rules/*.md`
**Commit**: ✅ Yes

**Create files based on project needs**:
- `testing.md` - Testing standards
- `security.md` - Security guidelines
- `api-design.md` - API conventions
- Language/framework specific rules

**Use path scoping** when rules only apply to certain files:
```yaml
---
paths:
  - "src/api/**/*.ts"
---
```

**Read template**: `project.example/rules/example-rule.example.md`

---

### 6. Skills Directory

**Location**: `./.claude/skills/<name>/SKILL.md`
**Commit**: ✅ Yes

**Create skills for common workflows**:
- Commit workflow
- PR review
- Deployment
- Testing routines
- Code generation

**Each skill needs**:
- Frontmatter with configuration
- Clear description
- Step-by-step instructions
- Argument placeholders if needed ($ARGUMENTS)

**Read template**: `project.example/skills/example-skill/SKILL.example.md`

---

### 7. Commands Directory

**Location**: `./.claude/commands/*.md`
**Commit**: ✅ Yes

**Create simple commands for**:
- Status checks
- Quick actions
- Common queries

**Simpler than skills** - single file, no supporting files.

**Read template**: `project.example/commands/example-command.example.md`

---

### 8. Agents Directory

**Location**: `./.claude/agents/*.md`
**Commit**: ✅ Yes

**Create specialized agents**:
- Code reviewer
- Security auditor
- Documentation writer
- Performance expert

**Each agent needs**:
- Name and model (optional)
- Tool permissions
- System prompt defining persona

**Read template**: `project.example/agents/example-agent.example.md`

---

### 9. Agent Memory Directory

**Location**: `./.claude/agent-memory/<agent-name>/MEMORY.md`
**Commit**: ✅ Yes

**Create memory for agents that need persistence**:
- Index of learnings
- Reference material
- Preferences

**Read template**: `project.example/agent-memory/example-agent/MEMORY.example.md`

---

### 10. Output Styles Directory

**Location**: `./.claude/output-styles/*.md`
**Commit**: ✅ Yes

**Create styles if needed**:
- terse - Minimal responses
- explanatory - Detailed explanations
- technical - Precise terminology

**Read template**: `project.example/output-styles/example-style.example.md`

---

### 11. MCP Configuration (.mcp.json)

**Location**: `./.mcp.json`
**Commit**: ✅ Yes

MCP server configurations for team-shared integrations.

**Always create this file** - even if empty. It serves as documentation
of available MCP integrations and can be populated as needed.

**What to include**:
- GitHub integration (if project uses GitHub)
- Database connections (if team shares DB access)
- Other shared integrations

**If no MCP servers needed yet**: Create with empty `mcpServers` object
and comments explaining what can be added.

**Read template**: `project.example/dot.mcp.json.example`

---

### 12. Worktree Configuration (.worktreeinclude)

**Location**: `./.worktreeinclude`
**Commit**: ✅ Yes

Gitignored files to copy to new git worktrees.

**Always create this file** - even if just a template with comments.
This documents which files should exist in all worktrees.

**What to include**:
- `.env.example` - Environment template
- `docker-compose.override.yml.example` - Docker config template
- Any other `.example` files developers need to copy

**If no templates exist yet**: Create with comments explaining what
should be listed when templates are added.

**Read template**: `project.example/dot.worktreeinclude.example`

---

## Gitignore Updates

Ensure `.gitignore` includes:

```
# Claude Code local files
CLAUDE.local.md
.claude/settings.local.json
```

If `.gitignore` doesn't exist, create it with these entries.

---

## Completion Checklist

After creating all files:

- [ ] `.claude/` directory exists with all subdirectories
- [ ] `CLAUDE.md` has project-specific content
- [ ] `settings.json` has appropriate permissions
- [ ] `settings.local.json` exists (can be empty)
- [ ] `CLAUDE.local.md` exists with explanation
- [ ] `.gitignore` updated with Claude files
- [ ] Rules created for relevant topics
- [ ] Skills created for common workflows
- [ ] Example agents created
- [ ] `.mcp.json` created (can be empty template)
- [ ] `.worktreeinclude` created (can be empty template)

---

## User Instructions

After setup, tell the user:

1. **Review the created files** - Especially CLAUDE.md and settings.json
2. **Customize as needed** - Add project-specific details
3. **Restart Claude Code** - To load the new configuration
4. **Verify with commands**:
   - `/memory` - Check CLAUDE.md loaded
   - `/skills` - See available skills
   - `/permissions` - Review permission rules
5. **Add personal preferences** to `CLAUDE.local.md`

---

## Reference: File Commit Status

| File | Commit | Notes |
|------|--------|-------|
| `.claude/CLAUDE.md` | ✅ | Main instructions |
| `.claude/settings.json` | ✅ | Team settings |
| `.claude/settings.local.json` | ❌ | Auto-gitignored |
| `.claude/rules/*.md` | ✅ | Topic rules |
| `.claude/skills/*/` | ✅ | Reusable skills |
| `.claude/commands/*.md` | ✅ | Quick commands |
| `.claude/agents/*.md` | ✅ | Subagents |
| `.claude/agent-memory/*/` | ✅ | Agent memory |
| `.claude/output-styles/*.md` | ✅ | Output styles |
| `CLAUDE.local.md` | ❌ | Add to .gitignore |
| `.mcp.json` | ✅ | MCP configs |
| `.worktreeinclude` | ✅ | Worktree files |

---

## Additional Resources

- Official Docs: https://code.claude.com/docs/
- JSON Schema: https://json.schemastore.org/claude-code-settings.json
