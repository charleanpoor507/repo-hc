# Turborepo + TanStack Start: Peer-Dependency Learnings

## Links
- README: `../README.md`
- Prompt: `../prompts/01_turborepo_tanstack-start_peer-deps.md`

## Context
During `pnpm install` in a Turborepo with TanStack Start apps (`apps/frontend`, `apps/admc`), peer warnings appeared:

- `unstorage@2.0.0-alpha.6` required `chokidar@^4 || ^5`, but `3.6.0` was found
- `unstorage@2.0.0-alpha.6` required `lru-cache@^11.2.6`, but `5.1.1` was found

The trigger was `nitro@3.0.260311-beta` (indirectly via app dependencies).

## Root Cause
`nitro` pulled an alpha version of `unstorage` whose peer dependencies were not automatically satisfied by the existing transitive resolution.

## Proven Fix
Add explicit compatible versions in **both** apps:

- `chokidar: ^4.0.3`
- `lru-cache: ^11.2.2`

Files:

- `apps/frontend/package.json`
- `apps/admc/package.json`

Then run `pnpm install` again so the lockfile is updated.

## Result
The `unstorage` peer warnings disappear after installation.

## Setup Note For Later
If `nitro`/`unstorage` switches again to alpha/beta builds, check the following first:

1. Which peer dependencies `unstorage` currently requires
2. Whether they are already resolved compatibly in the workspace
3. If not: set them explicitly in affected apps (or manage centrally via root `overrides`)
