# GitHub Infrastructure Migration

## Source and destination

The configuration was copied from [github-infrastructure at 45f4be9](https://github.com/land-foundry/github-infrastructure/tree/45f4be901f02ed43969044d671b1863740068f70) into `github/`. Terraform files, examples, and license are unchanged. The provider lock file retains version 6.13.0 and adds the signed Linux AMD64 package checksum needed for validation on this platform. The provisioning ADR is preserved under `docs/adr/` with a location note; its original Proposed status is retained.

The source has no committed backend or automation workflow. No state files were found in the available workspace during preparation. These observations do not prove that resources have never been applied or that state does not exist outside this workspace.

## Cutover

1. Merge the destination PR before retiring the source configuration. Stop using the old location for plans and applies during cutover; do not run two independent states against the same repositories.
2. Identify the actual operator, complete repository inventory, state storage, workspace selection, and any external jobs or backend configuration. Check outside this workspace for existing local or remote state before planning from an empty state.
3. If state exists, back it up securely and preserve its backend identity, workspace, and inventory when executing from `github/`. If local state must be relocated, handle it outside Git under the operator's control. No resource address changes are needed for this directory-only move. Do not re-import resources already tracked by the existing state. A backend change is a separate reviewed migration.
4. If no resources have been applied, select persistent state storage and locking before an authorized apply. Use the standalone examples only as empty-state previews, as described in the GitHub README.
5. From `github/`, run `terraform init -input=false`, `terraform fmt -check -recursive`, and `terraform validate` with the pinned Terraform version. With the actual backend, credentials, workspace, and complete inventory, generate and review a plan. For previously managed resources, relocation alone should produce no resource changes. Investigate any create, replacement, deletion, or unrelated settings update before proceeding.
6. Update external execution references to the new repository and directory, keeping GitHub credentials and execution independent of GCP. No in-repository workflow exists to migrate.
7. After the destination is merged and the applicable state/plan checks pass, merge the source retirement PR and archive github-infrastructure with its migration notice intact. Until then, treat the source retirement PR as pending and avoid applying from either location during cutover.

This change does not authorize Terraform apply or import. A live continuity plan has not been run as part of source relocation because the actual state, inventory, and operator credentials have not been established. Archive only after the cutover checks are complete.
