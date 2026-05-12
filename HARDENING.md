# Hardening Report: hugoalh--scan-virus-ghaction/v0.15.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **hugoalh--scan-virus-ghaction/v0.15.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three action files reference Docker images by mutable version tags instead of immutable SHA digests. This means the image content could change without notice, enabling supply-chain attacks. Failing references: action.yml uses `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1` (tag, not a SHA digest); clamav/action.yml uses `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-clamav` (tag, not a SHA digest); yara/action.yml uses `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-yara` (tag, not a SHA digest). These should be replaced with digest-pinned references, e.g. `docker://ghcr.io/hugoalh/scan-virus-ghaction@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`
- `clamav/action.yml:60`
- `yara/action.yml:57`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three Docker image references to immutable SHA digests:
- action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.15.1 → @sha256:4a9dde2e90acfe6e9a5f958e5ce41a76281bd7ac8cff5089d2d13c3d23a841d6 # 0.15.1
- clamav/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-clamav → @sha256:565e3e20e186ac487e1ab1ab8906a1856d98885eb5460c0ecedee2dfd646a20b # 0.15.1-clamav
- yara/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-yara → @sha256:85e97fde7f253bcc378acc30d292f457b9bc85e5413d92a662b23562d4757f06 # 0.15.1-yara
Original tags are preserved as comments outside the YAML string quotes for readability.

