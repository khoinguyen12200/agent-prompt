# Phase 1 — Inspect the Repository

First inspect the repository in depth.

Read as many relevant files as needed, such as:
- README and docs
- package manifests and lockfiles
- source tree
- app/server/client folders
- components/pages/routes/controllers/services
- tests
- CI/CD configs
- Docker/infra/deploy scripts
- database schema/migrations/ORM config
- lint/formatter/tooling config
- auth/middleware/validation/security-related code
- scripts and developer workflows
- contribution or release docs if present

Determine from evidence (files you actually read):
- repository maturity
- languages
- frameworks
- runtimes
- package manager(s)
- app type(s)
- repository shape
- architecture/layer boundaries
- API presence and style
- UI presence and style
- database presence and style
- testing strategy
- deployment/release strategy
- security-sensitive areas
- developer workflow conventions
- which concerns are verified present now
- which concerns are verified absent now

For each item, you must be able to point to the file or pattern that proves it. If you cannot, mark it as "unverified" and do not build `.claude/` content on top of it.

If the repo is blank or nearly blank:
- explicitly say so
- create only the bare minimum `.claude/` scaffold
- do not speculate about what the project will become
- do not create content for concerns that do not yet exist
