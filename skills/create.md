# Create Skills

Skills for creating content — documents, media, design, writing.

## Documents

### Official (Anthropics)
**Install:** `/plugin install document-skills@anthropic-agent-skills`

- **docx** — Word docs
- **pdf** — PDF manipulation
- **pptx** — Slides
- **xlsx** — Spreadsheets

### From awesome-claude-skills (copy individually):
```bash
git clone --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git /tmp/awesome
cp -r /tmp/awesome/markdown-to-epub .claude/skills/
```

## Media & Design

### Official
- **creative-art** — Art and design
- **music** — Music-related

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/canvas-design .claude/skills/
cp -r /tmp/awesome/imagen .claude/skills/
cp -r /tmp/awesome/image-enhancer .claude/skills/
cp -r /tmp/awesome/slack-gif-creator .claude/skills/
```

### From gstack
- `/design-html` — Mockup to HTML
- `/design-shotgun` — Generate mockups

## Writing & Content

### From awesome-claude-skills (copy individually):
```bash
cp -r /tmp/awesome/content-research-writer .claude/skills/
cp -r /tmp/awesome/brainstorming .claude/skills/
```

### Plugins
- **marketing** — `/plugin install marketing`

## Usage

```
Load docx and edit this Word document
Load imagen and generate a mockup
```
