# Angular Architecture Inventory — Deterministic v2

You are analyzing a large Angular codebase.

Your task is to extract a stable architectural inventory of the current system.

This output will be reused by engineers and later AI agents.

Your objective is architectural extraction, not interpretation.

Do not refactor.
Do not redesign.
Do not speculate.

Only describe what can be reasonably supported by observable code structure.

When evidence is weak, state uncertainty explicitly.

---

# Deterministic operating rule

Use this workflow strictly.

Do not skip phases.

Do not scan the repository exhaustively.

Expand from runtime composition outward.

Phase order is mandatory.

---

# Phase 1 — Runtime map

Inspect first:

- `main.ts`
- `app.config.ts`
- `app.routes.ts`
- bootstrap configuration
- root provider registration

Extract only:

- application entrypoint
- bootstrap sequence
- root providers
- root routing composition
- runtime initialization before first feature render

At this phase do not infer feature boundaries yet.

---

# Phase 2 — Candidate feature boundaries

Identify candidate feature boundaries.

A boundary should only be considered valid if at least **two** of the following are true:

- owns route subtree
- owns local state coordination
- owns API orchestration
- owns isolated providers
- owns bounded internal component composition
- has a clear business responsibility

If fewer than two conditions hold, do not classify it as a feature boundary.

For each candidate feature capture:

- name
- evidence
- confidence: high / medium / low

Prefer runtime ownership over folder grouping.

---

# Phase 3 — Shared platform capabilities

Identify cross-cutting technical layers.

Examples:

- authentication
- API abstraction
- routing infrastructure
- shared UI primitives
- logging
- analytics
- configuration
- feature flags
- permissions
- error handling
- caching
- shared state infrastructure

Only include capabilities that are observable.

For each capability capture:

- role
- where it is composed
- who consumes it

---

# Phase 4 — Dependency topology

Using only validated feature boundaries, extract structural dependency behavior.

Describe only:

- dominant dependency direction
- coupling hotspots
- shared dependency concentration
- fragile integration paths
- stable boundaries

Do not enumerate imports.

Do not describe individual files unless structurally important.

---

# Phase 5 — State and data model

Describe:

- where state originates
- where state is coordinated
- how state propagates
- how data enters the system
- transformation layers
- UI consumption path

Identify only dominant patterns.

Do not attempt exhaustive coverage.

---

# Phase 6 — Complexity signals

Identify only observable structural complexity.

Examples:

- hidden coupling
- large orchestration surfaces
- state diffusion
- broad shared dependencies
- unclear ownership
- fragile initialization paths

Do not propose solutions.

---

# Evidence rules

Prefer evidence in this priority order:

1. runtime composition
2. provider registration
3. routing ownership
4. dependency structure
5. feature-local orchestration
6. folder naming

Folder naming alone is weak evidence.

When a conclusion depends mostly on naming, mark confidence low.

---

# Output format

Use exactly this structure.

# System Overview

Short high-signal description.

# Runtime Map

- entrypoint
- bootstrap
- root providers
- root routing
- runtime initialization

# Feature Boundaries

For each feature:

- name
- responsibility
- evidence
- confidence

# Shared Platform Capabilities

List cross-cutting capabilities.

# Dependency Topology

Structural dependency behavior.

# State and Data Flow

Dominant state and data movement.

# Complexity Signals

Observed structural friction.

# Safe Decomposition Candidates

Boundaries suitable for later localized analysis.

# Five-Minute Onboarding

What a new engineer should understand first.

---

# Output constraints

Be concrete.

Prefer stable structural observations.

Prefer signal over coverage.

Avoid generic Angular explanations.

Do not narrate exploration process.

Do not propose refactors.

Document current architectural reality only.

---

# Persistence

Write the final result to:

.angular-arch-kit/memory/inventory.md
