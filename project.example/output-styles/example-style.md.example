# Output Style Template

## Purpose

Output styles modify how Claude responds by adding sections to the system prompt.
They allow customizing Claude's communication style.

## Location

Place style files in: `.claude/output-styles/*.md`

## What are Output Styles?

Output styles adjust Claude's response characteristics:
- Length and verbosity
- Tone and formality
- Use of examples
- Formatting preferences
- Technical depth

Think of them as personality settings for Claude.

## File Format

Styles have two parts:
1. YAML frontmatter (configuration)
2. Markdown content (style instructions)

## Frontmatter Options

### name (required)
Display name for the style.

```yaml
name: terse
```

### description (recommended)
What this style does.

```yaml
description: Minimal, concise responses
```

## Content Section

Instructions defining the output style. These are added to the system prompt.

---

## HOW TO DECIDE WHICH STYLES TO CREATE

Analyze team preferences and project needs:

### 1. Identify Communication Needs

What response styles would be helpful?
- **Quick answers** - Terse, to-the-point
- **Learning** - Explanatory, educational
- **Professional** - Formal, polished
- **Technical** - Precise, detailed
- **Collaborative** - Casual, conversational

### 2. Consider Team Preferences

What does the team prefer?
- Do they want detailed explanations or quick answers?
- Is this a professional/client-facing project?
- Are team members learning or experienced?
- Do they prefer examples or just facts?

### 3. Style Ideas by Use Case

**For Fast-Paced Development:**
- `terse.md` - Quick, minimal responses
- `action.md` - Focus on what to do

**For Learning/Onboarding:**
- `explanatory.md` - Detailed explanations
- `tutorial.md` - Teaching style

**For Professional/Client Work:**
- `formal.md` - Professional tone
- `polished.md` - Well-structured responses

**For Technical Deep Dives:**
- `technical.md` - Precise terminology
- `detailed.md` - Comprehensive coverage

**For Collaboration:**
- `casual.md` - Conversational
- `friendly.md` - Approachable tone

### 4. Default vs Optional Styles

**Consider creating by default:**
- `terse.md` - Always useful for quick answers
- `explanatory.md` - Good for complex explanations

**Create if team needs:**
- `formal.md` - Client-facing projects
- `technical.md` - Deep technical work
- `step-by-step.md` - Procedure-heavy projects

### 5. Style Content Guidelines

Each style should define:
- **Length preference** - Short vs long responses
- **Tone** - Formal vs casual
- **Formatting** - Bullets vs paragraphs
- **Examples** - When to include them
- **Explanations** - How much detail

---

## Example Styles

### Terse

```markdown
---
name: terse
description: Minimal, concise responses
---

Be extremely concise. Use bullet points. Avoid explanations unless asked.
Prefer one-sentence answers. Skip introductory phrases. Get straight to the point.
```

### Explanatory

```markdown
---
name: explanatory
description: Thorough explanations with context
---

Provide thorough explanations. Include "why" not just "what".
Use examples to illustrate concepts. Anticipate follow-up questions.
Explain the reasoning behind recommendations.
```

### Formal

```markdown
---
name: formal
description: Professional, formal tone
---

Use professional language. Avoid contractions. Structure responses clearly.
Use complete sentences. Maintain a respectful, business-appropriate tone.
```

### Technical

```markdown
---
name: technical
description: Precise, technical responses
---

Use precise technical terminology. Include type information.
Reference specific functions, methods, and APIs.
Assume technical audience. Provide implementation details.
```

### Casual

```markdown
---
name: casual
description: Conversational, friendly tone
---

Use a conversational, friendly tone. It's okay to be informal.
Use contractions. Feel free to be enthusiastic. Write as if explaining to a peer.
```

### Step-by-Step

```markdown
---
name: step-by-step
description: Detailed step-by-step instructions
---

Break down all instructions into numbered steps.
Be explicit about each action. Include expected outcomes.
Warn about common pitfalls. Verify each step completed successfully.
```

---

## How to Apply Styles

### Via Settings

```json
{
  "outputStyle": "terse"
}
```

### Via /config Command

Run `/config` and select output style.

---

## When to Create a Style

Create a style when:
- You want consistent response formatting
- Team prefers specific communication style
- You need different styles for different contexts

Don't create a style when:
- You just want a one-off change (ask directly)
- The default style works fine

---

## Tips

- Be specific about desired behaviors
- Include examples of good responses
- Note what to avoid
- Keep instructions actionable
- Test the style before finalizing
- Name clearly for discoverability
