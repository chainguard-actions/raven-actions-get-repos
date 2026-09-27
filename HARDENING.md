<!-- markdownlint-disable -->

# Hardening Report: raven-actions--get-repos/v1.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **raven-actions--get-repos/v1.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action step uses `actions/github-script@v6`, which is pinned to a mutable version tag (`v6`) rather than an immutable 40-character commit SHA. This means the action could be silently updated or compromised without the consuming workflow noticing, enabling a supply-chain attack. It should be pinned to a full SHA, e.g. `actions/github-script@60a0d83039c74a4aee543508d2ffcb1c3799cdea # v6`.

Locations:

- `action.yml:44`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/github-script@v6` to its full commit SHA `d7906e4ad0b1822421a7e6a35d5ca353c962f410` in hardened/action/action.yml (line 44). The mutable `v6` tag is preserved as a comment for readability.

