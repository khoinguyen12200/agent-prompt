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
- `/tmp/agent-prompt-install/bootstrap/commands/update-claude-docs.md`
- `/tmp/agent-prompt-install/bootstrap/commands/fpt.md`
- `/tmp/agent-prompt-install/bootstrap/guides/decision-making.md`
- `/tmp/agent-prompt-install/bootstrap/guides/inspect-repo.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-central-files.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-rules.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-agents.md`
- `/tmp/agent-prompt-install/bootstrap/guides/create-commands.md`
- `/tmp/agent-prompt-install/bootstrap/guides/install-community-skills.md`
- `/tmp/agent-prompt-install/bootstrap/guides/secrets.md`
- `/tmp/agent-prompt-install/bootstrap/guides/output-requirements.md`

## Step 3: Install

1. **Bootstrap `.claude/`** — Inspect the target repo. Create:
   - `CLAUDE.md` (8-step workflow inline from template + universal rules + @import context)
   - `settings.json` (hooks: SessionStart, Stop, PostCompact)
   - `context.md` (project knowledge)
   - Scoped rules in `rules/` (all with `paths:`)
   - Concern skills in `skills/` (all with `paths:`)
   - Subagents in `agents/` (only if justified)
   - Commands in `commands/`

2. **Install community skills** — Browse `/tmp/community-skills/` and `/tmp/awesome-skills/`. Copy relevant skills to `.claude/skills/`.

3. **CLAUDE.md must stay under 200 lines.** Universal rules in CLAUDE.md. Scoped constraints in `rules/`. Detailed knowledge in `skills/`.

4. **Clean up** — Remove `/tmp/agent-prompt-install`, `/tmp/community-skills`, `/tmp/awesome-skills`.

5. **Tell the user to restart Claude Code.** The system activates on next session start.

## Output

Provide:
- The final `.claude/` tree
- Which rules/skills/agents were created and the evidence for each
- Which community skills were installed and why
- Anything you could not verify
- **Remind the user: "Restart Claude Code to activate the `.claude/` system."**
