# Workflow Community PR Lifecycle (Mermaid)

Back to docs:

- [Docs Home](../README.md)
- [Workflow Documentation](../workflow/README.md)
- [Workflow Developer Guide](../workflow/developers.md)
- [Workflow User Guide](../workflow/users.md)

## Contribution Lifecycle

```mermaid
flowchart TD
  A["Contributor Idea"] --> B["Create Feature Branch"]
  B --> C["Write Scoped Plan"]
  C --> D["Implement Focused Change"]
  D --> E["Update Docs + Mermaid"]
  E --> F["Run Checks"]
  F --> G["Open PR"]
  G --> H["Maintainer Review"]
  H --> I["Merge"]
```

## Why It Keeps PRs Clean

```mermaid
flowchart LR
  SCOPE["Scoped Branch"] --> CLEAN["No unrelated changes"]
  PLAN["Plan-first"] --> TRACE["Clear intent"]
  DOCSYNC["Docs in same PR"] --> ALIGN["Behavior and docs aligned"]
  ALIGN --> TRUST["Higher user trust"]
  CLEAN --> REVIEW["Faster review"]
  TRACE --> REVIEW
  REVIEW --> QUALITY["Higher merge quality"]
```
