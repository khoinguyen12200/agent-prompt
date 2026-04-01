# .claude Bootstrap Installer

You are installing the `.claude/` bootstrap system and the 7-step workflow into the **current working directory** (the user's target repository).

## Source of truth

Fetch the source files from the `agent-prompt` repository.

1. Use `Shell` to clone (or `curl`/`wget` if `git` is unavailable):
   ```bash
   rm -rf /tmp/agent-prompt-install
   git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/agent-prompt-install
   ```

2. Read these files from the clone in this order:
   - `/tmp/agent-prompt-install/bootstrap/overview.md`
   - `/tmp/agent-prompt-install/bootstrap/contracts/auto-update.md`
   - `/tmp/agent-prompt-install/bootstrap/commands/update-claude-docs.md`
   - `/tmp/agent-prompt-install/bootstrap/commands/fpt.md`
   - `/tmp/agent-prompt-install/bootstrap/contracts/rule-learning.md`
   - `/tmp/agent-prompt-install/bootstrap/contracts/core-behavior.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/decision-making.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/inspect-repo.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/create-central-files.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/create-agents.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/create-rules.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/create-commands.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/create-skills.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/secrets.md`
   - `/tmp/agent-prompt-install/bootstrap/contracts/self-maintenance.md`
   - `/tmp/agent-prompt-install/bootstrap/guides/output-requirements.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/01-think.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/02-plan.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/03-build.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/04-review.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/05-test.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/06-ship.md`
   - `/tmp/agent-prompt-install/bootstrap/agent-workflow/07-reflect.md`

## What to install

In the **current working directory**, create the `.claude/` system:

1. **Create `.claude/skills/task-execution.md`**
   - Consolidate the 7 workflow docs into one skill file.
   - Include: Purpose, Trigger conditions (`always`), Step-by-step execution for Think → Plan → Build → Review → Test → Ship → Reflect, Mapping to the 7-step workflow, and the Rules from each step doc.

2. **Create `.claude/rules/workflow-step-enforcement.md`**
   - Write a hard rule that mandates the 7-step workflow for every task.
   - Include: Source, Scope (all tasks), Rule (must follow Think → Plan → Build → Review → Test → Ship → Reflect), Enforcement checkpoint, and Anti-patterns.

3. **Bootstrap the rest of `.claude/`**
   - Adopt the role described in `bootstrap/overview.md`.
   - Inspect the current repository (the one you're installing into).
   - Follow the bootstrap prompt's phases to create `.claude/CLAUDE.md`, `.claude/context.md`, agents, rules, commands, and skills as justified by the target repo.
   - Ensure `.claude/CLAUDE.md` references `.claude/skills/task-execution.md` for "Any task (always)".
   - Ensure the workflow enforcement rule is treated as a hard constraint.

4. **Clean up**
   - Remove `/tmp/agent-prompt-install` when done.

## Output

Provide:
- The final `.claude/` tree of the target repository
- Confirmation that `task-execution.md` and `workflow-step-enforcement.md` were created
- Which other agents/rules/skills were created and the evidence that justified each
- Anything you could not verify in the target repo
