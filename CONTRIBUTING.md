# Contributing to msms

Thanks for contributing to `msms`.
This repository is a Turborepo-based TypeScript workspace and uses `pnpm`.

## Before You Start

1. Read [AGENTS.md](./AGENTS.md).
2. Review `.agents/rules`, `.agents/learnings`, `.agents/prompts`, and `.agents/skills` before implementing.
3. Follow the project code of conduct: [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md).

## Prerequisites

- Node.js `>=20`
- pnpm `9.x`

## Local Setup

```bash
git clone https://github.com/iptoux/msms.git
cd msms
pnpm install
```

## Workspace Overview

- `apps/frontend` (Vite, port `3001`)
- `apps/admc` (Vite, port `3000`, admin control)
- `packages/ui` (shared UI package)
- `packages/db` (shared Drizzle data-layer package)

## Common Commands

Run from repo root unless stated otherwise.

```bash
pnpm dev
pnpm build
pnpm lint
pnpm format
pnpm typecheck
```

Per-package examples:

```bash
pnpm --filter frontend dev
pnpm --filter admc dev
pnpm --filter @workspace/ui lint
pnpm --filter @workspace/db typecheck
pnpm --filter @workspace/db test
```

## Contribution Workflow

1. For every new feature, create a dedicated branch from `main` (for example `feat/<topic>`).
2. For every new feature, create and maintain an implementation plan before coding (prefer `.agents/plans/` with a clear, scoped filename).
3. Make focused, minimal changes.
4. Keep app/package boundaries clear.
5. Reuse shared code from `packages/*` instead of duplicating app-local logic.
6. Run relevant checks (`lint`, `typecheck`, and build when needed).
7. Update documentation for any meaningful behavior/rule/setup changes.
8. Open a PR with a clear summary and testing notes.

## AI Contributions (Required)

If AI tooling is used for implementation, review, planning, or documentation, using the repository root [AGENTS.md](./AGENTS.md) is mandatory.

- Treat `AGENTS.md` as required baseline guidance for the entire change.
- Follow linked `.agents` rules, learnings, prompts, and skills before implementing.
- Do not bypass or replace `AGENTS.md` with ad-hoc instructions.

## Architecture and Reuse Expectations

1. Prefer reusable packages for shared components/types/interfaces/domain logic.
2. Keep sensitive logic on the server side.
3. Keep UI components lean and focused on presentation.
4. Follow `.agents/rules/04_use-shadcn-from-packages-ui.md`.
5. Follow `.agents/rules/AGENTS.override.md`.

## Documentation Requirements

Docs are part of done when relevant changes are made.

- Keep `.agents` accurate and current.
- If docs change under `.agents`, update `.agents/README.md` in the same change.
- Mask sensitive information in all docs.
- Keep docs text in English unless explicitly requested otherwise.
- Any newly introduced environment variable must be added to `.env.example`.
- New environment variables must be documented with purpose, expected format, and where they are used (at minimum in the relevant feature docs).

## Environment Variables

When introducing or changing environment variables:

1. Add new keys to `.env.example` in the same change.
2. Never commit real secrets or real credentials.
3. Document each variable in the relevant docs (for example under `docs/<feature>/`), including:
   - what it is used for
   - whether it is server-only or safe to expose publicly
   - expected value format / example placeholder
   - default/fallback behavior (if any)
4. If setup behavior changes, update root docs (`README.md` and/or `CONTRIBUTING.md`) as needed.

Relevant rules:

- `.agents/rules/01_mask_sensitive-data.md`
- `.agents/rules/02_write-in-english.md`
- `.agents/rules/03_keep-readme-updated.md`

## Commit and PR Guidance

1. Use clear, descriptive commit messages.
2. Keep one logical change per PR where possible.
3. Include in each PR description what changed, why it changed, how it was validated, and any follow-up tasks.

## Reporting Issues

If you find a bug or security concern:

- Open an issue with clear reproduction steps, or
- Contact maintainers using channels documented in the repository.
