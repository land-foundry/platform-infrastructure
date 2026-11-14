# Platform Infrastructure

Terraform configuration for Land Foundry platform infrastructure, including GitHub repository provisioning and future GCP infrastructure.

| Configuration | Scope | Execution |
|---|---|---|
| [GitHub](github/README.md) | Repository creation and selected repository settings | Independent Terraform root in `github/` |
| GCP | Cloud infrastructure | No configuration exists yet; introduce separate roots when needed |

Each Terraform root owns its provider lock file, credentials, state, and plan/apply execution. Run validation and plans only for the affected root. GitHub changes must not require GCP credentials or a GCP plan. No automated apply workflow is introduced by consolidation.

[GitHub Governance](https://github.com/land-foundry/github-governance) remains the authority for engineering policy; this repository implements infrastructure configuration.

## Architecture Decisions

- [ADR-001: Terraform repository provisioning](docs/adr/001-terraform-repository-provisioning.md)
- [ADR-002: Consolidate platform infrastructure](docs/adr/002-consolidate-platform-infrastructure.md)

## Migration

The GitHub configuration originates in [github-infrastructure](https://github.com/land-foundry/github-infrastructure). Follow the [migration guide](docs/github-infrastructure-migration.md) before using existing state or retiring the old execution location.
