# Project Developer Rules

This document defines global developer rules that apply to all features and contributors.

## Required Workflow For Every Feature

1. Create a dedicated feature branch (do not implement features directly on `main`).
2. Create a scoped implementation plan before writing code.
3. Keep implementation, tests, and documentation in sync in the same change.

## AI-Assisted Development (Required)

If AI is used (planning, coding, review, docs), contributors must follow the root [AGENTS.md](../../AGENTS.md) and its linked `.agents` guidance.

## Environment Variables

When a new environment variable is introduced:

1. Add it to `.env.example` in the same change.
2. Never commit real secrets.
3. Document it in relevant developer docs (at minimum feature docs), including:
   - purpose
   - server-only vs public scope
   - expected format/example placeholder
   - fallback/default behavior (if any)

## Documentation Standards

For in-scope feature changes, documentation must include:

- `docs/<feature>/developers.md`
- `docs/<feature>/users.md`
- `docs/<feature>/README.md`
- `docs/mermaid/*` updates when architecture/workflow changes
- updates in `docs/README.md` so links stay discoverable

## Security Baseline

- Keep secrets server-side only.
- Enforce auth and authorization on the server.
- Validate untrusted input.
- Avoid leaking sensitive internal details in errors and responses.

## Reference Rules

- [.agents/rules/05_use-dedicated-branch-for-large-features.md](../../.agents/rules/05_use-dedicated-branch-for-large-features.md)
- [.agents/rules/07_require-comprehensive-feature-docs.md](../../.agents/rules/07_require-comprehensive-feature-docs.md)
- [.agents/rules/08_require-feature-plan-and-env-docs.md](../../.agents/rules/08_require-feature-plan-and-env-docs.md)
