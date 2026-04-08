# Document Processing Skills

Install these if project works with documents.

## docx, pdf, pptx, xlsx

**Source:** https://github.com/anthropics/skills  
**Install:**
```bash
# Plugin (global)
/plugin install document-skills@anthropic-agent-skills

# Or clone for project level
git clone --single-branch --depth 1 https://github.com/anthropics/skills.git .claude/skills/anthropics
```
**When:** Processing PDF, Word, Excel, PowerPoint  
**What:** Complete document processing suite

| Skill | Files | What It Does |
|-------|-------|--------------|
| docx | .docx | Create, edit Word docs with tracked changes |
| pdf | .pdf | Extract text, tables, merge, annotate |
| pptx | .pptx | Read, generate slides |
| xlsx | .xlsx | Spreadsheets, formulas, charts |

## markdown-to-epub

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
**When:** Converting markdown to ebook  
**What:** Markdown to EPUB converter

## csv-data-summarizer

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** CSV analysis  
**What:** CSV analysis with visualizations

## Intent Mapping

```yaml
document: Load anthropics document-skills
pdf: Load pdf skill
csv: Load csv-data-summarizer
```
