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

1. **Bootstrap `.claude/`** — Inspect the target repo. Create `CLAUDE.md` (with 7-step workflow inline from `agent-workflow.md`), `context.md`, concern skills, and commands as justified by evidence. Do NOT create a task-execution skill — the workflow lives in CLAUDE.md only.

3. **Install community skills** — Browse `/tmp/community-skills/` and `/tmp/awesome-skills/`. Copy relevant skills to `.claude/skills/` based on what the target repo actually contains.

4. **CRITICAL: Embed the 7-step workflow inline at the top of `.claude/CLAUDE.md`.** Use the template from `contracts/core-contracts.md`. Universal rules go in CLAUDE.md. Concern-specific rules go in skill files. CLAUDE.md must stay under 200 lines.

5. **Clean up** — Remove `/tmp/agent-prompt-install`, `/tmp/community-skills`, `/tmp/awesome-skills`.

6. **Tell the user to restart Claude Code.** CLAUDE.md is auto-loaded at session start — it will NOT take effect in the current session. The user must start a new session for the `.claude/` system to activate.

## Output

Provide:
- The final `.claude/` tree
- Which skills were created and the evidence for each
- Which community skills were installed and why
- Anything you could not verify
- **IMPORTANT — End your response with this exact message:**

> ✅ Bootstrap complete! Now **close this session and open Claude Code again**. The `.claude/` system only activates on session start — it will NOT work in this current session.
