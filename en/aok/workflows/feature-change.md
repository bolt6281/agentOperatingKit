# Feature / Behavior Change Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

When adding a feature or changing behavior, classify task size first and follow the procedure that matches the risk.

## Procedure

1. Classify task size first.
   - Short path: single file or narrow scope, clear requirements, no public API/DB/deployment/build/auth/security impact, low regression risk.
   - Standard path: multiple files, new behavior design, user flow change, state/data/API change, or a needed test strategy.
   - High-risk path: DB, auth/authz, payments, deployment, migrations, build/CI, or possible data loss.
2. If the task is high-risk, do not continue this workflow. Read `.agents/workflows/risky-change.md` first and switch to that workflow.
   - Include the feature requirements inside the impact scope, rollback, and verification plan in `risky-change.md`.
   - Even when high-risk work is also feature work, `risky-change.md` has higher workflow priority.
3. For the short path, apply the principles of `brainstorming` in abbreviated form: confirm goal, change scope, and verification method, then execute inline.
   - `writing-plans` documentation and `executing-plans` can be skipped.
   - If behavior changes, add the smallest practical test or reproduction check.
   - Before completion, use `verification-before-completion` to confirm actual verification results.
4. For the standard path, use `brainstorming` to clarify purpose, user, success criteria, scope, and non-scope.
5. If needed, use `clarify` to narrow ambiguous requirements through concrete choices.
6. After user approval, use `writing-plans` to write an implementation plan.
7. When the plan is ready, use `executing-plans` to execute step by step.
8. For verifiable behavior changes, use `test-driven-development` to create a failing test first.
9. Use `dispatching-parallel-agents` or `subagent-driven-development` only when independent work can be split cleanly and the user has allowed it.
10. For medium or larger changes, shared-boundary changes, or regression risk, use `requesting-code-review` at key checkpoints.
11. If review feedback arrives, use `receiving-code-review` before applying it.
12. Use `verification-before-completion` to confirm tests, build, manual checks, or other actual results.
13. If work is on a branch, finish with `finishing-a-development-branch`.

## Before Completion

- Was the task size classified correctly?
- If the task was high-risk, was it switched to `risky-change.md`?
- Were the required Superpowers skills applied?
- Is there a test or reproduction check for the behavior change?
- Were actual verification results checked before claiming completion?
