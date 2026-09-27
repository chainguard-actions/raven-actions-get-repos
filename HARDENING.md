<!-- markdownlint-disable -->

# Hardening Report: raven-actions--get-repos/v1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **raven-actions--get-repos/v1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action step uses `actions/github-script@v6`, which is pinned to a mutable version tag rather than an immutable 40-character commit SHA. If the tag is moved (intentionally or via a supply-chain compromise), the action will silently execute different code. Replace with a full SHA pin, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v6`.

Locations:

- `action.yml:33`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced `actions/github-script@v6` with `actions/github-script@d7906e4ad0b1822421a7e6a35d5ca353c962f410 # v6` in hardened/action/action.yml line 33. The SHA was resolved via lookup_action_sha for the v6 tag.

