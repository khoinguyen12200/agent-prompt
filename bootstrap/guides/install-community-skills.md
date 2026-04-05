# Phase 6b — Install Community Skills

After creating custom skills, evaluate whether community-maintained skills should be installed.

## Skill sources

Clone these repos during installation:

1. **Official Anthropic skills**: `/tmp/community-skills/` (cloned from https://github.com/anthropics/skills)
2. **Community skills**: `/tmp/awesome-skills/` (cloned from https://github.com/ComposioHQ/awesome-claude-skills)

## How to evaluate

1. Browse the skill directories in both repos
2. Read each SKILL.md's `name` and `description` in the YAML frontmatter
3. Match against evidence found in the target repo (frameworks, tools, patterns)
4. Copy relevant skill directories to `.claude/skills/`
5. Register installed skills in the CLAUDE.md dispatch table

## Rules

- Evidence required — each installed skill must be justified by something observable in the target repo
- Do not install speculatively
- Adjust only repo-specific details (paths, commands) — preserve the skill's core workflow
- If neither repo has relevant skills, skip this phase entirely
