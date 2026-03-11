# AGENTS.md

## Purpose

This repository must be maintained with a strong focus on:

- security
- modularity
- maintainability
- reusability
- clear architectural boundaries
- long-term project health

When making changes, always prefer clean, well-structured, secure solutions over quick or overly convenient implementations.

This is a **TanStack Start** project inside a **Turborepo**. All work must respect repo boundaries, shared package architecture, and a strict separation of concerns.

---

## Required First Step

Before making changes, always check:

- `/.agents/rules`
- `/.agents/learnings`
- `/.agents/prompts`
- `/.agents/skills`

These folders contain repository-specific instructions, conventions, previous learnings, implementation notes, and reusable prompt context.

If relevant guidance already exists there, follow it.

If new useful knowledge is discovered during the task, document it appropriately in `/.agents` so the repository improves over time.

### Skills Usage (`/.agents/skills`)

The `/.agents/skills` folder contains reusable task-specific playbooks.
Each skill is defined by its own `SKILL.md`.

When a task matches a skill topic, read and apply that skill before implementing changes.

Current skills in this repository:

- none

If a relevant skill exists, treat it as implementation guidance (not optional reference).
If no relevant skill exists and a repeatable pattern emerges, add a new skill under `/.agents/skills`.

---

## Documentation Maintenance

The agent should actively help maintain the internal project knowledge base.

When useful, create or update files under `/.agents`, especially in areas such as:

- new implementation learnings
- architecture notes
- security notes
- recurring patterns
- prompt refinements
- rules for future work
- mistakes to avoid
- project-specific conventions

Only add documentation when it provides real future value. Do not create noisy or redundant files.

Documentation should be:

- concise
- actionable
- clearly named
- easy to discover
- specific to the repository

Prefer updating existing files over creating unnecessary new ones, unless a new file is clearly the better structure.

### Documentation Sync Requirement (Mandatory)

To avoid stale documentation, keep `/docs` and especially `/.agents` in sync with implementation changes.

- If behavior, architecture, setup, conventions, rules, or reusable patterns change, update the relevant docs in the same change.
- If architecture or workflow changes, update Mermaid diagrams in `docs/mermaid/` (or the relevant architecture doc) in the same change.
- For feature-level documentation, keep `docs/<feature>/developers.md`, `docs/<feature>/users.md`, and `docs/<feature>/README.md` aligned when relevant.
- Do not leave documentation updates for "later" when the current change affects documented behavior.
- Treat documentation updates as part of the definition of done for relevant changes.
- If no documentation update is needed, explicitly verify that existing docs are still accurate.

### Feature Branch and Plan Requirement (Mandatory)

- Every new feature must be implemented on a dedicated branch (do not develop features directly on `main`).
- Every new feature must start with a scoped implementation plan before coding begins.
- Prefer storing plans in `/.agents/plans` using clear, discoverable filenames.

### AI Usage Requirement (Mandatory)

- When AI tooling is used for planning, implementation, review, or documentation, `AGENTS.md` is required baseline guidance.
- AI-assisted work must follow this file and the linked guidance in `/.agents` (`rules`, `learnings`, `prompts`, `skills`).

---

## General Development Rules

- Always prefer small, focused, composable functions.
- Avoid large, monolithic files.
- Keep logic split into clearly named modules.
- Prefer readability, maintainability, and security over clever or condensed code.
- Follow existing repository conventions unless they conflict with these rules.
- Keep implementations minimal, robust, and easy to review.
- Make the codebase cleaner with every change.

---

## Package Manager

- Use **pnpm** by default.
- Do not use npm or yarn unless explicitly required by the repository.
- Prefer `pnpm install`, `pnpm add`, `pnpm remove`, and `pnpm run`.

---

## Monorepo / Turborepo Rules

- Respect package boundaries at all times.
- Do not mix app-specific code into shared packages unless it is truly reusable.
- Keep responsibilities clearly separated across apps, packages, services, and shared utilities.
- Reusable code should live in the correct shared package, not be duplicated across apps.
- Avoid hidden coupling between workspace packages.
- Keep imports intentional and architecture-aware.

---

## Security Requirements

Security is a core requirement, not an optional improvement.

Always design and implement changes with a **security-first mindset**.

### Core security rules

- Never expose secrets, tokens, API keys, credentials, or private configuration to the client.
- Never move sensitive logic to the frontend if it can be handled securely on the server.
- Always keep authentication, authorization, and sensitive business logic on the server side.
- Prefer server functions, server handlers, or server-only modules wherever possible for protected operations.
- Treat all client input as untrusted.
- Validate all external and user-provided input.
- Sanitize data where appropriate.
- Enforce authorization checks at the server boundary.
- Do not rely on the client for permission checks.
- Do not trust hidden UI states as security controls.
- Avoid leaking internal error details to clients.
- Use least-privilege principles wherever possible.
- Avoid unnecessary data exposure in API responses.
- Only return the minimum required data to the client.

### Secrets and environment handling

- Secrets must remain server-side only.
- Do not import server-only secrets into client code.
- Do not expose private environment variables to the browser.
- Be explicit about public vs private environment usage.
- Audit code paths carefully when working with runtime configuration.
- Any new environment variable must be added to `.env.example` in the same change.
- New environment variables must be documented in the corresponding developer docs (purpose, scope, format, and fallback behavior).

### Authentication and authorization

- Authentication logic must be clearly separated from UI concerns.
- Authorization must be enforced on the server, not inferred from frontend behavior.
- Protect privileged actions with explicit server-side checks.
- Do not assume authenticated users are authorized for all resources.
- Validate ownership, tenant scope, role scope, and access rights explicitly where applicable.

### Business logic protection

- Sensitive business rules must not live only in client components.
- Pricing, account rules, permissions, state transitions, and protected workflows must be enforced on the server.
- The client may render state, but the server must decide what is allowed.

---

## Architecture and Separation of Concerns

Maintain a **strict separation** between:

- frontend/UI
- backend/server logic
- authentication and authorization
- business/domain logic
- infrastructure concerns
- shared types
- reusable utilities

### Required separation rules

- UI components should not contain sensitive business logic.
- UI components should not contain authentication enforcement logic beyond presentation concerns.
- Business logic should live in dedicated services or domain modules.
- Authentication and authorization should be handled in dedicated backend/server layers.
- API access and server actions should be kept separate from presentational code.
- Shared types should be extracted into dedicated type files or folders.
- Utilities should remain focused and not become hidden business-logic containers.

---

## TanStack Start Guidance

For TanStack Start projects:

- Prefer server-side execution for protected operations wherever possible.
- Use server functions or equivalent server-only patterns for sensitive workflows.
- Keep client components lean and focused on rendering and interaction.
- Avoid pushing data access, auth decisions, or sensitive workflow logic into the client.
- Be explicit about what runs on the server and what runs on the client.
- Keep boundaries obvious in file structure and naming.

---

## File Size and Structure

- Keep files small and focused.
- Avoid mixing unrelated concerns in the same file.
- If a file grows too large, split it into smaller modules.
- Prefer multiple small files over one large file.
- Do not place business logic, UI logic, types, constants, and helpers all in one file.

### Preferred structure principles

- Components should only contain component-related logic.
- Services should contain business logic, domain workflows, or API orchestration.
- Types should be extracted into dedicated type files or folders when reused or when they improve clarity.
- Utilities should contain small reusable helpers.
- Constants should be extracted instead of repeated inline values.
- Reusable content should be centralized instead of duplicated.

---

## Functions

- Keep functions small and single-purpose.
- A function should do one thing well.
- Extract nested or repeated logic into helper functions.
- Prefer descriptive function names over comments that explain unclear logic.
- Avoid long functions with many branches.
- Break complex logic into smaller helpers or service methods.
- Prefer explicit inputs and outputs.
- Avoid hidden side effects unless clearly necessary and documented.

---

## Components

- Build components to be reusable whenever appropriate.
- Avoid hardcoding content that should be configurable through props, data, or shared config.
- Keep components small and composable.
- Separate presentation from domain logic wherever practical.
- Avoid oversized “do everything” components.
- Extract repeated UI patterns into shared components.
- Reuse existing components before creating new ones.

---

## Reusable Content

- Repeated text, labels, metadata, configuration objects, and UI content should be extracted into reusable structures where appropriate.
- Avoid duplicating the same content across multiple files.
- Prefer central definitions for reusable content, shared metadata, and common UI text.

---

## Types

- Create and maintain small, focused type definitions.
- Prefer dedicated type files or folders for shared or important types.
- Do not leave large inline type definitions inside unrelated files if they are reused or reduce readability.
- Keep domain types organized and easy to discover.
- Prefer clear naming for types and interfaces.
- Separate API types, domain types, and UI/component prop types when useful.

### Type organization

- Place reusable types in a dedicated `types/` folder or domain-specific type files.
- Keep type files small and grouped by responsibility.
- Avoid giant catch-all type files.

---

## Services

- Business logic should be moved into clearly named services or domain modules.
- API calls, domain workflows, transformations, and side effects should generally not live inside UI components.
- Services should have focused responsibilities.
- Split large services into smaller service modules if needed.
- Keep services predictable, testable, and easy to review.

---

## Testing

- Add tests for new functionality whenever reasonable.
- When creating new logic, also create the corresponding test files.
- Cover important behavior, edge cases, and regression-prone logic.
- Avoid shipping non-trivial logic without tests.
- If a bug is fixed, add or update a test to cover that case.
- Prefer small, readable tests with clear intent.

### Test expectations

Create test files for:

- new services
- utility functions
- important security-sensitive logic
- authentication-related logic
- authorization checks
- complex component behavior
- bug fixes

Keep tests focused and easy to read.

---

## Security Review Expectations

When touching authentication, authorization, secrets, data access, or protected workflows, also review:

- whether secrets remain server-only
- whether the client receives unnecessary data
- whether authorization is enforced server-side
- whether business logic is improperly placed in UI code
- whether inputs are validated
- whether errors leak sensitive details
- whether the implementation follows least-privilege principles

---

## Duplication

- Avoid duplication whenever possible.
- If logic or UI appears more than once, consider extracting it.
- Reuse existing helpers, services, components, and types before introducing new ones.
- Prefer shared abstractions only when they improve clarity, not abstraction for its own sake.

---

## Naming

- Use clear, descriptive, and consistent names.
- File names should reflect their responsibility.
- Avoid vague names when a more specific name is possible.
- Components, services, and types should be easy to locate by name.
- Use naming that makes server/client boundaries obvious where useful.

---

## Imports and Organization

- Keep imports organized and clean.
- Remove unused imports.
- Group related code logically.
- Maintain a predictable folder and file structure.
- Favor consistency over personal preference.
- Avoid imports that blur architecture boundaries.

---

## Change Style

When making changes:

- Prefer targeted, minimal edits.
- Do not refactor unrelated areas unless necessary.
- If a file is already too large, improve it incrementally by extracting focused parts.
- Preserve behavior unless the task explicitly requires changing it.
- Keep the codebase cleaner, safer, and more structured after every change.

---

## What to Prefer

Prefer:

- small files
- small functions
- reusable components
- reusable content
- dedicated services
- dedicated types
- explicit server/client boundaries
- secure server-side handling
- strict auth separation
- test coverage
- pnpm workflows
- architecture-aware documentation updates in `/.agents`

Avoid:

- huge files
- massive components
- mixed concerns
- duplicated logic
- client-side secrets
- client-side-only protection for sensitive flows
- inline reusable types everywhere
- untested non-trivial logic
- unnecessary complexity
- undocumented learnings when they would help future work

---

## Default Working Approach

For every implementation, aim for the following:

1. Check `/.agents` for existing rules, learnings, and prompts.
2. Understand the feature, fix, or request.
3. Identify security implications first.
4. Keep the solution as small, clean, and safe as possible.
5. Maintain strict separation between UI, server logic, auth, and business logic.
6. Extract reusable logic where appropriate.
7. Create or update types in the proper location.
8. Move sensitive and domain-critical logic to server-side services or server functions.
9. Add or update tests.
10. Update `/.agents` if meaningful new learnings or rules emerged.
11. Keep files organized and reasonably small.
12. Use pnpm commands and conventions.

---

## Final Standard

Every change should move the project toward:

- better security
- stronger server-side protection
- clearer separation of concerns
- better modularity
- smaller units
- stronger reusability
- cleaner architecture
- better testability
- easier maintenance
- better internal documentation

## Strict Rules

- Never create unnecessarily large files.
- Split code early instead of waiting until files become difficult to maintain.
- Do not place business logic directly inside components unless it is truly trivial.
- Extract shared types into dedicated type files.
- Extract repeated logic into services or utilities.
- Add test files for new logic by default.
- Prefer reusable and composable solutions over one-off implementations.
- Use pnpm exclusively unless the repository explicitly requires something else.
