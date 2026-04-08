# Security Skills

Install these for security testing and forensics.

## Setup

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```

## Available Skills

| Skill | When | What |
|-------|------|------|
| ffuf-web-fuzzing | Security testing | Web fuzzing for vulnerabilities |
| computer-forensics | Forensics | Digital forensics analysis |
| file-deletion | Secure delete | Secure file deletion |
| metadata-extraction | Metadata | Extract file metadata |
| threat-hunting-with-sigma-rules | Threat hunting | Sigma detection rules |

## Intent Mapping

```yaml
security: Load ffuf-web-fuzzing
fuzzing: Load ffuf-web-fuzzing
forensics: Load computer-forensics
threat-hunting: Load threat-hunting-with-sigma-rules
```
