# Research / Decision / Technology Choice Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Before implementing, define the decision purpose and evaluation criteria, compare alternatives and risks, and connect the decision to documentation updates when needed.

## Procedure

1. Do not implement first. Define the purpose of the question and the decision criteria.
2. If needed, ask only the minimum questions needed to settle options and evaluation criteria.
3. If the topic is time-sensitive, check official documentation, primary sources, release notes, standards documents, or similarly reliable sources first.
4. If external sources were used, record the source links and the date they were checked in the decision rationale.
5. Summarize alternatives, pros and cons, risks, and recommendation.
6. If the decision affects project operating rules or architecture, update the relevant document, `docs/adr.md`, or the domain ADR pointed to by `docs/adr/INDEX.md`.
7. If implementation is needed after the decision, switch to `feature-change.md` or `risky-change.md`.

## Before Completion

- Is the decision to be made clear?
- Are evaluation criteria and options explicit?
- If the topic is time-sensitive, were official documents or primary sources checked?
- If external sources were used, were source links and the date checked recorded?
- Does the recommendation affect project operating rules or architecture?
- If implementation follows, was the right workflow selected?
