<!-- Shared instructions source:
Repository: https://github.com/land-foundry/agentic-registry
Artifact: instructions/engineering-restraint/AGENTS.md
Commit: 013c578db9faf6c1fc06a4765040cc5b6610f290
Destination: AGENTS.md, between the shared-instructions markers below.
Update the copied content and source commit together through a reviewed PR.
Preserve repository-specific guidance outside the markers.
-->

<!-- BEGIN SHARED INSTRUCTIONS -->
# Engineering Restraint

Apply these principles to code, tests, documentation, configuration, and automation.

- **Every line is technical debt.** Add content only when it contributes to the requested outcome, clarity, correctness, or necessary validation. Remove unnecessary additions before completing the change. Do not compress useful content merely to reduce line count.
- **KISS — Keep It Simple, Stupid.** Prefer the simplest understandable solution that meets demonstrated requirements. Avoid speculative abstractions, options, extension points, and infrastructure.
- **DRY — Don't Repeat Yourself.** Reuse existing capabilities and maintain one authoritative source for each rule or piece of knowledge. Do not combine superficially similar concerns that need to evolve independently.
- **High cohesion.** Keep related responsibilities and information together. Each module, document, and change should have a clear purpose.
- **Low coupling.** Minimize dependencies, hidden assumptions, and changes that require unrelated components or documents to move together.

Before adding, inspect what already exists. Keep implementation within the requested scope. Before finishing, review the change for unnecessary structure, duplication, and content. Propose unrelated improvements separately.

Resolve tensions using correctness, understandability, and the requested outcome. Do not pursue any principle mechanically.
<!-- END SHARED INSTRUCTIONS -->

## Repository-Specific Guidance

This repository owns platform infrastructure across providers. Read README.md and the relevant Terraform root's documentation before changing infrastructure. GitHub provisioning lives in github/; GCP configuration has not yet been introduced. Keep each root's state, credentials, provider lock file, and plan/apply execution independent. Run Terraform commands from the affected root and do not combine GitHub and GCP resources into one state. Preserve unrelated GitHub settings during adoption; existing repositories require from_template=false and a reviewed import mapping. Do not run terraform import or terraform apply without explicit authorization. Do not commit state, saved plans, credentials, or provider binaries. Validate formatting, configuration, and applicable plan actions; distinguish validation and planning from changes applied to resources. Follow docs/github-infrastructure-migration.md before using any existing GitHub state from the old repository.
