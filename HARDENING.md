<!-- markdownlint-disable -->

# Hardening Report: hugoalh--scan-virus-ghaction/v0.20.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **hugoalh--scan-virus-ghaction/v0.20.0** was hardened automatically. 16 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml uses a mutable Docker image tag ('docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0') instead of a SHA digest. This allows the image to be silently replaced with a different version, enabling supply-chain attacks.

Locations:

- `action.yml:72`

### unpinned-uses (severity: high)

clamav/action.yml uses a mutable Docker image tag ('docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-clamav') instead of a SHA digest.

Locations:

- `clamav/action.yml:58`

### unpinned-uses (severity: high)

yara/action.yml uses a mutable Docker image tag ('docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-yara') instead of a SHA digest.

Locations:

- `yara/action.yml:51`

### unpinned-uses (severity: high)

announce-new-release-discord.yml references 'hugoalh/hugoalh/.github/workflows/reusable-announce-new-release-discord.yml@main' — a mutable branch ref instead of a full 40-character commit SHA.

Locations:

- `.github/workflows/announce-new-release-discord.yml:12`

### unpinned-uses (severity: high)

publish-docker-container-ghp.yml references multiple actions with mutable version tags instead of full 40-character commit SHAs: 'actions/checkout@v4.1.1', 'docker/login-action@v3.0.0', 'docker/metadata-action@v5.0.0' (×3), 'docker/build-push-action@v5.0.0' (×3).

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:27`
- `.github/workflows/publish-docker-container-ghp.yml:30`
- `.github/workflows/publish-docker-container-ghp.yml:36`
- `.github/workflows/publish-docker-container-ghp.yml:57`
- `.github/workflows/publish-docker-container-ghp.yml:78`
- `.github/workflows/publish-docker-container-ghp.yml:99`
- `.github/workflows/publish-docker-container-ghp.yml:107`
- `.github/workflows/publish-docker-container-ghp.yml:115`

### unpinned-uses (severity: high)

scan-virus.yml references 'hugoalh/hugoalh/.github/workflows/reusable-scan-virus.yml@main' — a mutable branch ref instead of a full 40-character commit SHA.

Locations:

- `.github/workflows/scan-virus.yml:33`

### unpinned-uses (severity: high)

sync-labels.yml references 'hugoalh/hugoalh/.github/workflows/reusable-sync-labels.yml@main' — a mutable branch ref instead of a full 40-character commit SHA.

Locations:

- `.github/workflows/sync-labels.yml:12`

### unpinned-uses (severity: high)

test-build.yml references multiple actions/workflows with mutable refs instead of full 40-character commit SHAs: 'actions/checkout@v4.1.1' (×3), 'hugoalh/scan-virus-ghaction/_build/all@main', 'hugoalh/scan-virus-ghaction/_build/clamav@main', 'hugoalh/scan-virus-ghaction/_build/yara@main'.

Locations:

- `.github/workflows/test-build.yml:37`
- `.github/workflows/test-build.yml:40`
- `.github/workflows/test-build.yml:58`
- `.github/workflows/test-build.yml:61`
- `.github/workflows/test-build.yml:79`
- `.github/workflows/test-build.yml:82`

### unpinned-uses (severity: high)

test-debug.yml references 'hugoalh/scan-virus-ghaction/_build/clamav@main' — a mutable branch ref instead of a full 40-character commit SHA.

Locations:

- `.github/workflows/test-debug.yml:18`

### unpinned-uses (severity: high)

test-package.yml references multiple actions/workflows with mutable refs instead of full 40-character commit SHAs: 'actions/checkout@v4.1.1' (×3), 'hugoalh/scan-virus-ghaction@main', 'hugoalh/scan-virus-ghaction/clamav@main', 'hugoalh/scan-virus-ghaction/yara@main'.

Locations:

- `.github/workflows/test-package.yml:37`
- `.github/workflows/test-package.yml:40`
- `.github/workflows/test-package.yml:58`
- `.github/workflows/test-package.yml:61`
- `.github/workflows/test-package.yml:79`
- `.github/workflows/test-package.yml:82`

### missing-permissions (severity: medium)

announce-new-release-discord.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/announce-new-release-discord.yml:1`

### missing-permissions (severity: medium)

publish-docker-container-ghp.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:1`

### missing-permissions (severity: medium)

scan-virus.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/scan-virus.yml:1`

### missing-permissions (severity: medium)

test-build.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/test-build.yml:1`

### missing-permissions (severity: medium)

test-debug.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/test-debug.yml:1`

### missing-permissions (severity: medium)

test-package.yml has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially broad) permissions.

Locations:

- `.github/workflows/test-package.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 16 findings across 10 files:

**Docker image pinning (action.yml files):**
- action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0 → pinned with sha256:7b2bd918832c4a1696985de9017bd1a2ef15bce46a5450b989dc20ecf94f3150
- clamav/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-clamav → pinned with sha256:f7666691204cd3c8e169d320b539773aee1ea6e63712ad29d1a13023cd55dd4f
- yara/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.0-yara → pinned with sha256:1a7a2ad2b6cc58a76e0740d679e3ca82cdb82f42a6f9c7b94bc7184e06e15fbb

**GitHub Actions pinning (workflow files):**
- actions/checkout@v4.1.1 → @b4ffde65f46336ab88eb53be808477a3936bae11
- docker/login-action@v3.0.0 → @343f7c4344506bcbf9b4de18042ae17996df046d
- docker/metadata-action@v5.0.0 → @96383f45573cb7f253c731d3b3ab81c87ef81934
- docker/build-push-action@v5.0.0 → @0565240e2d4ab88bba5387d719585280857ece09
- hugoalh/hugoalh reusable workflows @main → @d4341938b228ddc93b22c91c6fca2413d607046b
- hugoalh/scan-virus-ghaction @main → @6fd3ce3d07abc68dd032bd99eebb8cce12986a9d

**Permissions added:**
- announce-new-release-discord.yml: permissions: {}
- publish-docker-container-ghp.yml: permissions: { contents: read, packages: write }
- scan-virus.yml: permissions: {}
- test-build.yml: permissions: {}
- test-debug.yml: permissions: {}
- test-package.yml: permissions: {}
- sync-labels.yml: already had permissions (issues: write, pull-requests: write)

