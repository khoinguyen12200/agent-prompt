# Step 4: Review

## Purpose
Critically examine the work done so far to catch bugs, inconsistencies, and deviations from the requirements.

## What the Agent Must Do
1. **Re-read the requirements.** Compare the implemented solution against the original request.
2. **Inspect the code.** Look for logic errors, off-by-one bugs, race conditions, memory leaks, or security issues.
3. **Check for consistency.** Ensure naming, formatting, and patterns align with the rest of the codebase.
4. **Verify edge cases.** Consider empty inputs, null values, large data sets, and error paths.
5. **Review diffs.** If possible, look at the changes holistically to spot unintended modifications.

## Rules
- **Be your own critic.** Assume there is at least one bug and find it.
- **Do not skip this step.** Even for "simple" changes.
- **Check for regressions.** Ensure existing functionality is not broken by the new code.
- **Verify no debug code is left behind.** Remove print statements, temporary files, and commented-out code.
- **Fix issues immediately.** If you find a problem during review, correct it before moving to Test.
