# Plan: Central API Architecture Docs Update

## Goal
Update `/docs` architecture diagrams to show:
- `apps/api` as the central backend boundary
- `apps/admc` and `apps/frontend` connect to `apps/api`
- only `apps/api` connects to the database

## Scope
- `docs/mermaid/admc-architecture.md`
- `docs/mermaid/api-architecture.md`
- `docs/mermaid/db-architecture.md`
- new central architecture Mermaid file under `docs/mermaid/`
- index/link updates in docs files that list Mermaid diagrams

## Steps
1. Add a new system-level Mermaid diagram showing runtime boundaries and allowed data flow.
2. Update existing architecture Mermaid docs so they all match the same boundary model.
3. Update docs indexes (`docs/README.md` and feature README files where relevant) to include the new diagram links.
4. Verify links and Mermaid syntax consistency.

## Security Intent
Keep architecture docs explicit that DB access is server-side only through `apps/api`, with no direct DB path from clients (`apps/frontend` / `apps/admc`).
