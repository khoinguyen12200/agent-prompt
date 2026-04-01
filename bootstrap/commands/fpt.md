# First-Principles Thinking Command

You must create a command file at `.claude/commands/fpt.md`.

This command is triggered when the user says `/fpt` followed by their task or research question.

The `/fpt` command forces Claude into deep first-principles thinking mode. This is for important tasks where getting it right matters more than getting it fast. It maps directly to the **Think** step of the universal workflow.

The command must instruct Claude to:

1. STOP before doing anything. Do not write code. Do not make changes. Enter the **Think** step.

2. DECOMPOSE the problem:
   - What is the user actually asking for? (restate in your own words)
   - What is the root problem, not the surface symptom?
   - What are the fundamental truths involved? (verified facts only)
   - What are the constraints? (technical, business, user-stated)

3. GATHER EVIDENCE:
   - Read all relevant files in the repository
   - Trace the actual code paths involved
   - Identify the real current behavior vs the desired behavior
   - List every fact you verified and how you verified it

4. CHALLENGE your own thinking:
   - What am I tempted to assume here? List it. Then verify or discard each one.
   - Is there a simpler explanation?
   - Am I solving the right problem?
   - What would break if I'm wrong?

5. BUILD THE SOLUTION from fundamentals:
   - Start from verified facts only
   - Each step must follow logically from the previous
   - No leaps. No "this should work." Prove each step.
   - Consider edge cases derived from the actual code, not imagined scenarios

6. VALIDATE before executing:
   - Does the solution address the root cause?
   - Does it conflict with any existing rules in `.claude/rules/`?
   - What is the minimal change that solves this?
   - How will you verify the fix works?

7. PRESENT the analysis to the user:
   ```
   ## First-Principles Analysis

   **Problem:** [root problem, not surface symptom]
   **Verified facts:** [numbered list with evidence source for each]
   **Root cause:** [traced from evidence]
   **Proposed solution:** [built from fundamentals]
   **Why this works:** [logical chain from facts to solution]
   **Risks:** [what could still go wrong, based on evidence]
   **Verification plan:** [how to confirm the solution works]
   ```

8. WAIT for user confirmation before executing the solution.

This command is especially useful for:
- Debugging complex issues where the obvious answer might be wrong
- Architectural decisions that are hard to reverse
- Research tasks where accuracy matters more than speed
- Any task where the user says "this is important, get it right"
