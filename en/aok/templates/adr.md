# ADR Template

Use this template to record decisions that become references for future work, such as product, architecture, UX, data, and operations decisions.

In small projects, repeat this form inside `docs/adr.md`. When ADRs grow, split them into `docs/adr/INDEX.md` and `docs/adr/<domain>/<decision-topic>.md`.

## `docs/adr/INDEX.md` Example

| Domain | ADR Path | Status | Read When |
|---|---|---|---|
| product | `docs/adr/product/notification-policy.md` | accepted | notification policy, user flow, or feature scope changes |
| architecture | `docs/adr/architecture/app-web-boundary.md` | accepted | app/web/server boundary changes |
| data | `docs/adr/data/job-status-model.md` | proposed | state model, DB schema, or migration changes |

## ADR Body Copy Range

When creating a real ADR file, copy from `ADR Body` through the section before `Application Notes`. Do not include this template explanation or the `docs/adr/INDEX.md` example in the actual ADR body.

## ADR Body

# ADR: `[decision topic]`

| Field | Value |
|---|---|
| Status | proposed / accepted / deprecated / superseded |
| Decision Date | `[YYYY-MM-DD]` |
| Scope | `[product / architecture / data / operations / UX / other]` |
| Owner | `[person or team]` |
| Related Documents | `[links]` |
| Supersedes | `[none or path]` |

## Context

- `[problem or constraint that requires a decision]`
- `[current reference documents, code state, or operating conditions]`

## Decision

`[state the final decision clearly and briefly]`

## Rationale

- `[why this decision was chosen]`
- `[important trade-off]`

## Alternatives Considered

| Alternative | Pros | Cons | Why Not Chosen |
|---|---|---|---|
| `[alternative]` | `[pros]` | `[cons]` | `[reason]` |

## Impact

- Code impact: `[affected area]`
- Document impact: `[documents to update]`
- Operational impact: `[deployment, rollback, monitoring, data migration, etc.]`
- Risks: `[remaining risks or items to confirm]`

## Verification Or Operating Rule

- `[how to confirm that the decision is followed]`
- `[related tests, review criteria, or pre-deploy checks]`

## Change History

| Date | Change | Reason |
|---|---|---|
| `[YYYY-MM-DD]` | Initial version | `[reason]` |

## Application Notes

- Do not leave placeholders when applying this to a real project.
- Do not copy the `ADR Template`, `docs/adr/INDEX.md Example`, or `ADR Body Copy Range` sections into a real ADR file.
- If a value is undecided, move it to `Items To Confirm` instead of guessing in the body.
- If status is `superseded`, include the replacement ADR path.
