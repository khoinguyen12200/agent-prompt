

Example flow https://mintcdn.com/claude-code/WLZtXlltXc8aIoIM/images/hooks-lifecycle.svg?w=1650&fit=max&auto=format&n=WLZtXlltXc8aIoIM&q=85&s=526b1d8e3a69acd125c244fdfdd7acd5
Claude doc hook: https://code.claude.com/docs/en/hooks

I want completely new bootstrap and flow, we don't use 8 step as our main structure.

What did this bootstrap do ?

=> This base on skills & plugins already have on market & community
=> First we will generate all rules, skills

Recommended skill:
https://github.com/garrytan/gstack
https://claude.com/plugins/frontend-design
https://github.com/obra/superpowers
https://ui-ux-pro-max-skill.nextlevelbuilder.io/
https://claude.com/plugins/firecrawl
https://claude-mem.ai/
https://claude.com/plugins/prisma
https://claude.com/plugins/marketing
And those skill list https://github.com/ComposioHQ/awesome-claude-skills | https://github.com/anthropics/skills

superpowers already have a very good structure for complex skills
And gstack is really good at agentic
=> But I still don't know how to apply those to our project, give me some ideas

And we will add UserPromptSubmit hook to trigger according skills (actively), currently it's rarely use skill
And on Session end we will use SessionEnd hook to summarize and reflect, save new rules (actively)

==> FINAL Be smart and give me a Plan to implement those, base on what claude support & best practice