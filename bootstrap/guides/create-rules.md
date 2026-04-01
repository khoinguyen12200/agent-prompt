# Phase 4 — Create Dynamic Rules

Create the `rules/` folder. Rules come from TWO sources:

1. **Repository-detected rules**: Patterns, conventions, and structures observed in the codebase.
2. **User-expressed rules**: Preferences, constraints, conventions, and corrections stated by the user during any task.

Both sources have equal authority. Rules are concern-based.
Examples:
- code style
- project structure
- API conventions
- database conventions
- security
- testing
- error handling
- git workflow
- package boundaries
- dependency management
- release workflow
These are examples, not a fixed list.

Rule creation rules:
- Blank repo: create only foundational rules that make sense now
- Existing repo: create rules for active concerns
- If a concern appears later, create the rule then
- If the user expresses a preference or constraint during any task, create or update the rule immediately
- If a rule becomes stale, update it
- If a rule becomes irrelevant, simplify or retire it
- If the user contradicts an existing rule, update the rule and note the change history
- **ALWAYS create `rules/workflow-step-enforcement.md`** — this rule mandates the Think → Plan → Build → Review → Test → Ship → Reflect workflow for every task

Each rule file should include:
- Source (detected from code OR expressed by user, with context)
- Scope (which files, folders, or task types this rule applies to — must be specific enough for auto-matching)
- Current repo-specific guidance
- Evidence (what file, pattern, or user statement backs this rule)
- What patterns Claude should follow
- What anti-patterns to avoid
- Enforcement checkpoint (what Claude must verify before finishing any task that falls within this rule's scope)
- When this rule must be updated
