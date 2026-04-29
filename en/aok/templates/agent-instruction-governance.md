# Agent Instruction Governance Section

Use this optional section only when agent instruction files are managed policy files and changes need approval rules. Do not add it to small projects that only need a short root `AGENTS.md`.

## Managed Instruction Files

- `AGENTS.md`
- `**/AGENTS.md`
- `.agents/**`

## Changes Allowed Without Approval

These changes are allowed only when they preserve meaning:

- Typo fixes
- Broken internal link fixes
- Path corrections after actual file moves
- Clearly outdated date or filename corrections
- Table formatting and Markdown formatting cleanup
- Filling missing metadata for already-approved files in `.agents/INDEX.md`
- Marking deleted files as `deprecated` or `archived` in `.agents/INDEX.md`

If meaning may change, treat it as approval-required.

## Changes Requiring User Approval

- Creating a new root or nested `AGENTS.md`
- Creating a new `.agents/workflows/*.md`
- Changing required or forbidden agent behavior
- Adding, removing, or changing verification commands
- Changing scope, owner, or responsibility boundaries
- Adding, removing, or reordering workflow steps
- Changing document creation, approval, risky-work, or archive policy

## Explicit User Requests

If the user explicitly asks to modify an instruction, add a workflow, or make a structure, make changes only within that requested scope.

Do not create additional instructions or workflows beyond the requested scope without proposing them first.

## Ambiguous Cases

If it is unclear whether a change is cleanup or policy change, treat it as a policy change and propose it first.

After approval, create or meaningfully change the file and update `.agents/INDEX.md` in the same task when applicable.
