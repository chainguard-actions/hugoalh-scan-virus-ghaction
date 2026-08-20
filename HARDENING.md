<!-- markdownlint-disable -->

# Hardening Report: hugoalh--scan-virus-ghaction/v0.20.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **hugoalh--scan-virus-ghaction/v0.20.1** was hardened automatically. 16 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references the Docker image 'docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1' by a mutable version tag instead of an immutable SHA digest. This allows supply-chain attacks if the tag is moved to a different image.

Locations:

- `action.yml:74`

### unpinned-uses (severity: high)

clamav/action.yml references the Docker image 'docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-clamav' by a mutable version tag instead of an immutable SHA digest.

Locations:

- `clamav/action.yml:60`

### unpinned-uses (severity: high)

yara/action.yml references the Docker image 'docker://ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-yara' by a mutable version tag instead of an immutable SHA digest.

Locations:

- `yara/action.yml:55`

### unpinned-uses (severity: high)

Multiple uses: references in this workflow use mutable version tags or branch names instead of full 40-character SHA commit hashes: 'actions/checkout@v4.1.1', 'docker/login-action@v3.0.0', 'docker/metadata-action@v5.0.0' (×3), 'docker/build-push-action@v5.0.0' (×3). Any of these can be silently redirected to a different commit.

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:28`
- `.github/workflows/publish-docker-container-ghp.yml:31`
- `.github/workflows/publish-docker-container-ghp.yml:36`
- `.github/workflows/publish-docker-container-ghp.yml:55`
- `.github/workflows/publish-docker-container-ghp.yml:74`
- `.github/workflows/publish-docker-container-ghp.yml:93`
- `.github/workflows/publish-docker-container-ghp.yml:107`
- `.github/workflows/publish-docker-container-ghp.yml:118`

### unpinned-uses (severity: high)

Uses reference 'hugoalh/hugoalh/.github/workflows/reusable-announce-new-release-discord.yml@main' uses the mutable branch name 'main' instead of a full 40-character SHA commit hash.

Locations:

- `.github/workflows/announce-new-release-discord.yml:10`

### unpinned-uses (severity: high)

Uses reference 'hugoalh/hugoalh/.github/workflows/reusable-scan-virus-1.yml@main' uses the mutable branch name 'main' instead of a full 40-character SHA commit hash.

Locations:

- `.github/workflows/scan-virus.yml:38`

### unpinned-uses (severity: high)

Uses reference 'hugoalh/hugoalh/.github/workflows/reusable-sync-labels.yml@main' uses the mutable branch name 'main' instead of a full 40-character SHA commit hash.

Locations:

- `.github/workflows/sync-labels.yml:13`

### unpinned-uses (severity: high)

Multiple uses: references in this workflow use mutable version tags or branch names: 'actions/checkout@v4.1.1' (×3), 'hugoalh/scan-virus-ghaction/_build/all@main', 'hugoalh/scan-virus-ghaction/_build/clamav@main', 'hugoalh/scan-virus-ghaction/_build/yara@main'.

Locations:

- `.github/workflows/test-build.yml:42`
- `.github/workflows/test-build.yml:46`
- `.github/workflows/test-build.yml:60`
- `.github/workflows/test-build.yml:64`
- `.github/workflows/test-build.yml:78`
- `.github/workflows/test-build.yml:82`

### unpinned-uses (severity: high)

Uses references 'hugoalh/scan-virus-ghaction/_build/clamav@main' uses the mutable branch name 'main' instead of a full 40-character SHA commit hash.

Locations:

- `.github/workflows/test-debug.yml:17`

### unpinned-uses (severity: high)

Multiple uses: references in this workflow use mutable version tags or branch names: 'actions/checkout@v4.1.1' (×3), 'hugoalh/scan-virus-ghaction@main', 'hugoalh/scan-virus-ghaction/clamav@main', 'hugoalh/scan-virus-ghaction/yara@main'.

Locations:

- `.github/workflows/test-package.yml:42`
- `.github/workflows/test-package.yml:46`
- `.github/workflows/test-package.yml:60`
- `.github/workflows/test-package.yml:64`
- `.github/workflows/test-package.yml:78`
- `.github/workflows/test-package.yml:82`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default (potentially write) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/announce-new-release-discord.yml:1`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. The job pushes Docker images to GHCR using github.token but does not explicitly scope the token permissions.

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:1`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default permissions.

Locations:

- `.github/workflows/scan-virus.yml:1`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default permissions.

Locations:

- `.github/workflows/test-build.yml:1`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default permissions.

Locations:

- `.github/workflows/test-debug.yml:1`

### missing-permissions (severity: medium)

Workflow has no top-level 'permissions:' key and no job-level 'permissions:' key on any job. Without explicit permissions, the GITHUB_TOKEN is granted default permissions.

Locations:

- `.github/workflows/test-package.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 16 findings across 9 files:

**Docker image pinning (action.yml files):**
- action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1 → pinned with sha256:d169739a0b559a1978da107e7d5e9fb8d73ce804bcb92edbca1694ea323fbae8
- clamav/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-clamav → pinned with sha256:806278ed1a2829743c4b9d92f29bdd49e384ab3cdc6bf19caea19b1390d4c085
- yara/action.yml: ghcr.io/hugoalh/scan-virus-ghaction:0.20.1-yara → pinned with sha256:a8a55550d7acc35fec6cb9c51219efed57292d8f18662fd8930bf77f81ecc8c9

**GitHub Actions pinning (workflow files):**
- actions/checkout@v4.1.1 → @b4ffde65f46336ab88eb53be808477a3936bae11
- docker/login-action@v3.0.0 → @343f7c4344506bcbf9b4de18042ae17996df046d
- docker/metadata-action@v5.0.0 → @96383f45573cb7f253c731d3b3ab81c87ef81934
- docker/build-push-action@v5.0.0 → @0565240e2d4ab88bba5387d719585280857ece09
- hugoalh/hugoalh reusable workflows @main → @bd6d88d955061b37108519fb4e595ed71403c0e3
- hugoalh/scan-virus-ghaction @main → @6fd3ce3d07abc68dd032bd99eebb8cce12986a9d

**Missing permissions added:**
- announce-new-release-discord.yml: permissions: {}
- publish-docker-container-ghp.yml: contents: read, packages: write
- scan-virus.yml: permissions: {}
- test-build.yml: permissions: {}
- test-debug.yml: permissions: {}
- test-package.yml: permissions: {}
- sync-labels.yml: already had permissions, only needed SHA pinning

