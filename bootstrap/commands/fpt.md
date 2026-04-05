# First-Principles Thinking Command

Create a command file at `.claude/commands/fpt.md`.

Triggered via `/fpt` followed by a task or question. Forces deep first-principles thinking — maps to the **Think** step. For important tasks where correctness matters more than speed.

The command must instruct Claude to:

1. **STOP.** Do not write code. Enter the Think step.

2. **DECOMPOSE:** What is the user actually asking? What is the root problem (not surface symptom)? What are the verified fundamental truths? What are the constraints?

3. **GATHER EVIDENCE:** Read all relevant files. Trace actual code paths. Identify real vs desired behavior. List every verified fact with its source.

4. **CHALLENGE THINKING:** What am I tempted to assume? Is there a simpler explanation? Am I solving the right problem? What breaks if I'm wrong?

5. **BUILD FROM FUNDAMENTALS:** Start from verified facts only. Each step follows logically. No leaps — prove each step. Consider edge cases from actual code.

6. **VALIDATE:** Does it address root cause? Conflicts with existing rules? What's the minimal change? How to verify?

7. **PRESENT:**
   ```
   ## First-Principles Analysis

   **Problem:** [root problem]
   **Verified facts:** [numbered list with evidence sources]
   **Root cause:** [traced from evidence]
   **Proposed solution:** [built from fundamentals]
   **Why this works:** [logical chain]
   **Risks:** [evidence-based]
   **Verification plan:** [how to confirm]
   ```

8. **WAIT** for user confirmation before executing.

Best for: complex debugging, irreversible architectural decisions, research tasks, anything where "get it right" trumps "get it fast."
