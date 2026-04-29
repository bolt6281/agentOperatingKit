# Component Selection Guide

AOK is not a fixed installation sequence and not a larger prompt. Select only the components that fit the project state and the user's goal.

Use [Recommended File Structure](file-structure.md) for default paths and file roles. This document only decides when each component should be selected.

## Selection Principles

- Keep root `AGENTS.md` short enough to read every session. Prefer 50-100 lines for small projects.
- Move optional procedures, historical notes, and governance details behind explicit read conditions.
- Do not create the full AOK structure up front.
- Prefer updating existing documents over adding new documents.
- Do not create components the user did not select.
- Propose files to create, modify, move, or archive first.
- Change the meaning of existing documents only after user approval.
- If existing documents are stale or conflicting, leave them as conflict candidates instead of silently choosing a source of truth.

AOK succeeds when it reduces the amount of context an agent must read for ordinary work. If applying AOK makes every task read more documents by default, the application is wrong.

## Read Frequency Categories

| Category | Files | Default Behavior |
|---|---|---|
| Always-read | Root `AGENTS.md` | Read every session; keep short |
| Routed-read | `.agents/INDEX.md`, nested `AGENTS.md` | Read only when routing or area-specific rules are needed |
| Task-read | Selected workflow files | Read only for the matching repeated task |
| Reference-read | ADR, current status, version history | Read only when the task depends on that source of truth |
| Exception-read | Work log, archive | Read only for rollback, recovery, incident investigation, regression tracing, or historical preservation |

## Component Selection Criteria

| Component | Create Or Update When | Do Not Create When |
|---|---|---|
| Root `AGENTS.md` | The agent needs always-read project overview, common commands, verification routing, or short document routing | README is enough and the project does not need agent operating rules |
| Document map section | Current project documents need read conditions and source-of-truth status | There are only one or two obvious documents and README routing is enough |
| Agent instruction governance section | Agent instruction files are managed policy files and changes need approval rules | The project has only a small root `AGENTS.md` and no repeated instruction changes |
| `.agents/INDEX.md` | Workflows, nested agent instructions, or project-specific skills need an index | Root `AGENTS.md` is enough or the project does not use Superpowers workflows |
| `.agents/workflows/*.md` | The project uses Superpowers and the same work procedure repeats | The project does not use Superpowers or the repeated procedure is not stable yet |
| `.agents/skills/<skill-name>/SKILL.md` | The same failure repeats and requires a stable judgment procedure that tests, lint, CI, or scripts cannot prevent alone | Automation can prevent the issue or the procedure has not stabilized |
| Nested `AGENTS.md` | A specific directory or area has repeated rules, verification commands, or risk boundaries | Repo-wide rules are enough or the scope is unclear |
| `docs/adr.md` or `docs/adr/` | Product, architecture, UX, data, or operations decisions need a source of truth | The content is only work history or existing decision docs are enough |
| `docs/current-status.md` | The project needs a short current operating baseline, verification baseline, deployment/external dependency snapshot, and remaining risks | README or existing operations docs already provide the current baseline |
| `docs/VERSION_HISTORY.md` | Versions, release baselines, and deployment artifacts need one tracking document | Existing CHANGELOG, release notes, GitHub Releases, or CONTRIBUTING are enough |
| `docs/work-log.md` | Long-running operational notes repeat and are hard to track in issues, PRs, or plans | The goal is ordinary work journaling or existing issues, PRs, and deploy logs are enough |
| `docs/archive/` | Non-current documents must be preserved | The user has not approved deletion, movement, or deprecation |
| Global `~/.codex/AGENTS.md` | The user wants personal global instructions aligned with AOK across all projects | The user wants repo-only adoption |

## Workflow Selection Criteria

Select workflow documents only for projects that use Superpowers. Do not create converted workflows that replace skill calls with generic procedures.

| Workflow | Select When | Defer When |
|---|---|---|
| `feature-change.md` | Feature or behavior changes repeat and requirement, scope, or verification control often drifts | Work is limited to one-off small edits |
| `bugfix.md` | Reproduction, root-cause analysis, and regression checks repeat | The fix is a trivial typo or clearly bounded edit |
| `refactor.md` | Internal structure work must be separated from external behavior changes | Feature changes and structure changes are not yet separated |
| `docs-change.md` | Documentation, policy, ADR, or agent instruction changes repeat | AOK is being applied for the first time. Use `application-guide.md` first. |
| `risky-change.md` | DB, migration, deployment, CI, secrets, auth/authz, payments, or security changes have high failure cost | Risky changes are rare or existing approval procedures are enough |
| `research-decision.md` | Research, comparison, technology choices, and decision rationale repeat | The work is simple search or one-off reference gathering |
| `review-feedback.md` | Review feedback often needs validity checks and scope control before changes | Feedback is simple and directly actionable |
| `repeated-failure.md` | A recurring failure needs a decision about automation, documentation, or skill extraction | The issue is one-off or the pattern is not confirmed yet |

## Existing Documents

- Do not delete or move existing documents automatically.
- Do not add new AOK documents automatically.
- If a document map is selected, record existing documents with status and source-of-truth role. Otherwise keep only minimal document routing in root `AGENTS.md`.
- If a large `AGENTS.md` already exists, first propose how to split it into root router, `.agents/INDEX.md`, workflows, and general docs.
- If CHANGELOG or release notes already exist, strengthen them before creating `docs/VERSION_HISTORY.md`.
- If ADR, current status, or archive documents already exist, first mark whether each one is a current reference, preserved history, or conflict candidate.

## Signals For Adding Components

Review whether a related component is needed when these patterns repeat:

- The same work procedure has to be explained repeatedly.
- The agent repeats the same kind of mistake.
- Finding document locations takes time.
- Verification commands or work boundaries are often confused.
- Decision history begins to drift away from the code.
- Rollback, recovery, incident investigation, or regression tracing requires past context that is hard to find.
