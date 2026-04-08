# Creative & Media Skills

Install these for image generation, video, and creative content.

## Setup

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```

## Available Skills

| Skill | When | What |
|-------|------|------|
| canvas-design | Visual art | Create PNG/PDF artwork |
| imagen | Image generation | Generate images with Gemini API |
| image-enhancer | Image quality | Enhance resolution/sharpness |
| slack-gif-creator | GIFs | Animated GIFs for Slack |
| theme-factory | Theming | Apply themes to docs/slides |
| video-downloader | Videos | Download YouTube videos |
| youtube-transcript | Transcripts | Fetch YouTube transcripts |

## Intent Mapping

```yaml
design: Load canvas-design or theme-factory
image: Load imagen or image-enhancer
gif: Load slack-gif-creator
video: Load video-downloader or youtube-transcript
```
