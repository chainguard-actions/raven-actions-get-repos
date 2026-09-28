<!-- markdownlint-disable -->

# Hardening Report: raven-actions--get-repos/v1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **raven-actions--get-repos/v1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action step uses `actions/github-script@v6`, which is pinned to a mutable version tag (`@v6`) rather than an immutable full-length 40-character commit SHA. This means the referenced action could be silently replaced with a different (potentially malicious) version without any change to this file, exposing the action to supply-chain attacks.

Locations:

- `action.yml:38`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v6` to its full commit SHA `d7906e4ad0b1822421a7e6a35d5ca353c962f410` in hardened/action/action.yml (line 38). The mutable tag is preserved as a comment (`# v6`) for readability.

