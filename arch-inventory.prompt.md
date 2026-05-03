# /inventory

Build an ultra-compact mental map of the current Angular project for immediate onboarding.

Your goal is to answer:
👉 “What does a new engineer need to understand in 5 minutes to orient themselves inside this codebase?”

Do not perform deep architectural audits.
Do not explain implementation details.
Do not list the full file tree.
Do not propose refactors.

---

Generates output in English by default if the {$input} does not come in a recognized language

---

## 🎯 Expected Output (MANDATORY)

Return exactly the following sections, write it in a clear, concise manner, and use the provided emojis for better readability and within a file named `inventory.md` inside the `.angular-arch-kit/memory/` folder:

---

## 0. General context

Provide a concise summary of:

- application type (backoffice, SaaS, internal tool, portal, etc.)
- Angular version if detectable
- monorepo or single repository
- approximate scale (small / medium / large)
- high-level architectural style if visible

Keep this section short.

---

## 1. 🧭 What this system is
- What the application does in 1–3 sentences
- Functional domain (e.g., CRM, dashboard, e-commerce, etc.)
- Primary users of the system

---

## 2. 🧱 High-level architecture (Angular mental model)
Explain the system structure at a macro level:

- Feature-based vs module-based vs standalone components
- Routing strategy (lazy loading, feature routes, etc.)
- State management (NgRx / services / signals / hybrid)
- Communication patterns between features

---

## 3. 📦 Core building blocks
List ONLY the essentials:

- Core module / core services (auth, http, interceptors)
- Shared layer (UI kit, pipes, directives)
- Main feature modules
- Layout / shell / app bootstrap structure

---

## 4. 🔁 Data flow (how things move)
Explain simply:

- How a request enters (UI → service → API)
- Where state lives
- How UI ↔ backend synchronization works
- If a store exists: how a typical action flows

---

## 5. 🧩 Key mental entry points
Where a new developer should look first:

- Root app routing
- Main layout / shell component
- Auth flow entry point
- 1–2 key features (most representative ones)

---

## 6. ⚠️ Important conventions (only if critical)
Include only if they actually exist:

- Relevant naming conventions
- Folder structure rules
- Architectural constraints
- Avoided anti-patterns

---

## 7. Structural map

Show only **high-level project structure**. Describe generally the domain of each feature within the example.

Example:

```text
src/app/
  core/
  shared/
  features/
    customers/ 
    orders/ 
    billing/ 
```

---

## 🚫 Exclusions (VERY IMPORTANT)

Do not include:
- Full file listing
- Deep implementation details
- Complex business logic explanations
- Minor dependencies
- Code snippets

---

## 🧠 Style

- Maximum clarity
- Designed for 5-minute reading time
- “Senior onboarding cheat sheet” level
- Clear technical English
- Prioritize understanding over completeness
