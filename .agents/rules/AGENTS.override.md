# AGENTS Override: Prefer New Packages for Reusable Scope

## Links
- README: `../README.md`
- Related Rule: `./03_keep-readme-updated.md`
- Related Rule: `./04_use-shadcn-from-packages-ui.md`

## Override Policy
Whenever it is useful, create a new package in the monorepo instead of implementing app-local-only artifacts.

## Applies To
- Components
- Types and interfaces
- SQL and data-layer modules
- Shared utilities and domain logic

## Decision Heuristic
Prefer a new package when at least one condition is true:

- The code can be reused by more than one app.
- The code represents shared domain or platform behavior.
- The code is likely to grow and should be versioned as an isolated unit.
- The code would otherwise duplicate patterns across apps.

## Exception
Keep implementation app-local only when it is clearly specific to one app and not expected to be reused.
