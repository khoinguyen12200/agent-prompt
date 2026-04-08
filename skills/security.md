# Security Skills

Install these for security testing and forensics.

## How to Install

**Source:** https://github.com/ComposioHQ/awesome-claude-skills

Copy individual skill folders:

```bash
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
cp -r /tmp/awesome/ffuf-web-fuzzing .claude/skills/
```

## Available Skills

| Skill | When | What |
|-------|------|------|
| ffuf-web-fuzzing | Security testing | Web fuzzing for vulnerabilities |
| computer-forensics | Forensics | Digital forensics analysis |
| file-deletion | Secure delete | Secure file deletion |
| metadata-extraction | Metadata | Extract file metadata |
| threat-hunting-with-sigma-rules | Threat hunting | Sigma detection rules |

## Usage

```
Load ffuf-web-fuzzing and scan for vulnerabilities
```
