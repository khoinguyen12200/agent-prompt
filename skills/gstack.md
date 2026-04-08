# GStack Skills

From: https://github.com/garrytan/gstack

Install:
```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

## Planning Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/office-hours` | Building new feature | 6 forcing questions that reframe product before coding |
| `/plan-ceo-review` | Strategic decisions | Challenges scope, finds 10-star product hiding in request |
| `/plan-eng-review` | Technical planning | Architecture, data flow diagrams, edge cases, tests |
| `/plan-design-review` | UI/UX decisions | Rates design dimensions 0-10, detects AI slop |
| `/plan-devex-review` | API/SDK design | Developer experience review, benchmarks TTHW |
| `/autoplan` | Full pipeline | Runs CEO → design → eng review automatically |

## Review Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/review` | Code complete | Staff engineer review, auto-fixes obvious issues |
| `/investigate` | Debugging needed | Systematic root-cause debugging, Iron Law enforcement |
| `/design-review` | UI changes | Design audit then fixes what it finds |
| `/devex-review` | API changes | Live developer experience audit |
| `/codex` | Second opinion | Independent review from OpenAI Codex CLI |

## QA Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/qa` | Ready to test | Browser testing, finds bugs, fixes with atomic commits |
| `/qa-only` | Bug report needed | Same methodology but report only, no code changes |
| `/benchmark` | Performance check | Baseline page load times, Core Web Vitals |

## Shipping Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/ship` | Ready to release | Sync main, run tests, audit coverage, push, open PR |
| `/land-and-deploy` | PR approved | Merge PR, wait for CI, deploy, verify production |
| `/canary` | After deploy | Post-deploy monitoring for errors/regressions |
| `/document-release` | After release | Update all project docs to match what shipped |

## Design Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/design-consultation` | Design system needed | Build complete design system from scratch |
| `/design-shotgun` | Need options | Generate 4-6 AI mockup variants, iterate visually |
| `/design-html` | Mockup to code | Turn mockup into production HTML, 30KB zero deps |
| `/design-review` | Audit existing | Same audit as plan-design-review, then fixes |

## Browser Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/browse` | Need browser | Real Chromium, real clicks, ~100ms per command |
| `/open-gstack-browser` | Full browser | GStack Browser with sidebar, anti-bot stealth |
| `/setup-browser-cookies` | Auth needed | Import cookies from real Chrome/Arc/Brave |
| `/pair-agent` | Multi-agent | Share browser with OpenClaw/Hermes/Codex agents |

## Utility Skills

| Command | Use When | Description |
|---------|----------|-------------|
| `/cso` | Security audit | OWASP Top 10 + STRIDE threat model, zero noise |
| `/careful` | Dangerous ops | Warn before rm -rf, DROP TABLE, force-push |
| `/freeze` | Scope control | Lock edits to one directory |
| `/guard` | Maximum safety | `/careful` + `/freeze` combined |
| `/retro` | Weekly retro | Per-person breakdowns, shipping streaks, trends |
| `/learn` | Memory mgmt | Review/search what gstack learned across sessions |
