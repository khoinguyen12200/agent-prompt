# Frontend Skills

Install these if project uses React, Vue, Angular, or frontend frameworks.

## frontend-design

**Source:** https://claude.com/plugins/frontend-design  
**Install:**
```bash
# Plugin (global)
/plugin install frontend-design

# Or for project level, check if skill files available in awesome-claude-skills
```
**When:** React, Vue, Angular projects  
**What:** Frontend design patterns and component architecture

## ui-ux-pro-max

**Source:** https://ui-ux-pro-max-skill.nextlevelbuilder.io  
**Install:** Check website for install method  
**When:** Advanced UI/UX needs  
**What:** Advanced UI/UX patterns and accessibility

## artifacts-builder

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
**When:** Creating HTML artifacts with React/Tailwind  
**What:** Multi-component HTML artifacts using React, Tailwind CSS, shadcn/ui

## d3-visualization

**Source:** https://github.com/ComposioHQ/awesome-claude-skills  
**Install:** With awesome-claude-skills repo  
**When:** Need charts/visualizations  
**What:** D3 charts and interactive data visualizations

## Intent Mapping

```yaml
frontend: Load frontend-design
artifacts: Load artifacts-builder
d3: Load d3-visualization
```
