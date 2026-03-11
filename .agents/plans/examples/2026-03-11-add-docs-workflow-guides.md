# Plan: Add Self-Contained Docs and Feature-Branch Workflow Guides

## Scope
Create comprehensive user and developer documentation under `docs/` that explains:

- how the self-contained docs system works
- how the feature-branch + scoped-plan workflow works
- how this keeps repo history and PRs clean for community collaboration
- which concrete benefits users receive from this workflow quality model

## Steps
1. Add a new feature docs area `docs/workflow/` with:
   - `README.md`
   - `developers.md`
   - `users.md`
2. Add Mermaid docs under `docs/mermaid/` for:
   - docs-system structure and update flow
   - community contribution and PR lifecycle
3. Cross-link all related docs in both directions:
   - `docs/README.md` -> new workflow docs + Mermaid files
   - `docs/workflow/README.md` -> users/developers + Mermaid files
   - Mermaid docs -> docs home + workflow docs
4. Update `docs/project/README.md` and root `README.md` so the new workflow docs are discoverable from existing entry points.
5. Add a concise `.agents` learning + prompt entry if reusable process guidance emerges.

## Security Considerations
- Keep the workflow docs explicit about server-side authz and secret handling responsibilities.
- Reinforce documentation-as-contract to reduce unsafe or undocumented changes.

## Environment Variables
No new environment variables are introduced by this documentation change.
