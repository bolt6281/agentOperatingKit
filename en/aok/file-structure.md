# Recommended File Structure

This document is the source catalog for AOK paths and file roles. Component selection guides, application guides, and templates describe when to use files, but if a default path or structure conflicts, prefer this document.

```text
~/.codex/AGENTS.md (optional)
  Personal global principles applied across all projects.
  Suggest or modify only when the user explicitly selects it.

<repo>/AGENTS.md
  Project structure, common commands, verification routing, document map, and instruction-file governance.

<repo>/.agents/INDEX.md
  Index of workflows and approved agent instruction files.

<repo>/.agents/workflows/*.md
  Task-specific procedure documents such as feature work, bug fixes, and refactors.
  Create only for projects that use Superpowers.

<repo>/.agents/skills/
  Project-specific skills used only when repeated failures or project-specific judgment procedures have stabilized.
  Create or meaningfully modify only after user approval.

<repo>/.agents/skills/INDEX.md (optional)
  Dedicated skill index used only when project-specific skills become numerous.
  By default, use the project-specific skill table in .agents/INDEX.md.

<repo>/<area>/AGENTS.md
  Scope-specific coding rules, design tone, or verification methods.
  Create or meaningfully modify only after user approval.

<repo>/docs/
  Source-of-truth documents, operational notes, and build guides.

<repo>/docs/README.md or <repo>/docs/INDEX.md
  A docs index created only when documents grow enough to need one.
  Include only current source-of-truth documents and repeatedly referenced documents.

<repo>/docs/archive/
  Deprecated documents, backups, and original references.
  Do not use as current source of truth.

<repo>/docs/superpowers/
  Outputs from Superpowers skill workflows.
  Examples: specs, plans, review notes, skill work results.

<repo>/docs/adr.md
  Single ADR source-of-truth document for small projects.

<repo>/docs/adr/INDEX.md
  ADR router used when ADR content grows.
  Track domain, ADR path, status, and when to read it.

<repo>/docs/adr/<domain>/<decision-topic>.md
  Domain-specific decision documents used when ADR content grows.
  Examples: product/notification-policy.md, architecture/app-web-boundary.md, data/job-status-model.md, operations/deployment-policy.md, ux/worker-flow.md.
  Prefer filenames that reveal domain and topic over plain sequential numbering.

<repo>/docs/current-status.md (optional)
  Short current operating baseline, verification baseline, deployment/external dependency snapshot, and remaining risks.
  Do not accumulate work logs or past change history here.

<repo>/docs/VERSION_HISTORY.md
  Major version changes and decision history.

<repo>/docs/work-log.md (optional)
  Historical implementation flow, rollback/recovery references, and long-running operational notes.
  Do not read it at the start of ordinary work; use it as a history sink by default.
  Read it only when rollback, recovery, incident investigation, or regression tracing needs past context.
```
