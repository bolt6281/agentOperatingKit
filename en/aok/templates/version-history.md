# Version History Template

Use this template to track major versions, release baselines, deployment artifacts, and user-facing release changes in one place.

`docs/VERSION_HISTORY.md` is not a general work log. Put detailed implementation history in `docs/work-log.md` and decision rationale in ADRs.

If the project already has a `CHANGELOG`, release notes, GitHub Releases, or a release-criteria section in `CONTRIBUTING`, do not create a new `docs/VERSION_HISTORY.md` by default. Strengthen the existing document first, and use this template only when the existing documents cannot reliably track release baselines and deployment artifacts.

# Version History

Current staged build: `[version or not applicable]`

Current release baseline: `[version or not applicable]`

This document tracks release-to-release changes and related deployment artifacts.
Update this file together with version/build files only when a version, release baseline, or deployment artifact changes.

## Operating Rules

- Only bump versions when the user or release process explicitly asks for it.
- Do not advance the version just because a feature change landed.
- If this file would duplicate an existing CHANGELOG or release note, keep the existing document as the source of truth instead.
- Keep user-facing version, platform build number, and deployment artifact names aligned.
- Record artifact type and path when a release package is built.

## Comparison Summary

| Version | Baseline Status | Change Summary |
|---|---|---|
| `[version]` | current staged build / current release baseline / previous release baseline | `[one-line summary]` |

## `[version]`

previous version: `[previous version or none]`

### changes

- `[release-to-release change]`
- `[build, deployment, data, or compatibility change]`

### release notes

- user-facing version: `[version]`
- platform build number: `[versionCode, build number, or not applicable]`
- release artifact: `[artifact path or deployment URL]`
- `[user-facing release note]`

## Application Notes

- Keep newest versions near the top.
- If a CHANGELOG, release notes, or GitHub Releases already exist, check whether strengthening that document is enough before creating a new file.
- If the project has no staged-build concept, use only `Current release baseline`.
- If the project has no mobile/build artifact, remove platform build number rows instead of inventing values.
- Do not leave placeholders when applying this to a real project.
