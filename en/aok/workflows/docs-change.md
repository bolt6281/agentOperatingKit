# Documentation / Policy / ADR Change Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Prevent document sprawl and maintain consistency between existing documents and policies.

## Procedure

1. Before creating a new document, check whether an existing document can solve the need.
2. If updating an existing document or adding a section is enough, update that document first.
3. When reflecting existing project documents into AOK structure, follow the user's selected mode: preserve originals, archive originals, merge first, or report conflicts first.
4. If existing documents conflict, do not silently choose one as the source of truth. Propose a conflict list and recommended basis first.
5. If a new document is needed, propose its name, path, purpose, and why existing documents are insufficient. Create it only after user approval.
6. If a core product decision changes, update `docs/adr.md` or the relevant domain ADR pointed to by `docs/adr/INDEX.md` first.
7. If the documentation change leads to implementation work, use `brainstorming` or `writing-plans`.
8. Before completion, check related documents for conflicts and information loss, then use `verification-before-completion`.

## Documentation Principles

- Prefer updating existing documents over creating new documents.
- Needing to inspect or modify documentation does not imply permission to create a new document.
- If a new Markdown document seems necessary, propose the name, path, purpose, and why existing documents are insufficient before creating it.
- If a core product decision changes, update `docs/adr.md` or the relevant `docs/adr/<domain>/<decision-topic>.md` first.
- Project-specific agent documents are also Markdown documents, so new ones require prior approval.
- When merging existing documents into AOK format, check that original details, exceptions, and conditions were not lost.
- Do not move, delete, deprecate, or archive existing documents without user approval.
- If an existing workflow conflicts with AOK workflow, follow the user's selected conflict-handling mode.

## Before Completion

- Was updating an existing document considered first?
- If a new document was needed, was user approval received?
- Were related document conflicts checked?
- Was possible information loss checked?
- Were move, delete, deprecate, and archive actions approved?
