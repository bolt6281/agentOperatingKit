# Adoption Levels

This document is not a command to create the full AOK structure up front. Adopt only the parts selected through the AOK application interview.

## Level 1. Minimal Adoption

Use when:

- A repo is starting development but its process is not complex yet.
- The project is personal, small, or experimental.
- Agent work is infrequent and document governance is not yet needed.

Create:

- `<repo>/AGENTS.md`

Rules:

- Include only project overview, common commands, and verification methods.
- Do not create `.agents/`, `docs/adr.md`, `docs/VERSION_HISTORY.md`, or `docs/work-log.md`.
- Promote workflow documents only when the same procedure repeats.

## Level 2. Workflow Adoption

Use when:

- The project repeatedly uses LLM agents for work.
- Feature work, bug fixes, and refactors happen regularly.
- The project needs work pipeline consistency and context savings.
- The project has installed or will install Superpowers skills.

Create:

- `<repo>/AGENTS.md`
- `<repo>/.agents/INDEX.md`
- Only the needed `.agents/workflows/*.md` files

Rules:

- Root `AGENTS.md` acts as a router.
- Long procedures become workflow documents only in Superpowers-enabled environments.
- Create only workflows that are actually used.
- Manage ordinary project documents through the root `AGENTS.md` document map; do not create `docs/INDEX.md` by default.
- Do not apply Level 2 workflow structure to projects that do not use Superpowers.

## Level 3. Documentation Governance

Use when:

- The project is long-running.
- Multiple people or multiple agents work on the repo.
- Source-of-truth cleanup, document consistency, and decision history matter.
- Deployment, migrations, policy changes, or other risky work must be controlled.

Create:

- All selected Level 2 files
- Selected Level 3 documentation governance files
- Needed nested `AGENTS.md` files

Use [Recommended File Structure](file-structure.md) for default paths and file roles. This document only decides when Level 3 documents should exist.

Rules:

- Create nested `AGENTS.md` files only when repeated rules and clear scope exist.
- Each instruction file should include owner, scope, and last review date.
- Prefer updating existing documents over adding new documents.
- Index only current source-of-truth documents and repeatedly referenced documents.
- Create `docs/current-status.md` only when the project needs a short current operating baseline, verification baseline, deployment/external dependency snapshot, and remaining risk list.
- Create `docs/work-log.md` only for long-running operational notes that are hard to track in issues, PRs, or plans. Do not read it during ordinary work; read it only for rollback, recovery, incident investigation, or regression tracing.
- Promote a large single `docs/adr.md` into a `docs/adr/` directory structure.
- Prefer domain and topic names over plain numbers for ADR filenames. Examples: `docs/adr/product/notification-policy.md`, `docs/adr/architecture/app-web-boundary.md`, `docs/adr/operations/deployment-policy.md`.
- `docs/adr/INDEX.md` should be a routing table by change area, not just a chronological list.

## Representative Adoption Examples

| Project Situation | Default Recommendation | Files Not To Create | Reason |
|---|---|---|---|
| Small new CLI or personal experiment repo | Level 1: root `AGENTS.md` only | `.agents/`, ADR, VERSION_HISTORY, work-log | Work procedures and document governance have not repeated yet. Leave unconfirmed test/build commands in `Items To Confirm`. |
| Existing small app without Superpowers where README, plan, and architecture docs conflict | Custom: Level 1 + a short `docs/current-status.md` only if needed | `.agents/workflows/`, ADR, VERSION_HISTORY, work-log | Restoring document consistency does not automatically require workflows or full Level 3 structure. Preserve existing docs and mark conflicts as candidates. |
| Public open-source library with existing README, CONTRIBUTING, CHANGELOG, or release notes | Custom: Level 1 + strengthen existing contributor-facing docs | `.agents/workflows/`, `docs/VERSION_HISTORY.md`, ADR, current-status, work-log | Avoid adding burden for external contributors. Prefer improving the existing CHANGELOG, release notes, or CONTRIBUTING before creating a new release-history file. |

## Custom Adoption

If the user selects only specific AOK components, do not force the project into Level 1, 2, or 3. Propose a custom adoption plan.

Custom adoption still follows these rules:

- Propose files to create, modify, move, or archive first.
- Change the meaning of existing documents only after user approval.
- Do not create AOK components the user did not select.

## Mixed Adoption

Existing projects may not fit cleanly into Level 2 or Level 3. For example, a project may not have AOK workflows yet, but may already have Level 3-like documents such as `docs/adr.md`, `docs/current-status.md`, `docs/VERSION_HISTORY.md`, `docs/work-log.md`, or `docs/archive/`.

In this case, do not force full Level 3 adoption. Label the proposal as `Level 2 + preserve existing document governance` or `Custom`.

Rules:

- Do not delete or move existing Level 3-like documents automatically.
- Do not add new Level 3 documents automatically.
- Record existing documents in the root `AGENTS.md` document map with status and source-of-truth role.
- Decide workflow adoption separately based on Superpowers usage and repeated work needs.
- If a large `AGENTS.md` already exists, first propose how to split it into root router, `.agents/INDEX.md`, workflows, and general docs.
- If existing documents are stale or conflicting, leave them as conflict candidates instead of silently choosing a source of truth.

## Promotion Criteria

Consider promoting to the next level when one of these patterns repeats:

- The same work procedure has to be explained repeatedly.
- The agent repeats the same kind of mistake.
- Finding document locations takes time.
- Verification commands or work boundaries are often confused.
- Decision history begins to drift away from the code.

Do not create Level 3 structure up front. Add only the files that are needed when they become needed, and confirm default paths in [Recommended File Structure](file-structure.md).
