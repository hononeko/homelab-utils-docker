# Homelab Utils Docker

This repository generates lean, purpose-built Docker utility images for homelab workloads.

## Images

| Image | Description | Core Binaries |
| --- | --- | --- |
| `k8s-backup-tools` | Data synchronization and event monitoring for sidecar tasks | `rsync`, `inotify-tools`, `findutils`, `sqlite` |
| `k8s-config-tools` | Dynamic config templating and generation | `gomplate`, `yq`, `jq`, `curl` |

## CI/CD Workflow

This repository uses GitHub Actions configured for monorepo semantics, with the shared actions from [hononeko/actions](https://github.com/hononeko/actions).

1. **Pull Requests (CI)**: `ci.yml` lints the workflows (actionlint, zizmor) and Dockerfiles (hadolint), and builds every image on amd64 and arm64, checking each one starts. Nothing is pushed.
2. **Releases (CD)**: manual. In the **Actions** tab, run **Release** and pick the image. It computes that image's next version, builds both architectures and publishes them as one multi-arch image tagged with the version and `latest` (with build provenance), then creates the `<image>-X.Y.Z` GitHub Release with that image's notes. With nothing to release, it stops after the version.

## Versioning & Commits

Each image is versioned on its own from the **Conventional Commits** that change its directory (`images/<image>`) since its last `<image>-X.Y.Z` tag, using the `version` action's rules:
- `feat(tool): add new package` -> Minor bump (1.0.0 -> 1.1.0)
- `fix(tool): fix bug`, or any other type -> Patch bump (1.0.0 -> 1.0.1)
- `docs:` and `test:` -> no release
- `feat(tool)!: update alpine base`, or a `BREAKING CHANGE:` footer -> Major bump (1.0.0 -> 2.0.0)
