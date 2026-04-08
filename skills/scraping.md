# Web Scraping Skills

Install these if project needs to scrape websites.

## firecrawl

**Source:** https://claude.com/plugins/firecrawl  
**Install:**
```bash
# Plugin (global)
/plugin install firecrawl

# Or check awesome-claude-skills for standalone
```
**When:** Web scraping, data extraction  
**What:** Web scraping and data extraction

## firecrawl-skill

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:**
```bash
git clone --single-branch --depth 1 https://github.com/ComposioHQ/awesome-claude-skills.git .claude/skills/awesome
```
**When:** Scraping (if plugin not available)  
**What:** Web scraping capabilities

## article-extractor

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Extracting article content  
**What:** Extract article text and metadata from web pages

## reddit-fetch

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Fetching Reddit content  
**What:** Fetches Reddit when WebFetch blocked

## Intent Mapping

```yaml
scrape: Load firecrawl
crawl: Load firecrawl
extract: Load article-extractor
reddit: Load reddit-fetch
```
