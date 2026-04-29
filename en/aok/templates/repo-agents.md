# Project AGENTS.md

## Project Overview

- This project is `[what the product/tool does]`.
- Primary users are `[user type or usage context]`.
- This project prioritizes `[stability/speed/auditability/UX/operational convenience/etc.]`.

## Codebase Structure

| Path | Role | Check Before Editing | Risk / Notes |
|---|---|---|---|
| `[path]` | `[frontend/backend/data/infra/shared library/etc.]` | `[related docs/tests/dependencies]` | `[why changes here are risky]` |

- Clearly separate frontend, backend, data, infrastructure, and shared library boundaries.
- Mark high-risk areas such as public APIs, DB schema, auth/authz, payments, deployment, build, and CI.
- If specific documents or tests must be read before editing an area, list them here.

## Common Commands

- Install: `[command]`
- Full dev server: `[command]`
- Full build: `[command]`
- Full verification or the closest local equivalent to CI: `[command]`

Area-specific lint, typecheck, test, and single-test commands follow the relevant nested `AGENTS.md`.

## Verification Routing

| Change Area | Instructions To Read First | Notes |
|---|---|---|
| Frontend | `[example: apps/web/AGENTS.md]` | UI, routing, state, style changes |
| API / Backend | `[example: apps/api/AGENTS.md]` | request/response, auth, server logic |
| DB / Data | `[example: packages/db/AGENTS.md]` | schema, migrations, seeds, queries |
| Infra / Deployment / CI | `[example: infra/AGENTS.md or docs/deploy.md]` | deployment, build, workflows |
| Docs | `[example: docs/AGENTS.md or .agents/workflows/docs-change.md]` | docs structure, ADR, policy changes |

- If multiple areas are changed, check all relevant nested `AGENTS.md` verification rules.
- If an area has no nested `AGENTS.md`, inspect related package scripts, README, and existing CI config, then report executable verification commands to the user.
- If verification commands cannot be found, do not invent them. Report the candidates and uncertainty.

## Document Map

List only documents that the current project actually uses as references. Do not list documents that do not exist or future candidates.
Manage general project documents in this document map. Manage agent instructions, workflows, and project-specific skills in `.agents/INDEX.md`.

| Document | Path | Status | Source Status | Read When | Update When |
|---|---|---|---|---|---|
| `[document name]` | `[path]` | active | source of truth / reference | `[read condition]` | `[update condition]` |

Read only the documents relevant to the task.

### Additional Documentation Governance Candidates

Review these only when documentation governance is needed. Default paths and structures follow AOK `file-structure.md`. List a document in the map above only when it exists or is currently used as a reference.

| Candidate | Role | Add To Document Map When |
|---|---|---|
| ADR | product, architecture, UX, data, and operations decisions | it is the source of truth for current decisions |
| Current status | current operating state, verification baseline, deployment/external dependencies, remaining risks | it must be checked at the start of relevant work |
| Version history | versions, release baselines, deployment artifacts | the project has version or release baselines to manage |
| Work log | historical work used for recovery, rollback, incident investigation, or regression tracing | it is a special-case reference, not a default read |
| Archive | deprecated, backup, and original reference material | it is preserved history, not current source of truth |
| Superpowers outputs | specs, plans, review results | an output has been registered as an official reference |

`docs/current-status.md` should contain only the current operating baseline. Put past release changes in `docs/VERSION_HISTORY.md`, recovery or rollback work history in `docs/work-log.md` when needed, and decision rationale in ADRs.

`docs/work-log.md` is not created by default and is not read at the start of ordinary work. Create it as a history sink only when long-running operational notes repeat and cannot be tracked well elsewhere. Read it only for rollback, recovery, incident investigation, or regression tracing.

For ADR path and domain examples, follow AOK `file-structure.md` and the `adr.md` template.

## Document Map Maintenance Rules

Project documents age like code. If the document map no longer matches the actual source-of-truth documents, do not trust the map.

### What To Index

Index only:

- Current policy documents
- Product, architecture, API, deployment, data, and operations reference documents
- Repeatedly used work guides
- Documents that are the current source of truth for decisions

Do not index by default:

- One-off research notes
- Temporary work logs
- Old drafts
- Backups
- References inside archive
- Intermediate agent outputs that are not official references

### Update When

Update the document map in the same task when:

- A new source-of-truth document is created.
- A source-of-truth document is moved, renamed, or deleted.
- A document is no longer source of truth.
- A document is moved into `docs/archive/`.
- Product policy, API contract, deployment procedure, data structure, or operations rule changes.
- Document conflicts are resolved by choosing one document as primary.

### Document Status

Documents in the map use one of these statuses:

- `active`: current reference document
- `draft`: draft under review
- `deprecated`: no longer source of truth, but kept for transition reference
- `archived`: preserved for history

Do not use `deprecated` or `archived` documents as the source for new work.

## Work Procedure Documents

- Create `.agents/workflows/*.md` only in projects that use Superpowers.
- For complex tasks, check `.agents/INDEX.md` and read only the relevant workflow.
- Do not read all workflow documents by default.

## Agent Instruction File Governance

The following files are managed policy files:

- `AGENTS.md`
- `**/AGENTS.md`
- `.agents/**`

These files have separate rules depending on change type.

### Changes Allowed Without Approval

The following are meaning-preserving cleanup changes and may be done without user approval:

- Typo fixes
- Broken internal link fixes
- Path corrections after actual file moves
- Clearly outdated date or filename corrections
- Table formatting and Markdown formatting cleanup
- Filling missing metadata for already-approved files in INDEX
- Marking deleted files as `deprecated` or `archived` in INDEX

The meaning must not change. If meaning may change, treat it as approval-required.

### Changes Requiring User Approval

The following require user approval:

- Creating a new root or nested `AGENTS.md`
- Creating a new `.agents/workflows/*.md`
- Changing behavior rules in existing instructions
- Adding, removing, or changing verification commands
- Changing scope
- Changing owner or responsibility boundaries
- Adding, removing, or reordering workflow steps
- Changing document creation policy, approval policy, or risky-work policy
- Changing required or forbidden agent behavior

### Changes Allowed By Explicit Request

If the user explicitly says "modify this instruction", "add this workflow", or "make this structure", changes may be made within that requested scope.

Do not create additional instructions or workflows beyond the requested scope without proposing them first.

### Ambiguous Cases

If it is unclear whether a change is cleanup or a policy change, treat it as a policy change and propose it first.

If a new nested `AGENTS.md`, meaning change to existing instructions, or meaning change to workflow documents seems necessary, do not edit immediately. First propose it using `.agents/INDEX.md` or the AOK `agent-change-proposal.md` template.

After explicit approval, create or meaningfully change the file. Update `.agents/INDEX.md` in the same task.

## Placeholder Handling

Applied `AGENTS.md` files must not contain unresolved placeholders such as `[command]`, `[path]`, `[document]`, or TODO.

Unknown values go into a separate section:

```md
## Items To Confirm

- `[item]`: `[why confirmation is needed]`
```
