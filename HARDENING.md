# Hardening Report: hugoalh--scan-virus-ghaction/v0.20.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **hugoalh--scan-virus-ghaction/v0.20.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml files reference Docker images using mutable version tags instead of immutable SHA digests. This is a supply-chain risk: if the tag is overwritten with a malicious image, all consumers of this action will silently execute the attacker's code. Affected references:
- action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1` (tag, not a SHA digest)
- clamav/action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-clamav` (tag, not a SHA digest)
- yara/action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-yara` (tag, not a SHA digest)

Each should be pinned to a full SHA256 digest, e.g. `docker://ghcr.io/hugoalh/scan-virus-ghaction@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`
- `clamav/action.yml:61`
- `yara/action.yml:49`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three Docker container image references to immutable SHA256 digests:
- action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1 → @sha256:d169739a0b559a1978da107e7d5e9fb8d73ce804bcb92edbca1694ea323fbae8 # 0.20.1
- clamav/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-clamav → @sha256:806278ed1a2829743c4b9d92f29bdd49e384ab3cdc6bf19caea19b1390d4c085 # 0.20.1-clamav
- yara/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-yara → @sha256:a8a55550d7acc35fec6cb9c51219efed57292d8f18662fd8930bf77f81ecc8c9 # 0.20.1-yara
Original tags are preserved as comments for readability.

