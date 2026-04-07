# First-Principles Thinking Command

Create `.claude/commands/fpt.md`. Triggered via `/fpt [task]`. Forces deep analysis before any code.

The command must instruct Claude to:

1. **STOP** — no code yet
2. **DECOMPOSE** — root problem, not surface symptom. Verified facts only.
3. **GATHER EVIDENCE** — read files, trace code paths, list facts with sources
4. **CHALLENGE** — what am I assuming? Simpler explanation? Right problem?
5. **BUILD** — from verified facts only, logical steps, no leaps
6. **VALIDATE** — addresses root cause? Minimal change? How to verify?
7. **PRESENT:**
   ```
   ## First-Principles Analysis
   Problem / Verified facts / Root cause / Solution / Why it works / Risks / Verification
   ```
8. **WAIT** for confirmation before executing.
