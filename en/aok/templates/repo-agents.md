# Project AGENTS.md

Use this as the minimal root `AGENTS.md` template. Keep it short enough to read every session. Prefer 50-100 lines for small projects.

Do not paste optional workflows, long document governance rules, work logs, ADR content, or archive summaries into this file. Put optional details behind explicit read conditions.

## Project

- Purpose: `[what the product/tool does]`
- Primary users: `[user type or usage context]`
- Current priority: `[stability/speed/auditability/UX/operational convenience/etc.]`

## Before Work

- Read this file first.
- Read only the task-relevant documents listed below.
- Do not create, move, archive, deprecate, or delete project documents without approval.
- If requirements, docs, or verification commands conflict, report the conflict before changing files.

## Common Commands

- Install: `[command]`
- Test: `[command]`
- Lint/typecheck: `[command]`
- Build: `[command]`

If a command is unknown, do not invent it. Put it in `Items To Confirm`.

## Verification Routing

| Change | Read First | Verify With |
|---|---|---|
| Code | `[path or "none"]` | `[test/lint/typecheck/build command]` |
| Docs | `[path or "none"]` | `[link check or affected-reference check]` |
| Risky change | `[path or approval rule]` | `[rollback/CI/deploy verification]` |

If multiple areas are changed, apply every relevant verification route.

## Docs To Read

List only existing documents that the project actually uses. Keep read conditions specific.

| When | Read |
|---|---|
| Feature work | `[path or none]` |
| Bug fix | `[path or none]` |
| Architecture or product decision | `[path or none]` |
| Deployment, CI, auth, DB, or other risky work | `[path or none]` |
| Rollback, recovery, incident investigation, or regression tracing | `[path or none]` |

Read only the documents relevant to the task.

## Optional Extensions

- Add [document-map.md](document-map.md) only when documents need source-of-truth status, explicit read conditions, or review state.
- Add [agent-instruction-governance.md](agent-instruction-governance.md) only when agent instruction files need approval rules.
- Add `.agents/INDEX.md` only when workflows, nested `AGENTS.md`, or project-specific skills need routing.
- Add `.agents/workflows/*.md` only for projects that use Superpowers and have repeated task procedures.

## Items To Confirm

- `[item]`: `[why confirmation is needed]`
