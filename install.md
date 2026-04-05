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
- `/tmp/agent-prompt-install/bootstrap/guides/create-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-commands.md`
- `/tmp/agent-prompt-install/bootstrap/guides/install-community-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/secrets.md`
- `/tmp/agent-prompt-install/bootstrap/guides/output-requirements.md`

## Step 3: Install

1. **Create `.claude/skills/task-execution/SKILL.md`** — Consolidate `agent-workflow.md` into one skill with YAML frontmatter. Include all 7 steps and rules.

2. **Bootstrap `.claude/`** — Inspect the target repo. Create `CLAUDE.md`, `context.md`, concern skills, workflow skills, and commands as justified by evidence.

3. **Install community skills** — Browse `/tmp/community-skills/` and `/tmp/awesome-skills/`. Copy relevant skills to `.claude/skills/` based on what the target repo actually contains.

4. **CRITICAL: Embed the 7-step workflow inline at the top of `.claude/CLAUDE.md`.** Use the template from `contracts/core-contracts.md`. Universal rules go in CLAUDE.md. Concern-specific rules go in skill files. CLAUDE.md must stay under 200 lines.

5. **Post-install activation** — Read the `CLAUDE.md` you just created and follow it for any remaining tasks in this session.

6. **Clean up** — Remove `/tmp/agent-prompt-install`, `/tmp/community-skills`, `/tmp/awesome-skills`.

## Output

Provide:
- The final `.claude/` tree
- Which skills were created and the evidence for each
- Which community skills were installed and why
- Anything you could not verify
