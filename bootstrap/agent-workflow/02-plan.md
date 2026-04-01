# Step 2: Plan

## Purpose
Design a clear, actionable approach to solve the problem. A good plan minimizes wasted effort and prevents architectural missteps.

## What the Agent Must Do
1. **Break down the task.** Split the work into small, logical subtasks or milestones.
2. **Identify affected files.** List the files that will be read, created, modified, or deleted.
3. **Choose an approach.** Evaluate trade-offs (simplicity vs. performance, short-term vs. long-term) and pick the best one.
4. **Consider risks.** Think about edge cases, backward compatibility, and potential regressions.
5. **Get approval for significant changes.** If the plan involves architectural changes, refactoring, or multiple files, present it to the user for approval before building.

## Rules
- **Keep it stupidly simple.** Prefer the simplest solution that meets the requirements.
- **Minimize blast radius.** Limit changes to only what is necessary.
- **Follow existing patterns.** Align with the project's architecture, style, and conventions.
- **Document the plan.** Write it down so it can be reviewed and referenced during execution.
- **No coding yet.** This step is for design and decision-making only.
