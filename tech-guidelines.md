
# NHS England Tech Guidelines

## Core Principles

### I. Mainstream, Governed Platform Adoption
Every delivery decision must favour mainstream, approved tools and platforms from the NHS Tech Radar and NHS Tech Stack.
- Prefer established, supported technologies over niche or legacy alternatives.
- Standardize on common build, test, deploy, and infrastructure tooling to reduce cognitive load.
- Use approved managed services and cloud-native patterns when they improve reliability and operational efficiency.

### II. Security, Compliance, and Dependency Hygiene by Default
Security and compliance are non-negotiable requirements for every change.
- Integrate vulnerability scanning, secret scanning, and dependency management into the default pipeline.
- Enforce security controls through automation rather than manual checkpoints wherever possible.
- Record any approved deviation in an ADR and justify why the mainstream guidance cannot be followed.

### III. Independent, Incremental Delivery
Work must be split into independently testable, demonstrable increments.
- Each user story should deliver measurable value and be workable in isolation.
- Build minimum viable increments first and validate them before expanding scope.
- Avoid monolithic design changes in favour of small, user-focused iterations.

### IV. Automated Quality, Observability, and Governance
Quality and operational readiness must be visible and automated.
- Gate changes with tests, static analysis, security scans, and peer review.
- Instrument code and services for observability, diagnostics, and supportability.
- Use CI/CD as the default delivery path for validation, release, and rollback.

### V. Simplicity, Explicit Architecture, and Maintainability
Architecture decisions must be explicit, minimal, and easy to maintain.
- Choose the simplest tool or pattern that satisfies the requirement.
- Avoid unsupported, legacy, or overly complex technologies.
- Document non-obvious decisions, trade-offs, and exception paths clearly.

## Technology Governance
The radar provides the baseline for permitted technology choices.
- Approved stack guidance includes GitHub, GitHub Actions, Terraform, Python, TypeScript, React, Next.js, Flask, Kubernetes, AWS/Azure mainstream services, and the security/observability tooling shown in the radar.
- Use the mainstream category for new production adoption; use proposed only with a documented review and approval path.
- Avoid contained or avoided technologies unless a formal exception is recorded and approved.
- Capture architectural decisions and exceptions in ADRs, and link them from feature plans and PRs.

## Development Workflow
The workflow must preserve independence, visibility, and constitution compliance.
- Start with a feature spec, then plan implementation in discrete phases: setup, foundation, incremental stories, polish.
- Use the plan template’s Constitution Check to verify alignment before Phase 0 research and again after design changes.
- Require peer review on every change, with an explicit checklist for tests, security, observability, and architecture rationale.
- Prefer evidence-based decisions: failing tests before code, automation through CI/CD, and documented exceptions for deviations.

## Governance
This constitution is authoritative for tool selection, delivery practices, quality gates, and exception handling.
- All work must align with these principles unless a documented governance exception is approved.
- Amendments require a written rationale, team review, and a version bump following semantic versioning.
- PRs must include evidence of compliance: relevant tests, scan results, ADR links for exceptions, and a summary of how the change maps to the constitution.
- Complexity must be justified, with simpler alternatives considered and rejected in writing.
- Use the constitution as the baseline for planning, review, and handover; do not rely on undocumented tribal knowledge.

**Version**: 1.0.1 | **Ratified**: 2026-05-21 | **Last Amended**: 2026-05-21
