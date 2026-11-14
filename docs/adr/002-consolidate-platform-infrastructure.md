# Consolidate Platform Infrastructure in One Repository

* **ID:** 002
* **Date:** 2026-11-14
* **Status:** Proposed
* **Authors:** Land Foundry Engineering

## Context

GitHub repository provisioning is a small Terraform configuration in a dedicated repository. The platform-infrastructure repository previously contained only documentation for intended GCP infrastructure. There is no demonstrated need for different repository access or ownership between these infrastructure domains.

Keeping separate repositories adds navigation and maintenance overhead. Combining all providers into one Terraform root would instead couple credentials, state, and execution unnecessarily.

## Decision

Move GitHub repository provisioning into platform-infrastructure/github/ and broaden this repository's scope to platform infrastructure across providers. Preserve the existing Terraform resource addresses, inputs, provider versions, lock file (adding verified platform checksums as needed), examples, and provisioning decision record.

Keep GitHub and future GCP configurations in independent Terraform roots with separate state, credentials, and plan/apply execution. Keep engineering policy in github-governance and reference it from implementation documentation.

Retire the old execution location only after the destination change is merged and state continuity is verified. Preserve the old repository as archived history with a migration notice after cutover.

## Consequences

- Related infrastructure becomes easier to discover and maintain in one repository.
- A common repository shares its access boundary; reassess separation if maintainers or access requirements diverge.
- Working-directory changes require updated commands and any external automation references.
- Source relocation does not itself migrate state or apply resources. The migration guide requires checking existing state ownership and reviewing a plan before cutover.
