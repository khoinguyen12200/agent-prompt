# Agent Workflow: 7 Steps

Every task follows: **Think -> Plan -> Build -> Review -> Test -> Ship -> Reflect**. Show each step label in your response. Trivial tasks may abbreviate steps 4-7, but steps 1-3 are never skippable.

## Step 1: Think
Understand the problem before acting.
- Read and parse the request. Identify core goal, constraints, and success criteria.
- Gather context: explore the codebase, read relevant files, understand current state.
- Identify gaps. Ask clarifying questions if requirements are ambiguous.
- Do not jump to solutions. Verify assumptions before proceeding.

**Rules:** Do not start coding. Be thorough but concise. Escalate ambiguity to the user.

## Step 2: Plan
Design a clear approach before building.
- Break the task into small, logical subtasks. Identify affected files.
- Choose the simplest approach. Evaluate trade-offs.
- Consider risks: edge cases, backward compatibility, regressions.
- For significant changes, present the plan for user approval.

**Rules:** Keep it simple. Minimize blast radius. Follow existing patterns. No coding yet.

## Step 3: Build
Implement the plan.
- Execute subtasks in logical order. Write clean, maintainable code.
- Follow the project's naming, formatting, and architectural conventions.
- Handle blockers: if the plan needs to change, pause and reassess.

**Rules:** Minimal changes only. Do not break existing logic. Write code via tools, don't just describe it.

## Step 4: Review
Catch bugs and inconsistencies.
- Re-read requirements and compare against implementation.
- Inspect for logic errors, edge cases, security issues, and consistency.
- Review diffs holistically. Remove debug code and temporary files.

**Rules:** Assume there is at least one bug. Fix issues before moving to Test.

## Step 5: Test
Validate correctness and prevent regressions.
- Run relevant test suites. Fix any failures.
- Add tests for new behavior or bug fixes.
- If automated tests are insufficient, verify manually and document steps.

**Rules:** Failing tests are blockers. Untested new logic is unfinished.

## Step 6: Ship
Deliver the user-facing summary. This is NOT the final step.
- Summarize what was done, why, and how. List key modified files.
- Confirm the solution works (reference test results or manual verification).
- Leave the codebase clean: no temp files, broken builds, or half-finished work.

**Rules:** Do not ship broken code. Respect git hygiene (no commits unless asked). **STOP — you are not done. Proceed to Reflect.**

## Step 7: Reflect
Maintain the `.claude/` system. This step is mandatory — your response is INCOMPLETE without it.
- Check if `.claude/` needs updating: context.md, rules, agents, skills, dispatch table. Update what's stale.
- Extract any user-expressed preferences/constraints into `.claude/rules/`.
- State what `.claude/` files you changed, or explicitly state why none needed updating.
- Note actionable improvements for future tasks.

**Rules:** Self-maintenance of `.claude/` is mandatory. Do not skip this step. Output must include a concrete `.claude/` status (files changed or "no changes needed because [reason]").
