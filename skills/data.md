# Data & Research Skills

Install these for data analysis and research.

## Setup

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
# Clone to temp then copy individual skills:
```bash
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
# Then copy specific skill folders:
cp -r /tmp/awesome/[skill-name] .claude/skills/
```
```

## Available Skills

| Skill | When | What |
|-------|------|------|
| csv-data-summarizer | CSV analysis | CSV analysis with visualizations |
| deep-research | Research | Multi-step research with Gemini |
| root-cause-tracing | Debugging | Trace deep errors to origin |

## From gstack

| Command | When | What |
|---------|------|------|
| /investigate | Debugging | Systematic root cause debugging |

## Intent Mapping

```yaml
research: Load deep-research
csv: Load csv-data-summarizer
trace: Load root-cause-tracing or /investigate
```
