# Hardening Report: hugoalh--scan-virus-ghaction/v0.20.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **hugoalh--scan-virus-ghaction/v0.20.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three action.yml files reference Docker images using mutable version tags instead of immutable SHA256 digests. This means the image content could change without notice, enabling supply-chain attacks. Affected references:
- action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0` (tag, not a digest)
- clamav/action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-clamav` (tag, not a digest)
- yara/action.yml: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-yara` (tag, not a digest)

Each should be replaced with a SHA256 digest reference, e.g. `docker://ghcr.io/hugoalh/scan-virus-ghaction@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`
- `clamav/action.yml:61`
- `yara/action.yml:54`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced all three mutable Docker image tag references with immutable SHA256 digests:
- action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0 → @sha256:7b2bd918832c4a1696985de9017bd1a2ef15bce46a5450b989dc20ecf94f3150 # 0.20.0
- clamav/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-clamav → @sha256:f7666691204cd3c8e169d320b539773aee1ea6e63712ad29d1a13023cd55dd4f # 0.20.0-clamav
- yara/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-yara → @sha256:1a7a2ad2b6cc58a76e0740d679e3ca82cdb82f42a6f9c7b94bc7184e06e15fbb # 0.20.0-yara
Original tags are preserved as inline comments for readability. Digests were resolved using the Docker Registry HTTP API v2.

