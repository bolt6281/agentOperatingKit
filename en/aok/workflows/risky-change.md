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

## High-Risk Approval Card

If the change may affect deployment, migrations, secrets, production data, auth/authz, payments, security, personal data, or sensitive data, present these items to the user and get explicit approval before editing files.

| Item | What To Confirm |
|---|---|
| Change type | Relevant category: config, build, CI, dependency, deployment, DB, auth, authorization, payments, security, or data processing |
| Affected data | Whether production data, personal data, sensitive data, payment data, or audit-relevant data is affected |
| PII/PHI | Whether personal information or regulated health information is involved |
| Migration direction | Whether the change is forward-only, reversible, a data backfill, or destructive |
| Backup/recovery | Backup need, recovery point, and recovery verification method |
| Rollback | Whether code rollback is enough or DB/data rollback is needed |
| Approver/audit ticket | Approver and issue, PR, ticket, or deploy-log location |
| Deployment window | Whether immediate deployment is safe, maintenance window, and user-impact period |
| Dry run | Whether migration dry-run, staging validation, or sample-data validation is possible |
| Monitoring | Metrics, logs, alerts, or error-budget checks after deployment |

## Procedure

1. Read related documents and current config files first.
2. Summarize impact scope, rollback method, and local verification method.
3. If the change may affect deployment, migrations, secrets, production data, auth/authz, payments, security, personal data, or sensitive data, present the high-risk approval card and get explicit approval before changing files.
4. If risk is high or many files will be touched, use `using-git-worktrees`.
5. If behavior changes or migrations are involved, use `test-driven-development` where practical.
6. Apply the change in the smallest practical unit and run config/build/migration verification commands.
7. If operational risk exists or verification scope is broad, use `requesting-code-review` to check missing verification.
8. Use `verification-before-completion` to confirm actual verification results.

## Before Completion

- Were related documents and current config files checked first?
- Were impact scope, rollback method, and local verification method summarized?
- Were deployment, migration, secret, production data, auth/authz, payment, security, personal-data, or sensitive-data changes approved through the high-risk approval card before execution?
- Were actual verification commands run?
