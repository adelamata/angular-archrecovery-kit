# /inventory

Build a high-level architectural inventory of the current Angular project.

Your goal is to describe **how the system is actually organized today** — both from a functional perspective and from a technical perspective.

This inventory is intended for AI-assisted architectural understanding and onboarding.  
It should help answer a simple question:

**If a new engineer joined tomorrow, what would they need to understand in five minutes to orient themselves inside the codebase?**

Do not propose refactors yet.  
Do not perform a deep dependency audit.  
Focus on reconstructing the current shape of the system.

## User input when using this prompt

If ${INPUT} is detected as a accept language, then the output should be in that language. Otherwise, the output should be in English.

When you run this prompt, provide the following input:

## What to inspect first

Start by identifying the project’s functional structure before diving into implementation details.

### 1. Functional map

Determine:

- What business problem does the application solve?
- What are the main product areas, workflows, or domains?
- What are the core user-facing capabilities?

Use signals such as:

- top-level routes
- navigation structure
- feature names
- major screens
- business-oriented folder naming

The objective is to extract the **main functional domains of the application**.

---

### 2. Routing as the primary architectural map

Inspect:

- `app.routes.ts`
- `app-routing.module.ts`
- lazy-loaded routes
- route guards
- layouts / shells

Capture:

- major application areas
- domain boundaries
- authenticated vs public sections
- feature isolation strategy

In large Angular applications, **routing usually reveals the real architecture faster than code-level inspection**.

---

### 3. Structural organization of the codebase

Identify how the code is partitioned.

Look for patterns such as:

- `core`
- `shared`
- `features`
- `domain`
- `data-access`
- `ui`
- `state`

Determine:

- whether the system is organized by business domain or by technical artifact
- whether layers are explicit or implicit
- whether boundaries are clear or porous

This should explain **how engineers are expected to navigate the codebase**.

If you detect a clear architectural pattern (e.g. domain-driven design, feature-based organization, layered architecture), describe it here.

If you detect a folder named features, domain or similar, inspect its structure to determine whether it’s organized by business domain or by technical artifact.

---

### 4. Application bootstrap and global runtime behavior

Inspect:

- `main.ts`
- application bootstrap
- global providers
- interceptors
- app initializers
- authentication initialization
- configuration loading
- feature flags

Answer:

**What happens before the first screen is rendered?**

This usually reveals important cross-cutting architectural behavior.

---

### 5. Data flow and execution path

Pick one representative business flow and follow it end to end.

Examples:

- login
- load dashboard
- create entity
- save form
- fetch user profile

Trace:

**UI → component → service/facade → state → API**

Identify:

- state management approach
- facades or orchestration layers
- side effects
- asynchronous boundaries
- ownership of business logic

Understanding one complete vertical flow usually provides far more insight than reading isolated files.

---

### 6. Domain model and data structures

Inspect:

- models
- interfaces
- DTOs
- mappers
- adapters

Identify:

- core business entities
- naming conventions
- API-to-domain translation patterns
- whether backend DTOs leak directly into UI

This helps reconstruct the **actual domain language of the application**.

---

### 7. Backend integration boundaries

Inspect:

- API clients
- `data-access`
- HTTP services
- interceptors
- authentication
- error handling
- caching

Determine:

- where backend boundaries live
- whether the frontend orchestrates logic or mostly renders remote data
- whether integration patterns are centralized or distributed

---

### 8. Team conventions and architectural signals

Look for conventions in:

- file naming
- folder naming
- suffixes such as `*.facade.ts`, `*.store.ts`, `*.adapter.ts`
- selectors
- actions
- providers
- feature boundaries

These conventions often reveal **the intended mental model of the system**.

---

## Output requirements

Produce a concise architectural inventory that captures:

- functional domains
- routing structure
- architectural layers
- state management approach
- backend integration boundaries
- notable conventions
- important global runtime behavior

Prefer describing **what exists today**, not what should exist.

---

## Output location

Write the result to:

`.angular-arch-kit/memory/inventory.md`

This file acts as persistent architectural memory for AI-assisted exploration of the codebase.
