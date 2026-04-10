# Agent Memory Template

## Purpose

Agent memory provides persistent storage for subagents across sessions.
Files in `.claude/agent-memory/<agent-name>/` are read by that specific agent
to maintain context between conversations.

## Location

Place memory files in: `.claude/agent-memory/<agent-name>/`

The `<agent-name>` should match the name of an agent defined in `.claude/agents/`.

## What is Agent Memory?

Unlike CLAUDE.md (which is loaded for all sessions), agent memory is:
- Specific to a particular subagent
- Written and read by that agent
- Persistent across sessions
- For notes the agent takes about its work

## Directory Structure

```
.claude/agent-memory/
└── <agent-name>/
    ├── MEMORY.md          # Main memory index
    ├── context.md         # Additional context
    └── notes/             # Other notes files
        └── *.md
```

## MEMORY.md Content

The MEMORY.md file acts as an index. It should include:

1. **Agent Purpose** - What this agent does
2. **Key Learnings** - Patterns discovered
3. **Preferences** - User preferences for this agent
4. **Reference Info** - Useful reference material
5. **File Index** - Links to other memory files

---

## HOW TO DECIDE WHICH AGENTS NEED MEMORY

Analyze which agents would benefit from persistence:

### 1. Identify Learning Agents

Which agents should remember things?
- **Code Reviewer** - Common issues, team patterns
- **Security Auditor** - Vulnerabilities found, patterns
- **Documentation Writer** - Style preferences, templates
- **Architecture Advisor** - Design decisions, patterns

### 2. Identify Reference Needs

Which agents need reference material?
- **Complex domains** - Business logic, domain terms
- **Large codebases** - Architecture overview, key files
- **Evolving projects** - Recent changes, migrations

### 3. Agent Memory Ideas by Type

**Code Reviewer Agent:**
- Common mistakes in this codebase
- Team-specific patterns
- User preferences for feedback style
- Reference to style guides

**Security Auditor Agent:**
- Previously found vulnerabilities
- Security-sensitive files
- Compliance requirements
- Security patterns used

**Documentation Writer Agent:**
- Documentation templates
- Style preferences
- Glossary of terms
- Common sections needed

**Performance Expert Agent:**
- Known bottlenecks
- Performance patterns
- Benchmark baselines
- Optimization history

**Architecture Advisor Agent:**
- Design decisions
- Architecture patterns
- Tech stack rationale
- Migration plans

### 4. When NOT to Create Memory

Don't create memory for:
- Simple agents that don't need persistence
- One-time use agents
- Agents where CLAUDE.md suffices
- Temporary or experimental agents

### 5. Memory Content Guidelines

Memory should include:
- **Index** - Overview of what's in memory
- **Learnings** - Things discovered over time
- **Preferences** - User preferences
- **Reference** - Useful links and context
- **Notes** - Additional detail files

---

## Example MEMORY.md

```markdown
# Code Reviewer Agent Memory

## Purpose
This agent specializes in code review for this codebase.

## Learnings

### Code Patterns
- Team prefers async/await over callbacks
- Error handling uses custom AppError class
- Tests use describe/it pattern with expect

### Common Issues
- Often missing await on async calls
- Sometimes forget to update type definitions
- Tests sometimes don't clean up mocks

### Preferences
- User prefers detailed explanations
- User wants security issues flagged immediately
- User likes suggestions with code examples

## Reference
- Style guide: @docs/style-guide.md
- Architecture: @docs/architecture.md

## Other Files
- Detailed patterns: patterns.md
- Security checklist: security.md
```

---

## How It Works

1. Agent is invoked (e.g., `/code-reviewer`)
2. Claude loads the agent definition from `.claude/agents/code-reviewer.md`
3. Claude also loads `.claude/agent-memory/code-reviewer/MEMORY.md`
4. The memory provides additional context specific to that agent
5. The agent can write updates to its memory during the session

---

## Creating Initial Memory

When setting up agent memory:

1. Create the directory: `.claude/agent-memory/<agent-name>/`
2. Create MEMORY.md with initial structure
3. Include reference to agent's purpose
4. Add any known patterns or preferences
5. Leave room for the agent to add learnings

---

## Maintenance

Agent memory evolves:
- Agents may write to their memory during sessions
- Humans can edit memory files directly
- Review periodically for outdated information
- Keep it organized as it grows

---

## Tips

- Start with basic structure, let agent fill in details
- Include file references for additional context
- Keep it focused on what that specific agent needs
- Use it to capture institutional knowledge
- Cross-reference other documentation
- Only create for agents that truly need persistence
