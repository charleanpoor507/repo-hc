# Workflow Docs System (Mermaid)

Back to docs:

- [Docs Home](../README.md)
- [Workflow Documentation](../workflow/README.md)
- [Workflow Developer Guide](../workflow/developers.md)
- [Workflow User Guide](../workflow/users.md)

## Self-Contained Documentation Structure

```mermaid
flowchart LR
  HOME["docs/README.md"] --> FEATURE["docs/<feature>/README.md"]
  FEATURE --> DEV["docs/<feature>/developers.md"]
  FEATURE --> USER["docs/<feature>/users.md"]
  FEATURE --> MMD["docs/mermaid/*"]
  AGENTS[".agents/ rules + plans + learnings"] --> DEV
  AGENTS --> FEATURE
```

## Documentation Sync Workflow

```mermaid
flowchart LR
  CHANGE["Code / Behavior Change"] --> CHECK["Check Impact Scope"]
  CHECK --> DOCS["Update Feature Docs"]
  DOCS --> DIAGRAMS["Update Mermaid Diagrams"]
  DIAGRAMS --> INDEX["Update docs/README links"]
  INDEX --> REVIEW["PR Review"]
```
