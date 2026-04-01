# How to Decide What to Create

You must detect the current repository state first.

Classify the repository, for example:
- blank / nearly blank
- skeleton / starter
- frontend-only
- backend-only
- full-stack
- library / SDK
- CLI tool
- monorepo
- package workspace
- service + worker
- API + admin panel
- docs-heavy repo
- infra / deployment repo
- data / ETL repo
- mobile / desktop / browser extension
- mixed or evolving structure

Then decide what `.claude` assets are needed.

Examples of dynamic outcomes:
- Blank repo:
  - minimal `CLAUDE.md` routing table and minimal `context.md`
  - minimal `rules/` for verified conventions only
  - a maintenance agent if justified
  - no content for concerns that do not yet exist — no placeholders, no speculation

- Backend appears later:
  - create or expand backend-related agent(s)
  - create or expand API/database/error-handling/security/testing rules as needed
  - update architecture and stack docs

- Frontend appears later:
  - create or expand frontend-related agent(s)
  - create or expand UI/style/testing/accessibility/project-structure docs as needed

- Database appears later:
  - create or expand database-related agent(s) and rules

- Deployment/CI appears later:
  - create or expand release/deploy skill and command docs

- Existing mature repo:
  - create the relevant agents/docs immediately based on what is already present

Do not use these examples as a fixed file list.
Use them only as guidance for dynamic generation.
