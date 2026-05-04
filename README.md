# angular-arch-kit v1

Production-oriented repository scaffold for architecture recovery and bounded-context AI workflows in large Angular codebases.

## Repository structure

```text
angular-arch-kit/
  README.md
  prompts/
    inventory.md
    feature-inventory.md
    task-brief.md
    impact-analysis.md
    safe-change.md
  templates/
    inventory-template.md
    feature-template.md
    task-template.md
  memory/
    inventory.md
    feature-map/
    tasks/
    decisions/
  commands/
    inventory.md
    feature.md
    task.md
```

---

## README.md

### Purpose

Create durable architectural context before localized code changes.

The repository is designed for large Angular systems where understanding architecture is more important than generating code immediately.

### Core operating principle

Persist context once.
Reuse it many times.

### Recommended workflow

```text
inventory
  ↓
feature-inventory
  ↓
task-brief
  ↓
impact-analysis
  ↓
safe-change
```

### Operating rules

- Do not scan the entire repository for every task.
- Prefer bounded-context exploration.
- Preserve architectural context across iterations.
- Prefer small localized interventions.
- Do not refactor opportunistically.

---

## prompts/inventory.md

Use the deterministic architecture inventory prompt.

Goal:

Extract runtime structure, feature boundaries, shared platform capabilities, dependency topology, state flow, and safe decomposition candidates.

Write output to:

```text
.angular-arch-kit/memory/inventory.md
```

---

## prompts/feature-inventory.md

```md
Analyze only the requested feature.

Use:

- .angular-arch-kit/memory/inventory.md

Do not scan the full repository.

A feature should be analyzed as a bounded context.

Describe:

- feature purpose
- ownership boundary
- entrypoints
- internal composition
- state ownership
- external dependencies
- inbound consumers
- outbound consumers
- integration contracts
- local complexity
- safe local reasoning boundaries

Write output to:

.angular-arch-kit/memory/feature-map/<feature-name>.md
```

---

## prompts/task-brief.md

```md
Prepare an execution-ready bounded-context task brief.

Use:

- global inventory
- relevant feature inventory

Determine:

- affected bounded context
- relevant files and entrypoints
- expected integration surfaces
- required architectural context
- likely side effects
- out-of-scope areas
- uncertainty requiring validation

Do not implement.

Write output to:

.angular-arch-kit/memory/tasks/<task-name>.md
```

---

## prompts/impact-analysis.md

```md
Analyze change impact before implementation.

Using task brief and architectural context, identify:

- directly affected areas
- indirectly affected areas
- dependency propagation risks
- shared contracts impacted
- state coordination risks
- runtime composition risks
- validation surfaces

Do not propose implementation.
```

---

## prompts/safe-change.md

```md
Implement only the requested localized change.

Use:

- task brief
- feature inventory
- impact analysis

Rules:

- preserve existing architecture
- minimize modification surface
- avoid opportunistic refactors
- do not broaden scope
- preserve contracts unless explicitly required

Before editing, explain:

- exact files to modify
- reason for each modification
- expected behavioral effect
```

---

## templates/inventory-template.md

```md
# System Overview

# Runtime Map

# Feature Boundaries

# Shared Platform Capabilities

# Dependency Topology

# State and Data Flow

# Complexity Signals

# Safe Decomposition Candidates

# Five-Minute Onboarding
```

---

## templates/feature-template.md

```md
# Feature Purpose

# Ownership Boundary

# Entrypoints

# Internal Composition

# State Ownership

# External Dependencies

# Inbound Consumers

# Outbound Consumers

# Integration Contracts

# Complexity Signals

# Safe Local Reasoning Boundaries
```

---

## templates/task-template.md

```md
# Task Summary

# Affected Bounded Context

# Relevant Files

# Integration Surfaces

# Architectural Constraints

# Expected Side Effects

# Out of Scope

# Validation Questions
```

---

## commands/inventory.md

Run the inventory prompt and persist output.

---

## commands/feature.md

Run feature-inventory for one bounded context.

Example:

```text
feature auth
```

---

## commands/task.md

Create a task brief for a localized change.

Example:

```text
task add-authorization-flow
```

---

## First practical usage

1. Run inventory once.
2. Generate feature inventories only for actively touched domains.
3. Create task brief before modifications.
4. Run impact analysis for shared or sensitive areas.
5. Apply safe-change only after scope is explicit.

