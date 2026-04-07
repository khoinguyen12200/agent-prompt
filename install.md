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

1. Inspect the target repo. Create:
   - `CLAUDE.md` — workflow + universal rules + `@import context`
   - `settings.json` — hooks: SessionStart, Stop, PostCompact
   - `context.md` — project knowledge
   - `rules/` — scoped constraints, all with `paths:`
   - `skills/` — concern knowledge, all with `paths:`
   - `agents/` — only if justified
   - `commands/` — mandatory: update-claude-docs, fpt

2. Install community skills — browse `/tmp/community-skills/` and `/tmp/awesome-skills/`, copy relevant ones.

3. Clean up — remove `/tmp/agent-prompt-install`, `/tmp/community-skills`, `/tmp/awesome-skills`.

4. Tell the user to restart Claude Code.
