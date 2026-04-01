# Step 5: Test

## Purpose
Validate that the solution works correctly and does not introduce regressions.

## What the Agent Must Do
1. **Run relevant tests.** Execute unit tests, integration tests, or any other test suites related to the changed code.
2. **Verify manually if needed.** If automated tests are insufficient, run the code or use tools to check behavior.
3. **Fix failures.** If tests fail, diagnose the root cause and fix it.
4. **Add tests for new behavior.** If the task introduces new features or fixes bugs, add or update tests to cover them.
5. **Confirm no regressions.** Run broader tests if the change has a wide impact.

## Rules
- **Do not ignore failing tests.** A failing test is a blocker.
- **Run tests in the project's native environment.** Use the correct test runner, config, and commands.
- **Add tests for new logic.** Untested code is unfinished code.
- **Keep test changes minimal.** Only modify tests that are directly related to the change.
- **Document manual verification steps.** If you tested something manually, note what you did and the results.
