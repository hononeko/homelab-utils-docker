# Homelab Utils Docker

This repository generates lean, purpose-built Docker utility images for homelab workloads.

## Images

| Image | Description | Core Binaries |
| --- | --- | --- |
| `k8s-backup-tools` | Data synchronization and event monitoring for sidecar tasks | `rsync`, `inotify-tools`, `findutils`, `sqlite` |
| `k8s-config-tools` | Dynamic config templating and generation | `gomplate`, `yq`, `jq`, `curl` |

## CI/CD Workflow

This repository uses GitHub Actions configured for monorepo semantics.

1. **Pull Requests (CI)**: Any changes pushed to an image directory will trigger `ci.yml` which validates the `Dockerfile` by building it locally using `docker buildx build`.
2. **Deployments (CD)**: Deployments are completely manual. Go to the **Actions** tab and trigger the deployment workflow (e.g., `Deploy k8s-backup-tools`). 

## Versioning & Commits

This repository relies on **Conventional Commits** to calculate versions per directory automatically via `PaulHatch/semantic-version`.

When making commits, ensure they follow this pattern:
- `feat(tool): add new package` -> Minor bump (1.0.0 -> 1.1.0)
- `fix(tool): fix bug` -> Patch bump (1.0.0 -> 1.0.1)
- `feat!(tool): update alpine base` -> Major/Breaking bump (1.0.0 -> 2.0.0)

> **Note:** The `!` operator in the prefix dictates a BREAKING CHANGE and will bump the major version.
