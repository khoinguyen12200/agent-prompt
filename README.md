# 🚀 Agent Prompt - Claude Code Bootstrap

A bootstrap template for setting up `.claude/` directories with AI-assisted development workflows.

## What This Project Does

This repository provides a `project.example/` folder containing detailed templates for AI agents to create project-specific Claude Code configurations.

## Quick Start

**Step 1:** Clone this repo to temp:

```bash
!rm -rf /tmp/claude-bootstrap && git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/claude-bootstrap
```

**Step 2:** Tell Claude to set up the project:

```
Read /tmp/claude-bootstrap/GUIDE.md and follow the instructions to create the .claude/ directory structure for this project.
```

**Step 3:** Restart Claude Code when done.

## How It Works

1. **GUIDE.md** is the main entry point - it explains everything
2. AI reads GUIDE.md first to understand the structure
3. GUIDE.md instructs AI to read all templates in `project.example/`
4. AI discovers project specifics (tech stack, build commands, etc.)
5. AI creates adapted `.claude/` configuration for this project

## Template Files

All templates are in `project.example/`:

| Template | Creates | Purpose |
|----------|---------|---------|
| `CLAUDE.example.md` | `CLAUDE.md` | Main project instructions |
| `settings.json.example` | `.claude/settings.json` | Team-shared configuration |
| `settings.local.json.example` | `.claude/settings.local.json` | Personal overrides |
| `CLAUDE.local.example.md` | `CLAUDE.local.md` | Private preferences |
| `dot.mcp.json.example` | `.mcp.json` | MCP server configurations (always create) |
| `dot.worktreeinclude.example` | `.worktreeinclude` | Worktree inclusions (always create) |
| `rules/example-rule.example.md` | `.claude/rules/*.md` | Topic/path-scoped rules |
| `skills/example-skill/SKILL.example.md` | `.claude/skills/<name>/SKILL.md` | Reusable workflows |
| `commands/example-command.example.md` | `.claude/commands/*.md` | Quick commands |
| `agents/example-agent.example.md` | `.claude/agents/*.md` | Subagent definitions |
| `agent-memory/example-agent/MEMORY.example.md` | `.claude/agent-memory/<name>/MEMORY.md` | Agent memory |
| `output-styles/example-style.example.md` | `.claude/output-styles/*.md` | Output styles |

## What Gets Created

```
.claude/                        # Project configuration (committed to git)
├── CLAUDE.md                  # Main project instructions
├── settings.json              # Team-shared settings
├── settings.local.json        # Personal overrides (auto-gitignored)
├── rules/                     # Topic-scoped instructions
├── skills/                    # Reusable prompts (/skill-name)
├── commands/                  # Quick single-file skills
├── agents/                    # Subagent definitions
├── agent-memory/              # Subagent persistent memory
└── output-styles/             # Custom output styles

CLAUDE.local.md                # Private preferences (gitignored)
.mcp.json                      # MCP server configs
.worktreeinclude               # Worktree inclusions
```

## Key Features

- **Single entry point** - Just tell AI to read GUIDE.md
- **Instructional templates** - Each template tells AI how to customize
- **Discovery-based** - AI discovers build commands, patterns from project
- **Security-aware** - Settings template emphasizes careful permissions
- **Team-focused** - Clear separation of shared vs personal config

## Verification

After installation, verify with:

```
/memory      # See loaded CLAUDE.md and rules
/skills      # See available skills
/agents      # See configured subagents
/permissions # See current permission rules
/mcp         # See connected MCP servers
```

## Documentation

- **GUIDE.md** - Main guide for AI agents (the entry point)
- **project.example/** - Template files with detailed instructions

## License

MIT
