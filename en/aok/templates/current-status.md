# Current Status Template

Use this template in long-running projects to keep a short snapshot of the current operating baseline.

`docs/current-status.md` is not a work journal. Put release history in `docs/VERSION_HISTORY.md`, recovery or rollback work history in `docs/work-log.md` when needed, and decision rationale in ADRs. Do not read `docs/work-log.md` at the start of ordinary work.

# Current Status

> Last updated: `[YYYY-MM-DD]`

## Current Baseline

- Product/service state: `[operating / in development / paused / other]`
- Current major version or deployment baseline: `[version, branch, tag, environment]`
- Source-of-truth documents: `[links]`

## Run And Verification Baseline

| Purpose | Command Or Location | Notes |
|---|---|---|
| Install | `[command]` |  |
| Dev server | `[command]` |  |
| Full verification | `[command]` | closest local equivalent to CI |
| Pre-deploy check | `[command or document]` |  |

## Operating State

- Deployment environment: `[environment and access path]`
- External dependencies: `[APIs, DB, storage, auth, payments, etc.]`
- Last confirmed healthy behavior: `[date and verification method]`

## Remaining Risks And Items To Confirm

| Item | Status | Next Action |
|---|---|---|
| `[risk or uncertainty]` | needs confirmation | `[how to confirm]` |

## Update Rules

- Update this document when deployment baseline, verification commands, external dependencies, or operating state changes.
- Do not accumulate detailed progress notes for individual tasks here.
- Do not leave placeholders when applying this to a real project.
