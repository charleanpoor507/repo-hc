# Agents Docs Guide

## Purpose
This folder stores reusable agent knowledge for consistent, safe, and fast collaboration.

- `learnings/`: proven solutions, root causes, and implementation outcomes
- `prompts/`: original user prompts and execution context (sanitized)
- `rules/`: writing and safety policies that all agent docs must follow
- `skills/`: task-specific playbooks defined by `SKILL.md` files
- `default_scopilot_instructions.md`: default execution guidance for Scopilot

## How To Use
1. Read relevant rules first.
2. Check `skills/` and apply matching skills before implementation.
3. When creating a new learning, also store the source prompt.
4. Cross-link related files (`learning` <-> `prompt` and both to this README).
5. Mask all sensitive data before saving any content.
6. Keep all text in English unless explicitly requested otherwise.
7. Update this README whenever files or conventions in `.agents` change.

## Naming Convention
- Use numbered files to keep ordering stable: `01_*`, `02_*`, `03_*`, `04_*`, `05_*`, `06_*`, `07_*`, `08_*`.
- Keep titles short and specific to one topic.

## Current Index

### Plans
- [global-drizzle-package-plan.md](./global-drizzle-package-plan.md)
- [plans/2026-03-11-rename-backend-to-admc.md](./plans/2026-03-11-rename-backend-to-admc.md)
- [plans/2026-03-11-add-api-hono-docs.md](./plans/2026-03-11-add-api-hono-docs.md)
- [plans/2026-03-11-add-admc-tauri-dev-exclusion-and-docs.md](./plans/2026-03-11-add-admc-tauri-dev-exclusion-and-docs.md)
- [plans/2026-03-11-add-docs-workflow-guides.md](./plans/2026-03-11-add-docs-workflow-guides.md)

### Learnings
- [01_turborepo_tanstack-start_peer-deps.md](./learnings/01_turborepo_tanstack-start_peer-deps.md)
- [02_shared-drizzle-workspace-package.md](./learnings/02_shared-drizzle-workspace-package.md)
- [03_app-rename-backend-to-admc.md](./learnings/03_app-rename-backend-to-admc.md)
- [04_exclude-admc-tauri-from-default-turbo-dev.md](./learnings/04_exclude-admc-tauri-from-default-turbo-dev.md)
- [05_self-contained-docs-and-feature-branch-workflow.md](./learnings/05_self-contained-docs-and-feature-branch-workflow.md)

### Prompts
- [01_turborepo_tanstack-start_peer-deps.md](./prompts/01_turborepo_tanstack-start_peer-deps.md)
- [02_shared-drizzle-workspace-package.md](./prompts/02_shared-drizzle-workspace-package.md)
- [03_app-rename-backend-to-admc.md](./prompts/03_app-rename-backend-to-admc.md)
- [04_exclude-admc-tauri-from-default-turbo-dev.md](./prompts/04_exclude-admc-tauri-from-default-turbo-dev.md)
- [05_add-workflow-docs-for-community-quality.md](./prompts/05_add-workflow-docs-for-community-quality.md)

### Rules
- [01_mask_sensitive-data.md](./rules/01_mask_sensitive-data.md)
- [02_write-in-english.md](./rules/02_write-in-english.md)
- [03_keep-readme-updated.md](./rules/03_keep-readme-updated.md)
- [04_use-shadcn-from-packages-ui.md](./rules/04_use-shadcn-from-packages-ui.md)
- [05_use-dedicated-branch-for-large-features.md](./rules/05_use-dedicated-branch-for-large-features.md)
- [06_update-mermaid-on-architecture-changes.md](./rules/06_update-mermaid-on-architecture-changes.md)
- [07_require-comprehensive-feature-docs.md](./rules/07_require-comprehensive-feature-docs.md)
- [08_require-feature-plan-and-env-docs.md](./rules/08_require-feature-plan-and-env-docs.md)
- [AGENTS.override.md](./rules/AGENTS.override.md)

### Skills
- [better-auth-best-practices/SKILL.md](./skills/better-auth-best-practices/SKILL.md)
- [create-auth-skill/SKILL.md](./skills/create-auth-skill/SKILL.md)
- [email-and-password-best-practices/SKILL.md](./skills/email-and-password-best-practices/SKILL.md)
- [organization-best-practices/SKILL.md](./skills/organization-best-practices/SKILL.md)
- [two-factor-authentication-best-practices/SKILL.md](./skills/two-factor-authentication-best-practices/SKILL.md)

### Additional
- [default_scopilot_instructions.md](./default_scopilot_instructions.md)
