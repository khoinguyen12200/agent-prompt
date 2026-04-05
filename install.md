# .claude Bootstrap Installer

You are installing the `.claude/` bootstrap system into the **current working directory**.

## Step 1: Clone sources

```bash
rm -rf /tmp/agent-prompt-install /tmp/community-skills /tmp/awesome-skills
git clone --depth 1 https://github.com/khoinguyen12200/agent-prompt.git /tmp/agent-prompt-install
git clone --depth 1 https://github.com/anthropics/skills.git /tmp/community-skills
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome-skills
```

## Step 2: Read bootstrap docs

Read these files from the clone in order:
- `/tmp/agent-prompt-install/bootstrap/overview.md`
- `/tmp/agent-prompt-install/bootstrap/contracts/core-contracts.md`
- `/tmp/agent-prompt-install/bootstrap/agent-workflow.md`
- `/tmp/agent-prompt-install/bootstrap/commands/update-claude-docs.md`
- `/tmp/agent-prompt-install/bootstrap/commands/fpt.md`
- `/tmp/agent-prompt-install/bootstrap/guides/decision-making.md`
- `/tmp/agent-prompt-install/bootstrap/guides/inspect-repo.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-central-files.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-agents.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-rules.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-commands.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/install-community-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/secrets.md`
- `/tmp/agent-prompt-install/bootstrap/guides/output-requirements.md`

## Step 3: Install

In the **current working directory**, create the `.claude/` system:

1. **Create `.claude/skills/task-execution/SKILL.md`** — Consolidate `agent-workflow.md` into one skill with YAML frontmatter. Include all 7 steps, trigger conditions (`always`), and rules from each step.

2. **Create `.claude/rules/workflow-step-enforcement.md`** — Hard rule mandating the 7-step workflow.

3. **Bootstrap the rest** — Inspect the target repo, follow the bootstrap phases, create `CLAUDE.md`, `context.md`, agents, rules, commands, and skills as justified.

4. **Install community skills** — Browse `/tmp/community-skills/` and `/tmp/awesome-skills/`. Copy relevant skills to `.claude/skills/` based on what the target repo actually contains. Register them in the dispatch table.

5. **CRITICAL: Embed the 7-step workflow inline at the top of `.claude/CLAUDE.md`.** Do NOT just reference `skills/task-execution/SKILL.md`. Use the template from `contracts/core-contracts.md`. CLAUDE.md must stay under 200 lines.

6. **Clean up** — Remove `/tmp/agent-prompt-install`, `/tmp/community-skills`, `/tmp/awesome-skills`.

## Output

Provide:
- The final `.claude/` tree
- Which agents/rules/skills were created and the evidence for each
- Which community skills were installed and why
- Anything you could not verify
