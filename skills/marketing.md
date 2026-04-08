# Marketing Skills

Install these if project involves marketing content.

## marketing

**Source:** https://claude.com/plugins/marketing  
**Install:**
```bash
# Plugin (global)
/plugin install marketing
```
**When:** Creating marketing content  
**What:** Marketing content creation and optimization

## brand-guidelines

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
**When:** Applying brand standards  
**What:** Applies Anthropic's brand colors and typography

## competitive-ads-extractor

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Competitor research  
**What:** Extracts and analyzes competitors' ads

## content-research-writer

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Writing content  
**What:** Research, citations, section-by-section feedback

## twitter-algorithm-optimizer

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Twitter/X optimization  
**What:** Optimize tweets using Twitter's algorithm

## Intent Mapping

```yaml
marketing: Load marketing plugin
content: Load content-research-writer
social: Load twitter-algorithm-optimizer
brand: Load brand-guidelines
```
