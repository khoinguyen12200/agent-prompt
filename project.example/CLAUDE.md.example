# CLAUDE.md - Project Instructions

## Purpose

This file contains instructions that Claude Code reads at the start of every session for this project. It provides persistent context about how to work with this codebase.

## Location

Place this file at either:
- `./CLAUDE.md` (project root)
- `./.claude/CLAUDE.md` (inside .claude directory)

Both locations work - use whichever you prefer. The file inside `.claude/` keeps all Claude config in one place.

## What to Include

### 1. Project Overview (REQUIRED)

Provide a brief description of what this project does:
- Primary purpose/functionality
- Technology stack (languages, frameworks, databases)
- Architecture pattern (monolith, microservices, serverless, etc.)

**How to discover this:**
- Read README.md
- Check package.json, Cargo.toml, pyproject.toml, etc.
- Look at the main entry points
- Check directory structure

### 2. Build Commands (REQUIRED)

Document how to:
- Build the project
- Run tests
- Run linting/formatting
- Start development server
- Run type checking

**How to discover this:**
- Check package.json "scripts" section
- Check Makefile
- Check build.gradle, pom.xml, etc.
- Check Dockerfile
- Look at CI/CD configuration (.github/workflows/, .gitlab-ci.yml)
- Check justfile, taskfile.yml

**Example formats:**
```
## Build Commands
- Build: npm run build
- Test: npm test
- Lint: npm run lint
- Dev server: npm run dev
- Type check: npm run type-check
```

### 3. Coding Standards (REQUIRED)

Document project-specific conventions:
- Naming conventions (camelCase, PascalCase, snake_case, kebab-case)
- Indentation and formatting (spaces vs tabs, width)
- Import organization (grouping, ordering)
- File organization (where different types of files live)
- Error handling patterns
- Comment style and requirements

**How to discover this:**
- Check .editorconfig
- Check prettier.config, .prettierrc
- Check eslint config, .eslintrc
- Check existing code patterns
- Look for CONTRIBUTING.md
- Check style guide docs

### 4. Architecture (RECOMMENDED)

Describe the project structure:
- Main directories and their purposes
- Where source code lives
- Where tests live
- Where configuration lives
- Key architectural patterns (MVC, layered, clean architecture, etc.)
- External integrations and APIs

**How to discover this:**
- Explore the directory tree
- Read architecture docs
- Check README sections
- Look at import patterns in code

### 5. Testing Standards (RECOMMENDED)

Document testing approach:
- Testing framework used
- Test file location and naming
- Required coverage levels
- Types of tests (unit, integration, e2e)
- Test data management
- Mocking approach

**How to discover this:**
- Check test config files (jest.config, vitest.config, pytest.ini)
- Look at existing test files
- Check CI test commands

### 6. Common Workflows (OPTIONAL)

Document frequently needed procedures:
- How to add a new feature
- How to create a database migration
- Deployment process
- Debugging procedures
- How to run locally

## Writing Tips

### Be Specific and Concrete

**BAD:** "Format code properly"
**GOOD:** "Use 2-space indentation" or "Run npm run format before committing"

**BAD:** "Keep files organized"
**GOOD:** "API handlers live in src/api/handlers/"

**BAD:** "Test your changes"
**GOOD:** "Run npm test and ensure all tests pass"

### Keep It Concise

- Target under 200 lines for better adherence
- Use headers and bullet points for scannability
- Longer instructions get less consistent follow-through

### Use Structured Format

```markdown
# Project Name

## Overview
Brief description here

## Build Commands
- Command 1
- Command 2

## Coding Standards
- Standard 1
- Standard 2

## Architecture
Key architectural info

## Testing
Testing approach
```

## Importing Additional Files

You can import other files using `@path` syntax:

```markdown
## Additional Resources
- Full architecture: @docs/architecture.md
- API documentation: @docs/api.md
- Contributing guide: @CONTRIBUTING.md
```

Imported files are expanded at load time. Maximum 5 levels of nesting.

**Note:** Use relative paths from the CLAUDE.md location.

## Block Comments

HTML comments are stripped before loading into context:

```markdown
<!-- This won't be loaded - use for maintainer notes -->
```

Use this for notes to human maintainers without consuming context tokens.

## Example Complete CLAUDE.md

```markdown
# E-Commerce API

A RESTful API for an e-commerce platform built with Node.js, Express, and PostgreSQL.

## Build Commands
- Install: npm install
- Build: npm run build
- Test: npm test
- Test watch: npm run test:watch
- Lint: npm run lint
- Type check: npm run type-check
- Dev server: npm run dev (runs on localhost:3000)

## Coding Standards
- TypeScript for all new code
- 2-space indentation
- Single quotes for strings
- No trailing semicolons
- PascalCase for components and types
- camelCase for variables and functions
- UPPER_SNAKE_CASE for constants

## Architecture
- src/
  - api/ - API route handlers
  - models/ - Database models
  - services/ - Business logic
  - utils/ - Utility functions
  - types/ - TypeScript type definitions
- tests/ - Test files mirroring src structure
- migrations/ - Database migrations

## Testing
- Jest for testing
- Co-located test files: Component.test.ts next to Component.ts
- Minimum 80% coverage for new code
- Use describe/it pattern
- Mock external services

## Database
- PostgreSQL 14+
- Migrations with node-pg-migrate
- Run migrations: npm run migrate
- Create migration: npm run migrate:create name

See @docs/architecture.md for detailed system design.
```

## Maintenance

Keep CLAUDE.md updated as the project evolves:
- Update when adding new build commands
- Update when changing architecture
- Update when modifying coding standards
- Review quarterly for accuracy
