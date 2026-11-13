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

This repository is intended to hold Terraform for the GCP environment; its current contents are only a README. Do not assume providers, backend configuration, modules, credentials, or validation commands exist. Inspect the configuration and document applicable validation as infrastructure is introduced. Keep infrastructure changes scoped to the requested environment and distinguish validation or planning from changes applied to cloud resources.
