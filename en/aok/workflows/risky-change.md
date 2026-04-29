# Config / Build / CI / Dependency / Deployment / DB Change Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Apply operationally risky changes in small units after checking impact scope and rollback options.

## Applies To

- Config file changes
- Build or CI changes
- Dependency additions, removals, or upgrades
- Deployment config changes
- DB schema, migration, seed, and data processing changes
- Authentication, authorization, payments, and security-related changes

## Procedure

1. Read related documents and current config files first.
2. Summarize impact scope, rollback method, and local verification method.
3. If the change may affect deployment, migrations, secrets, production data, auth/authz, payments, or security, present the plan, impact scope, rollback method, and verification method to the user and get explicit approval before changing files.
4. If risk is high or many files will be touched, use `using-git-worktrees`.
5. If behavior changes or migrations are involved, use `test-driven-development` where practical.
6. Apply the change in the smallest practical unit and run config/build/migration verification commands.
7. If operational risk exists or verification scope is broad, use `requesting-code-review` to check missing verification.
8. Use `verification-before-completion` to confirm actual verification results.

## Before Completion

- Were related documents and current config files checked first?
- Were impact scope, rollback method, and local verification method summarized?
- Were deployment, migration, secret, production data, auth/authz, payment, or security-impacting changes approved before execution?
- Were actual verification commands run?
