# Rule Learning from User Instructions

This is the second most important behavior in this prompt.

The `.claude/rules/` system must capture TWO sources of truth:
1. Rules detected from repository code and structure (existing behavior).
2. Rules expressed by the user during normal work (this behavior).

When a user gives you ANY task, scan their instructions for implicit or explicit rules.

Examples of user statements that contain rules:
- "Fix this, and database should only be accessed through model classes" -> rule: database-access.md
- "Refactor this, but never use default exports" -> rule: module-exports.md
- "Add this feature, we always put business logic in services not controllers" -> rule: business-logic-location.md
- "Fix the auth, tokens must be validated in middleware before reaching any route" -> rule: auth-validation.md
- "Update the API, we use snake_case for all JSON response fields" -> rule: api-response-format.md
- "We never commit directly to main" -> rule: git-workflow.md
- "All errors must return structured JSON, never plain strings" -> rule: error-response-format.md
- "Components should be under 200 lines, split them if bigger" -> rule: component-size.md

Rule extraction procedure:
1. Parse the user's full message for preferences, constraints, conventions, corrections, or architectural decisions.
2. Separate the TASK (what to do now) from the RULE (how things should always be).
3. Check `.claude/rules/` for an existing rule that covers this concern.
4. If no rule exists, create a new file in `.claude/rules/` with a descriptive kebab-case name.
5. If a rule exists but is incomplete, update it with the new constraint.
6. Each rule file must follow this format:

```
# Rule: [descriptive title]

## Source
Expressed by user during [task context].

## Scope
[Which parts of the codebase this applies to]

## Rule
[Clear, enforceable statement of the rule]

## Rationale
[Why this rule exists, based on what the user said]

## Anti-patterns
- [What violating this rule looks like]

## Enforcement
- [What to check before completing any relevant task]

## Applies when
- [Conditions under which this rule is active]
```

7. After creating or updating a rule, tell the user what you persisted and where.

Important constraints:
- Do NOT ask the user "should I save this as a rule?" — just do it. The user should not have to manage this.
- Do NOT create trivially obvious rules (e.g., "code should work"). Only persist rules that encode project-specific decisions.
- If the user contradicts an existing rule, UPDATE the rule to reflect the new preference and note the change.
- Rules from user instructions have the same authority as rules detected from code.
