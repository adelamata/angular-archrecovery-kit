# angular-arch-kit v1.1 — Guide & Usage

Deterministic Architecture Recovery Framework for Large Angular Codebases

---

# 🧠 What is angular-arch-kit?

`angular-arch-kit` is a structured workflow for understanding and safely modifying large Angular applications.

It is designed for:

- human engineers onboarding into large codebases
- AI-assisted development workflows
- architecture recovery in undocumented systems
- safe, incremental feature changes

It is NOT a code generator or refactoring tool.

It is a **deterministic architecture reasoning pipeline**.

---

# 🎯 Core objective

Turn a complex Angular application into:

- a stable architectural model
- clearly defined feature boundaries (bounded contexts)
- reusable knowledge across tasks and agents
- safe execution plans for code changes

---

# ⚙️ Core principle

> No action without structured context.

Every change must pass through:

1. understanding the system
2. isolating the feature
3. defining the task
4. analyzing impact
5. executing safely

---

# 🧭 Execution pipeline (IMPORTANT)

Always follow this order:

1. bootstrap
2. feature-discovery
3. inventory
4. feature-inventory (WIP)
5. task-brief (WIP)
6. impact-analysis (WIP)
7. safe-change (WIP)
8. decision-log (WIP)


Skipping steps reduces correctness and increases risk.

---

# 📦 Step-by-step explanation

## 1. bootstrap

Finds where the system starts.

- entrypoints (main.ts, app.config.ts)
- root providers
- routing root
- runtime initialization

👉 Output: starting point for analysis

---

## 2. feature-discovery

Detects candidate features.

Uses only structural signals:

- routing ownership
- providers scope
- runtime composition

❗ Folder structure is NOT reliable enough alone.

👉 Output: list of feature candidates

---

## 3. inventory

Builds global architecture model.

- validates feature candidates
- builds runtime map
- defines dependency topology
- describes state & data flow
- identifies complexity areas

👉 Output: global system architecture

---

## 4. feature-inventory

Deep analysis of one feature (bounded context).

Includes:

- responsibility
- entrypoints
- state ownership
- dependencies
- integration contracts
- internal structure

👉 Output: feature-level architecture model

---

## 5. task-brief

Defines a safe execution unit before coding.

- scope definition
- affected areas
- constraints
- dependencies involved
- out-of-scope boundaries

👉 Output: execution plan

---

## 6. impact-analysis

Evaluates risk before changing code.

- dependency propagation
- shared services impact
- state risks
- routing risks
- cross-feature effects

👉 Output: risk assessment

---

## 7. safe-change

Executes minimal and safe modifications.

Rules:

- no scope expansion
- no opportunistic refactors
- modify only what is required
- preserve architecture
- respect boundaries

👉 Output: code changes

---

## 8. decision-log

Records architectural decisions.

Used for:

- traceability
- future debugging
- avoiding repeated analysis
- team alignment

---

# 🧩 Core rules

## 1. Bounded context first

Never modify code without isolating the feature first.

---

## 2. Evidence hierarchy

Always prioritize:

runtime > providers > routing > services > folder structure


---

## 3. No full repo scan (except inventory)

Avoid global scanning in feature-level tasks.

---

## 4. No assumptions

If something is not observable → mark as uncertain.

---

## 5. No refactors during analysis

Refactoring only allowed in `safe-change` and only if required.

---

# 🧠 Mental model

Think of this system as:

> a pipeline that reduces uncertainty before touching code

Not:

> a chatbot that explains code

---

# 🚀 Typical usage flows

## Full system understanding

bootstrap → feature-discovery → inventory


## Understand a specific domain

feature-inventory (auth, billing, etc.)

## Prepare a change

task-brief → impact-analysis

## Execute change safely

safe-change

## Record architectural decision

decision-log


---

# ⚠️ What this is NOT

- not a refactoring tool
- not a code generator
- not a documentation replacement
- not a static analysis tool

---

# 🧠 Why this works

Large Angular codebases fail due to:

- unclear boundaries
- implicit architecture
- uncontrolled dependency flow
- lack of shared mental model

This framework enforces:

- explicit structure
- bounded contexts
- deterministic analysis steps
- safe modification workflow

---

# 🏁 Summary

`angular-arch-kit` is a deterministic architecture reasoning system for Angular applications.

It allows teams and AI agents to:

- understand large codebases faster
- reduce uncertainty before changes
- avoid cross-feature breakage
- operate within safe bounded contexts
