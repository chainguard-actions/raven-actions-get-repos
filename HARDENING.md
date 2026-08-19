<!-- markdownlint-disable -->

# Hardening Report: raven-actions--get-repos/v1.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **raven-actions--get-repos/v1.0.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references are pinned to mutable tags or branch names instead of immutable full 40-character commit SHAs, making the action vulnerable to supply-chain attacks if the referenced tag or branch is moved.

In action.yml:
- `actions/github-script@v6` (tag)

In .github/workflows/ci.yml:
- `raven-actions/debug@v1` (tag)
- `actions/checkout@v3` (tag, used twice)

In .github/workflows/linter.yml:
- `raven-actions/.workflows/.github/workflows/__linter.yml@main` (branch)

In .github/workflows/release-draft.yml:
- `raven-actions/.workflows/.github/workflows/__release-draft.yml@main` (branch)

In .github/workflows/release-publish.yml:
- `raven-actions/.workflows/.github/workflows/__release-publish.yml@main` (branch)

Locations:

- `action.yml:52`
- `.github/workflows/ci.yml:36`
- `.github/workflows/ci.yml:42`
- `.github/workflows/ci.yml:80`
- `.github/workflows/linter.yml:17`
- `.github/workflows/release-draft.yml:11`
- `.github/workflows/release-publish.yml:14`

### missing-permissions (severity: medium)

None of the workflow files define a top-level `permissions:` key, and no individual job defines its own `permissions:` block. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/ci.yml:1`
- `.github/workflows/linter.yml:1`
- `.github/workflows/release-draft.yml:1`
- `.github/workflows/release-publish.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all mutable tag/branch references to full 40-character commit SHAs: actions/github-script@v6→d7906e4a, raven-actions/debug@v1→9dbdeb7e, actions/checkout@v3→a37ce912 (×2 in ci.yml), and raven-actions/.workflows@main→6da075fe (×3 for linter, release-draft, release-publish workflows). Added top-level `permissions: contents: read` block to all four workflow files (ci.yml, linter.yml, release-draft.yml, release-publish.yml) to enforce least-privilege access.

