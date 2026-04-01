# Step 6: Ship

## Purpose
Deliver the completed work to the user in a clean, understandable way.

## What the Agent Must Do
1. **Summarize the changes.** Provide a concise overview of what was done, why, and how.
2. **List modified files.** Mention the key files that were created, updated, or deleted.
3. **Confirm the solution works.** Reference test results or manual verification.
4. **Update documentation.** If the change affects docs, READMEs, or AGENTS.md, update them.
5. **Leave the codebase clean.** Ensure no temporary files, broken builds, or half-finished work remains.

## Rules
- **Be clear and concise.** The user should understand the outcome without reading every line of code.
- **Highlight important details.** Call out breaking changes, new dependencies, or configuration updates.
- **Do not ship broken code.** Everything must compile, pass tests, and function as expected.
- **Respect git hygiene.** Do not run `git commit`, `git push`, or other git mutations unless explicitly asked.
- **Offer next steps.** If there are follow-up tasks or optional improvements, mention them briefly.
