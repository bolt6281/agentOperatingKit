# Review Feedback Handling Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Do not mechanically apply review feedback. Check validity and conflicts first, then apply changes in small units.

## Procedure

1. When review feedback arrives, use `receiving-code-review` before changing code.
2. Check whether the feedback conflicts with requirements, existing design, or test results.
3. Apply valid feedback in small units.
4. If behavior changes, use `test-driven-development` or strengthen existing tests.
5. After applying feedback, use `verification-before-completion` and rerun relevant checks.

## Before Completion

- Was feedback validity checked first?
- If any feedback was not applied, is the reason clear?
- If behavior changed, were tests or alternative verification strengthened?
- Were relevant checks rerun?
