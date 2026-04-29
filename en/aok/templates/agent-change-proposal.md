# Agent Instruction Change Proposal Template

This template is not meant to be saved as a file in most projects. It is a reusable approval form that agents copy into chat when asking the user to approve instruction changes.

After AOK is applied, projects usually reference this form from `.agents/INDEX.md` or the root `AGENTS.md`. Creating a separate project file for it is usually unnecessary.

```md
## Agent Instruction Change Proposal

- Change type: new nested `AGENTS.md` / existing instruction meaning change / workflow meaning change
- Target path:
- Scope:
- Reason:
- Proposed rules:
  - ...
- Conflict with existing rules:
- Verification method:
- User approval required: yes
```

Example:

```md
## Agent Instruction Change Proposal

- Change type: new nested `AGENTS.md`
- Target path: `apps/web/AGENTS.md`
- Scope: `apps/web/**`
- Reason: frontend verification commands and component rules are more specific than root rules.
- Proposed rules:
  - Run `pnpm --filter web test` after UI changes.
  - Check `packages/ui` before creating a new component.
- Conflict with existing rules: none
- Verification method: `pnpm --filter web lint`, `pnpm --filter web test`
- User approval required: yes
```
