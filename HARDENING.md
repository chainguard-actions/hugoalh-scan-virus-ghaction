<!-- markdownlint-disable -->

# Hardening Report: hugoalh--scan-virus-ghaction/v0.15.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **hugoalh--scan-virus-ghaction/v0.15.1** was hardened automatically. 24 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Rule (a) violation: The `run:` block in the 'Resolve Repositories' step directly interpolates the user-controlled expression `${{github.event.inputs.repositories}}` into a PowerShell script string. An attacker can inject arbitrary PowerShell code via the `repositories` workflow_dispatch input.

Locations:

- `.github/workflows/scan-virus-github-repository.yml:22`

### script-injection (severity: high)

Rule (a) violation: The `run:` block in the 'Resolve Packages' step directly interpolates the user-controlled expression `${{github.event.inputs.packages}}` into a PowerShell script string. An attacker can inject arbitrary PowerShell code via the `packages` workflow_dispatch input.

Locations:

- `.github/workflows/scan-virus-npm.yml:18`

### script-injection (severity: high)

Rule (a) violation: The `run:` block in the 'Push Git Commit' step directly interpolates `${{steps.updater.outputs.timestamp}}` (a steps output context value) into a shell command: `git --no-pager commit --message="Update assets on ${{steps.updater.outputs.timestamp}}"`

Locations:

- `.github/workflows/update-assets.yml:30`

### unpinned-uses (severity: high)

Multiple workflow files reference actions and reusable workflows using mutable tags or branch names instead of full 40-character commit SHAs. Failing references include: actions/checkout@v3.5.3, docker/login-action@v2.2.0, docker/metadata-action@v4.5.0, docker/build-push-action@v4.1.0

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:22`

### unpinned-uses (severity: high)

Multiple workflow files reference actions and reusable workflows using mutable tags or branch names instead of full 40-character commit SHAs. Failing references include: hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3, actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction/clamav@v0.15.0

Locations:

- `.github/workflows/scan-virus-github-repository.yml:17`

### unpinned-uses (severity: high)

Workflow references actions using mutable tags: hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3, hugoalh/scan-virus-ghaction/clamav@v0.15.0

Locations:

- `.github/workflows/scan-virus-npm.yml:14`

### unpinned-uses (severity: high)

Workflow references action using mutable tag: hugoalh/scan-virus-ghaction/clamav@v0.15.0

Locations:

- `.github/workflows/scan-virus-remote.yml:14`

### unpinned-uses (severity: high)

Workflow references reusable workflow using mutable branch ref @main: hugoalh/hugoalh/.github/workflows/scan-virus.yml@main

Locations:

- `.github/workflows/scan-virus.yml:35`

### unpinned-uses (severity: high)

Workflow references actions and reusable workflows using mutable tags/branches: actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction/_build/all@main, hugoalh/scan-virus-ghaction/_build/clamav@main, hugoalh/scan-virus-ghaction/_build/yara@main

Locations:

- `.github/workflows/test-build.yml:42`

### unpinned-uses (severity: high)

Workflow references actions using mutable tags/branches: actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction@main, hugoalh/scan-virus-ghaction/clamav@main, hugoalh/scan-virus-ghaction/yara@main

Locations:

- `.github/workflows/test-package.yml:42`

### unpinned-uses (severity: high)

Workflow references actions using mutable tags: actions/checkout@v3.5.3, hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3

Locations:

- `.github/workflows/update-assets.yml:16`

### unpinned-uses (severity: high)

Workflow references reusable workflow using mutable branch ref @main: hugoalh/hugoalh/.github/workflows/announce-new-release-discord.yml@main

Locations:

- `.github/workflows/announce-new-release-discord.yml:7`

### unpinned-uses (severity: high)

The action's `runs.image:` field references a Docker image by mutable tag instead of a SHA digest: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1`

Locations:

- `action.yml:68`

### unpinned-uses (severity: high)

The action's `runs.image:` field references a Docker image by mutable tag instead of a SHA digest: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-clamav`

Locations:

- `clamav/action.yml:60`

### unpinned-uses (severity: high)

The action's `runs.image:` field references a Docker image by mutable tag instead of a SHA digest: `docker://ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-yara`

Locations:

- `yara/action.yml:57`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job. This means the GITHUB_TOKEN is granted default (potentially write) permissions for all jobs.

Locations:

- `.github/workflows/publish-docker-container-ghp.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/scan-virus-github-repository.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/scan-virus-npm.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/scan-virus-remote.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/scan-virus.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/test-build.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/test-package.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/update-assets.yml:1`

### missing-permissions (severity: medium)

Workflow file has no top-level `permissions:` key and no job-level `permissions:` keys on any job.

Locations:

- `.github/workflows/announce-new-release-discord.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection, unpinned-uses, missing-permissions

**Notes:**

Fixed all 24 findings across 12 files:

**script-injection (3 fixes):**
- scan-virus-github-repository.yml: Moved `${{github.event.inputs.repositories}}` to env block as INPUT_REPOSITORIES, referenced via $Env:INPUT_REPOSITORIES in PowerShell
- scan-virus-npm.yml: Moved `${{github.event.inputs.packages}}` to env block as INPUT_PACKAGES, referenced via $Env:INPUT_PACKAGES in PowerShell
- update-assets.yml: Moved `${{steps.updater.outputs.timestamp}}` to env block as COMMIT_TIMESTAMP, referenced via ${COMMIT_TIMESTAMP} in shell

**unpinned-uses (13 fixes):**
- action.yml: Pinned ghcr.io/hugoalh/scan-virus-ghaction:0.15.1 to @sha256:4a9dde2e90acfe6e9a5f958e5ce41a76281bd7ac8cff5089d2d13c3d23a841d6
- clamav/action.yml: Pinned ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-clamav to @sha256:565e3e20e186ac487e1ab1ab8906a1856d98885eb5460c0ecedee2dfd646a20b
- yara/action.yml: Pinned ghcr.io/hugoalh/scan-virus-ghaction:0.15.1-yara to @sha256:85e97fde7f253bcc378acc30d292f457b9bc85e5413d92a662b23562d4757f06
- publish-docker-container-ghp.yml: Pinned actions/checkout@v3.5.3, docker/login-action@v2.2.0, docker/metadata-action@v4.5.0, docker/build-push-action@v4.1.0
- scan-virus-github-repository.yml: Pinned hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3, actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction/clamav@v0.15.0
- scan-virus-npm.yml: Pinned hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3, hugoalh/scan-virus-ghaction/clamav@v0.15.0
- scan-virus-remote.yml: Pinned hugoalh/scan-virus-ghaction/clamav@v0.15.0
- scan-virus.yml: Pinned hugoalh/hugoalh reusable workflow @main
- test-build.yml: Pinned actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction/_build/{all,clamav,yara}@main
- test-package.yml: Pinned actions/checkout@v3.5.3, hugoalh/scan-virus-ghaction{,/clamav,/yara}@main
- update-assets.yml: Pinned actions/checkout@v3.5.3, hugoalh-studio/setup-powershell-toolkit-ghaction@v1.2.3
- announce-new-release-discord.yml: Pinned hugoalh/hugoalh reusable workflow @main

**missing-permissions (9 fixes):**
- Added `permissions: {}` at top level to all 9 workflow files
- publish-docker-container-ghp.yml: Added job-level `contents: read, packages: write` for GHCR push
- update-assets.yml: Added job-level `contents: write` for git push

