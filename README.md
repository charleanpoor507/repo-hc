# msms

<p align="center">
  <a href="https://turbo.build/repo"><img src="https://img.shields.io/badge/Turbo-Repo-EF4444?style=for-the-badge&logo=turborepo&logoColor=white" alt="Turbo: repo" /></a>
  <a href="https://tanstack.com/start"><img src="https://img.shields.io/badge/TanStack-Start-0EA5E9?style=for-the-badge&logo=reactrouter&logoColor=white" alt="TanStack: Start" /></a>
  <a href="https://pnpm.io/"><img src="https://img.shields.io/badge/PM-pnpm-F59E0B?style=for-the-badge&logo=pnpm&logoColor=white" alt="PM: pnpm" /></a>
  <a href="./docs/README.md"><img src="https://img.shields.io/badge/Docs-Self--contained-10B981?style=for-the-badge&logo=readthedocs&logoColor=white" alt="Docs: Self-contained" /></a>
  <a href="./AGENTS.md"><img src="https://img.shields.io/badge/AI%20Flow-OpenAI-111827?style=for-the-badge&logo=openai&logoColor=white" alt="AI Flow: Codex" /></a>
  <a href="./SECURITY.md"><img src="https://img.shields.io/badge/Security-Policy-DC2626?style=for-the-badge&logo=shield&logoColor=white" alt="Security Policy" /></a>
  <a href="./CODE_OF_CONDUCT.md"><img src="https://img.shields.io/badge/Community-Code%20of%20Conduct-2563EB?style=for-the-badge&logo=github&logoColor=white" alt="Code of Conduct" /></a>
  <a href="./README.md"><img src="https://img.shields.io/badge/License-AGPL3-6B7280?style=for-the-badge" alt="License" /></a>
</p>

<h3 align="center">
  msms is a Turborepo + TanStack Start workspace with shared packages under <code>packages/*</code>.<br />
  It also includes a self-contained documentation system and a structured AI agent workflow for planning, implementation, and knowledge capture.
</h3>

## Table of Contents

- [Workspace](#workspace)
- [Install](#install)
- [Common Commands](#common-commands)
- [Documentation System](#documentation-system)
- [AI Agent Workflow System](#ai-agent-workflow-system)
- [OpenAI Codex Preferences](#openai-codex-preferences)
- [Shared Database Package](#shared-database-package)

## Workspace

- `apps/frontend`: TanStack Start app (port `3001`)
- `apps/admc`: TanStack Start app (admin control, configured `--port 3000`, auto-fallback if occupied)
- `apps/admc-tauri`: Tauri + React desktop app (manual start only)
- `apps/api`: default Hono backend app (Bun/Hono default port `3000`)
- `packages/ui`: shared UI package
- `packages/db`: shared Drizzle data-layer package

## Install

```bash
pnpm install
```

> [!NOTE]
> Use `pnpm` for all workspace operations (`install`, `add`, `remove`, and scripts).

## Common Commands

```bash
pnpm dev
pnpm dev:all
pnpm build
pnpm lint
pnpm format
pnpm typecheck
```

`pnpm dev` excludes `apps/admc-tauri` by design. Start desktop runtime manually with:

```bash
pnpm --filter admc-tauri tauri dev
```

When running root `pnpm dev`, effective local ports are typically:

- `api`: `3000`
- `frontend`: `3001`
- `admc`: `3002` (fallback, because `3000` and `3001` are already used)

## Documentation System

Project documentation is centralized in `docs/` and organized by feature, audience, and architecture diagrams:

- `docs/README.md`: docs index and recommended reading order
- `docs/project/`: global project standards and rules
- `docs/workflow/`: feature-branch and self-contained docs workflow guides
- `docs/api/`: Hono backend app docs for developers and users
- `docs/admc-tauri/`: desktop admin-control app docs for developers and users
- `docs/db/`: shared database package docs for developers and users
- `docs/mermaid/`: architecture and workflow diagrams

## AI Agent Workflow System

AI-assisted work in this repository is guided by `AGENTS.md` and the local `.agents/` knowledge base:

![Codex Workflow](./docs/assets/codex-workflow.svg)

- `AGENTS.md`: baseline collaboration, architecture, security, and documentation rules
- `.agents/rules/`: operational rules for agent-authored content
- `.agents/skills/`: reusable `SKILL.md` playbooks for common tasks
- `.agents/learnings/`: implementation learnings and decisions
- `.agents/prompts/`: sanitized source prompts for traceability
- `.agents/plans/` (when present): scoped feature implementation plans

> [!TIP]
> For AI-assisted tasks, read `AGENTS.md` first, then `.agents/README.md`, then `docs/README.md`.

> [!IMPORTANT]
> Security-first is mandatory: keep secrets server-side, enforce authorization on the server, and never trust client input.

Start with:

1. `AGENTS.md`
2. `.agents/README.md`
3. `docs/README.md`

## OpenAI Codex Preferences

When collaborating with OpenAI Codex in this repo, prefer:

- `pnpm`-only workflows
- feature branches + scoped plans for feature work
- strict server/client boundaries for auth and business logic
- small modular changes with reusable shared packages when appropriate
- test coverage for new logic and regression-prone paths
- immediate documentation sync in `docs/` and `/.agents` when behavior changes

## Shared Database Package

`packages/db` is the canonical home for shared Drizzle schema, adapters, types, and migrations.

Public subpath exports:

- `@workspace/db/schema`
- `@workspace/db/types`
- `@workspace/db/config`
- `@workspace/db/adapters/node-postgres`
- `@workspace/db/adapters/libsql`
- `@workspace/db/migrations`
- `@workspace/db/seeds`

Example (server-only):

```ts
import { createNodePostgresDbFromUrl } from "@workspace/db/adapters/node-postgres";

const db = createNodePostgresDbFromUrl(process.env.DATABASE_URL ?? "");
```
