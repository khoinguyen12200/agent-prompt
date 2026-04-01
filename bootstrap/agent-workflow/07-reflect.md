# Step 7: Reflect

## Purpose
Learn from the completed task to improve future performance. This step also ensures the `.claude/` system stays accurate and self-maintaining.

## What the Agent Must Do
1. **Assess the outcome.** Did the solution fully satisfy the requirements? Were there any surprises?
2. **Evaluate the process.** What went well? What could have been done faster or better?
3. **Identify mistakes.** Were there false assumptions, wrong turns, or overlooked edge cases?
4. **Note improvements.** Could the code be refactored later? Are there better tools or approaches to use next time?
5. **Update mental models.** If the task revealed something new about the project or technology, remember it.
6. **Auto-update `.claude/` docs.** Before finishing, the agent MUST independently check whether the `.claude/` system needs updating:
   - Did the repository structure, stack, or conventions change? → Update `.claude/context.md` and relevant rules.
   - Did a new concern or layer appear? → Create or expand the relevant agent, rule, skill, or command.
   - Did the user express a preference, convention, or constraint? → Extract it and persist it to `.claude/rules/`.
   - Did a concern disappear or become irrelevant? → Simplify or retire its docs.
   - Did any agent, rule, or skill file get created, renamed, or removed? → Update the dispatch table in `.claude/CLAUDE.md`.
   - If nothing changed, explicitly state why no `.claude/` update was needed.

## Rules
- **Be honest.** Acknowledge mistakes and inefficiencies without being self-deprecating.
- **Focus on actionable insights.** The goal is to improve the next task, not to dwell on the past.
- **Keep it brief.** Reflection should be quick but meaningful.
- **Do not modify source code during reflection.** Code changes happen in Build/Review/Test. Reflection is for learning and updating the agent's own guidance docs.
- **Apply lessons learned.** Use reflections to inform how you approach similar tasks in the future.
- **Self-maintenance is mandatory.** The `.claude/` system must never be left stale after a task. Update it automatically without waiting for the user to ask.
