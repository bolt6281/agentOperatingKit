# Work Log Template

Use this template for long-running implementation history and operational notes that are hard to track through issues, PRs, plans, or release notes alone.

`docs/work-log.md` is not a current reference document. Put the current operating baseline in `docs/current-status.md`, release baselines in `docs/VERSION_HISTORY.md`, and decision rationale in ADRs.
Do not read it at the start of ordinary work. Use it as a write-only history by default, and read it only for rollback, recovery, incident investigation, regression tracing, or old implementation rationale.

# Work Log

> Historical implementation and operations log.

## Writing Rules

- Keep the newest entries at the top.
- Each entry should end with date, short title, change summary, and validation.
- Keep only implementation reasons or operational judgments that may matter later.
- During ordinary work, write to this document when useful but do not use it as a default reference.
- Do not accumulate routine progress notes, chat summaries, or temporary research.
- Do not include secrets, personal data, full log dumps, or large command output.

## Read When

- Rolling back or recovering a previous change
- Investigating incidents, regressions, or data inconsistencies against past work
- Checking old implementation rationale or operational judgment
- Tracing history when reference documents conflict

### `[YYYY-MM-DD] [short title]`

- `[what changed]`
- `[why it changed or which reference/request it connects to]`
- `[main affected areas or artifacts]`
- Validation:
  - `[verification command or check]`

## Application Notes

- Do not leave placeholders when applying this to a real project.
- If the same change affects a release baseline, update `docs/VERSION_HISTORY.md` too.
- If a product, architecture, data, or operations policy decision changes, update ADRs instead of the work log.
