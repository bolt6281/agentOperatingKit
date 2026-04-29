# Document Map Section

Use this optional section only when the project needs document routing, source-of-truth status, or review state. Insert it into root `AGENTS.md` or a project docs index only after the user selects document governance.

Do not list documents that do not exist. Do not list future candidates. Do not read every listed document by default.

## Document Map

| Document | Path | Status | Source Status | Read When | Update When |
|---|---|---|---|---|---|
| `[document name]` | `[path]` | active / draft / deprecated / archived | source of truth / reference / conflict candidate | `[specific read condition]` | `[specific update condition]` |

Read only the documents relevant to the current task.

## Read Frequency

| Frequency | Document Types | Rule |
|---|---|---|
| Always-read | Root `AGENTS.md` | Keep short and safe to read every session |
| Routed-read | `.agents/INDEX.md`, nested `AGENTS.md` | Read only when routing or area-specific rules are needed |
| Task-read | Selected workflow files | Read only for the matching repeated task |
| Reference-read | ADR, current status, version history | Read only when the task depends on that source of truth |
| Exception-read | Work log, archive | Read only for rollback, recovery, incident investigation, regression tracing, or historical preservation |

## Document Status

- `active`: current reference document
- `draft`: draft under review
- `deprecated`: no longer source of truth, but kept for transition reference
- `archived`: preserved for history

Do not use `deprecated` or `archived` documents as the source for new work.

## Maintenance Rules

Update the document map in the same task when:

- A source-of-truth document is created, moved, renamed, or deleted.
- A document is no longer source of truth.
- A document is moved into `docs/archive/`.
- Product policy, API contract, deployment procedure, data structure, or operations rule changes.
- Document conflicts are resolved by choosing one document as primary.

`docs/work-log.md` is not read at the start of ordinary work. Use it as a history sink by default, and read it only for rollback, recovery, incident investigation, or regression tracing.
