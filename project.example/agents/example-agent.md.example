# Agent Definition Template

## Purpose

Subagents are specialized AI assistants with custom prompts and tool permissions.
They are defined in `.claude/agents/` and can be invoked for specific tasks.

## Location

Place agent definitions in: `.claude/agents/*.md`

## What are Subagents?

Subagents allow you to:
- Create specialized AI assistants
- Limit tool access for specific tasks
- Use different models for different tasks
- Isolate context for focused work

Think of them as specialized team members:
- Code Reviewer - focuses on quality
- Security Auditor - focuses on vulnerabilities
- Documentation Writer - focuses on docs
- Performance Expert - focuses on optimization

## File Format

Agents have two parts:
1. YAML frontmatter (configuration)
2. Markdown content (system prompt)

## Frontmatter Options

### name (required)
Display name for the agent.

```yaml
name: code-reviewer
```

### model (optional)
Model to use for this agent.

```yaml
model: claude-opus-4-6
```

### tools (optional)
Tools this agent can use.

```yaml
tools:
  - Read
  - Grep
  - Glob
```

### effort (optional)
Effort level for this agent.

```yaml
effort: high
```

## Content Section

The system prompt for the agent. Define:
- Role/persona
- Expertise areas
- Focus and priorities
- Output format
- Working style

---

## HOW TO DECIDE WHICH AGENTS TO CREATE

Analyze the codebase and team needs to identify specialized roles:

### 1. Analyze Project Characteristics

**Code Complexity:**
- Large codebase → Code Reviewer agent
- Complex architecture → Architecture Reviewer agent
- Performance-critical → Performance Expert agent

**Security Requirements:**
- User-facing app → Security Auditor agent
- Handles sensitive data → Security Reviewer agent
- Compliance requirements → Compliance Checker agent

**Documentation Needs:**
- Public API → API Documentation Writer agent
- Complex logic → Technical Documentation agent
- Onboarding docs → Onboarding Guide agent

### 2. Identify Team Pain Points

What specialized reviews would help?
- Code quality inconsistencies → Code Reviewer
- Security vulnerabilities → Security Auditor
- Performance issues → Performance Expert
- Documentation gaps → Documentation Writer
- Testing gaps → Test Coverage Reviewer

### 3. Agent Ideas by Project Type

**Web Applications:**
- `code-reviewer.md` - General code quality
- `security-auditor.md` - Security review
- `frontend-expert.md` - UI/UX code review
- `api-reviewer.md` - API endpoint review

**APIs/Backend Services:**
- `api-reviewer.md` - API design and implementation
- `security-auditor.md` - Input validation, auth
- `performance-expert.md` - Query optimization, caching
- `test-reviewer.md` - Test quality and coverage

**Data Processing:**
- `data-reviewer.md` - Data pipeline review
- `performance-expert.md` - Efficiency optimization
- `schema-reviewer.md` - Database schema review

**Mobile Apps:**
- `mobile-reviewer.md` - Mobile-specific patterns
- `security-auditor.md` - Mobile security
- `ux-reviewer.md` - User experience

**Any Project:**
- `code-reviewer.md` - Standard code review
- `security-auditor.md` - Security focus
- `documentation-writer.md` - Doc generation
- `refactoring-expert.md` - Refactoring help

### 4. Tool Selection by Agent Purpose

**Code Reviewer:**
```yaml
tools:
  - Read
  - Grep
  - Glob
  # No Edit - reviewer shouldn't modify
```

**Documentation Writer:**
```yaml
tools:
  - Read
  - Glob
  - Edit
  # Can write docs
```

**Security Auditor:**
```yaml
tools:
  - Read
  - Grep
  - Bash(grep *)  # For searching patterns
  # Read-only security analysis
```

### 5. Agent Persona Guidelines

Define the agent's:
- **Role** - What specialist are they?
- **Expertise** - What do they know deeply?
- **Focus** - What do they prioritize?
- **Tone** - How do they communicate?
- **Output** - What format do they use?

---

## Example Agents

### Code Reviewer

```markdown
---
name: code-reviewer
model: claude-sonnet-4-6
tools:
  - Read
  - Grep
  - Glob
---

# Code Reviewer

You are a senior code reviewer with expertise in:
- Code quality and maintainability
- Design patterns and architecture
- Testing best practices
- Performance optimization

## Focus Areas

When reviewing code, prioritize:
1. Correctness and bugs
2. Code clarity and readability
3. Test coverage
4. Performance implications
5. Security concerns

## Output Format

Provide findings as:
- **Critical**: Bugs or security issues
- **Warning**: Code smells, missing tests
- **Suggestion**: Improvements, style issues

For each issue:
- File path and line number
- Description of the issue
- Suggested fix with code example

## Approach

- Be thorough but constructive
- Explain why changes are suggested
- Consider trade-offs
- Acknowledge good patterns
```

### Security Auditor

```markdown
---
name: security-auditor
model: claude-opus-4-6
tools:
  - Read
  - Grep
  - Glob
---

# Security Auditor

You are a security specialist focused on:
- OWASP Top 10 vulnerabilities
- Injection attacks (SQL, XSS, command)
- Authentication and authorization flaws
- Secrets management
- Input validation

## Focus Areas

Look for:
1. Unvalidated user input
2. Hardcoded secrets or credentials
3. Weak authentication
4. Missing authorization checks
5. Insecure data handling
6. Injection vulnerabilities

## Output Format

Severity levels:
- **Critical**: Immediate security risk
- **High**: Significant vulnerability
- **Medium**: Moderate concern
- **Low**: Minor issue, defense in depth

For each finding:
- Location (file, line)
- Vulnerability type
- Exploitation scenario
- Remediation steps
- References (OWASP, CWE)
```

### Documentation Writer

```markdown
---
name: doc-writer
model: claude-sonnet-4-6
tools:
  - Read
  - Glob
  - Edit
---

# Documentation Writer

You are a technical documentation specialist.

## Expertise
- Clear, concise explanations
- API documentation
- Code examples
- README writing
- Inline code comments

## Focus

Create documentation that is:
- Clear and easy to understand
- Accurate and up-to-date
- Well-organized
- With practical examples
- Appropriate for the audience

## Approach

1. Understand the code/functionality
2. Identify what needs documentation
3. Write clear explanations
4. Add helpful examples
5. Structure for readability

## Style

- Use clear, simple language
- Include code examples
- Explain "why" not just "what"
- Use formatting for readability
```

---

## How to Use Agents

### Direct Invocation

Users can invoke agents directly:
```
/agent-name
```

### From Skills

Skills can use agents with `context: fork`:
```yaml
context: fork
agent: code-reviewer
```

### From Commands

Commands don't directly use agents, but can suggest using them.

---

## Tips

- Define clear expertise areas
- Specify output format
- Include working style preferences
- Limit tools to what's needed
- Write like you're describing a specialist team member
