# Agent Work Procedure Index

Read only the documents relevant to the current task. Do not read all workflow documents by default.
This file indexes only agent instruction files, workflows, and project-specific skills. Manage general project documents such as product docs, operations docs, ADRs, releases, and work logs through root `AGENTS.md` document routing or the optional document map section.

## Common Routing

- If the user instruction is unclear, requirements conflict, or a risky assumption appears, ask the minimum necessary question first.
- If an implementation plan has already been approved, execute that plan instead of redesigning the work.
- For medium-sized or high-risk work, consider a separate workspace, rollback method, and impact scope first.
- Even when two or more tasks are independent, parallelize only if the user explicitly allows parallel or subagent work.
- Before claiming completion, verify actual results.
- If the project does not use Superpowers, do not use `.agents/workflows/*.md`.

## Workflow Priority Routing

Use this table only in projects where Superpowers workflows have been applied. If multiple conditions match, follow the higher-priority row first.

| Priority | Condition | Workflow To Read First |
|---|---|---|
| 1 | DB, migration, auth/authz, payments, security, deployment, CI, dependencies, or build config change | `.agents/workflows/risky-change.md` |
| 2 | Bug reproduction, regression, incident, exception behavior fix | `.agents/workflows/bugfix.md` |
| 3 | Review feedback handling | `.agents/workflows/review-feedback.md` |
| 4 | Documentation, policy, ADR, or agent instruction change | `.agents/workflows/docs-change.md` |
| 5 | Structure improvement that should preserve external behavior | `.agents/workflows/refactor.md` |
| 6 | Research, comparison, technical choice, or decision | `.agents/workflows/research-decision.md` |
| 7 | Feature addition or ordinary behavior change | `.agents/workflows/feature-change.md` |
| 8 | Repeated failure that may need automation, docs, or skill extraction | `.agents/workflows/repeated-failure.md` |

## INDEX Maintenance Rules

`.agents/INDEX.md` is the current map of agent documents. If it differs from the actual file structure, do not trust the INDEX.

## Template Application Rules

When applying this file as a real project `.agents/INDEX.md`, do not leave example placeholders in place.

- Replace `[YYYY-MM-DD]`, `[work type]`, `[filename]`, `[skill-name]`, and `[when to use it]` with real values.
- If there is no real value, remove the example row or replace it with a `none` row.
- Do not list workflows or skills in `Workflow Documents` or `Project-Specific Skills` unless the user approved them.
- Keep AOK-provided candidates only in the `Available Workflow Candidates` table.

### Update When

Update this file in the same task when:

- `AGENTS.md` or nested `AGENTS.md` is created.
- An agent instruction file is deleted or moved.
- A workflow document is added, deleted, or renamed.
- A project-specific skill is added, deleted, or renamed.
- The scope of an instruction file changes.
- A document owner or last review date changes.
- A workflow becomes deprecated.

### Index Status

Each agent instruction file and workflow document uses one of these statuses:

- `active`: current official document
- `draft`: proposal or experiment
- `deprecated`: no longer used for new work
- `archived`: preserved for history

Do not use `deprecated` or `archived` documents as the default source for new work.

### Drift Signals

Check the INDEX first if:

- A file listed in the INDEX does not exist.
- A workflow file exists but is not listed in the INDEX.
- Document scope differs from the actual repo structure.
- The last review date is old and the repo structure changed recently.
- An agent is working from a document that differs from the INDEX.

## Approved Instruction Files

Agent instruction files not listed here require user approval before creation.

| Path | Status | Scope | Purpose | Owner | Last Review | Notes |
|---|---|---|---|---|---|---|
| `AGENTS.md` | active | entire repo | project default instructions | Maintainers | `[YYYY-MM-DD]` |  |

## Workflow Documents

List only workflows that have actually been created or approved by the user.

| Work Type | Status | Document |
|---|---|---|
| `[work type]` | active | `.agents/workflows/[filename].md` |

If no workflow has been approved, remove the example row above and write:

| Work Type | Status | Document |
|---|---|---|
| none | - | - |

## Available Workflow Candidates

The items below are candidates provided by AOK. Only applied items should be listed in the `Workflow Documents` table.
Do not copy every candidate into the active workflow list. Select only workflows that will actually be used after checking repetition frequency, failure cost, Superpowers usage, and recommended companion workflows.

| Work Type | Candidate Document | Repetition Signal | Failure Cost | Superpowers Required | Recommended Companion |
|---|---|---|---|---|---|
| Feature or behavior change | `.agents/workflows/feature-change.md` | Feature or behavior changes repeat and need requirement/scope/verification control | medium | yes | `risky-change.md` when high-risk features are common |
| Bug fix | `.agents/workflows/bugfix.md` | Reproduction, regression checks, and root-cause work repeat | medium | yes | `risky-change.md` when incidents or operational regressions are common |
| Refactor | `.agents/workflows/refactor.md` | Structure changes that must preserve external behavior repeat | medium | yes | `review-feedback.md` for large shared-boundary changes |
| Documentation, policy, or ADR change | `.agents/workflows/docs-change.md` | Document meaning, source of truth, ADRs, or agent instructions change repeatedly | low to medium | yes | Use `application-guide.md` for first-time AOK adoption instead of this workflow |
| Config, build, CI, dependency, deployment, or DB change | `.agents/workflows/risky-change.md` | DB, deployment, CI, secret, auth/authz, payment, or security changes repeat or have high failure cost | high | yes | Create first for high-risk features, operational bugs, and migration work |
| Research or technical decision | `.agents/workflows/research-decision.md` | Comparative research and decision rationale repeat | medium to high | yes | `feature-change.md` or `risky-change.md` if implementation follows |
| Review feedback handling | `.agents/workflows/review-feedback.md` | Review feedback needs validity checks and scope control before changes | medium | yes | Can pair with feature or refactor workflows |
| Repeated failure or project-specific skill extraction | `.agents/workflows/repeated-failure.md` | The same failure repeats and tests, lint, or CI cannot prevent it alone | medium to high | yes | Candidate project-specific skill after the judgment procedure stabilizes |

## Project-Specific Skills

List only project-specific skills that have actually been created or approved by the user.

| Skill | Status | Document | Use When |
|---|---|---|---|
| `[skill-name]` | active | `.agents/skills/[skill-name]/SKILL.md` | `[when to use it]` |

If no project-specific skill has been approved, remove the example row above and write:

| Skill | Status | Document | Use When |
|---|---|---|---|
| none | - | - | - |

If project-specific skills become numerous and this table is no longer enough, create `.agents/skills/INDEX.md` after user approval. Do not create a separate skill INDEX by default.
