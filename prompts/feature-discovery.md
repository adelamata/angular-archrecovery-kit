Identify feature boundaries in an Angular codebase.

Use only:
- routing structure
- provider scopes
- runtime composition
- lazy-loaded modules

Do NOT use folder structure as primary signal.

A valid feature boundary must satisfy at least 2:
- owns route subtree
- owns state
- owns API orchestration
- owns isolated providers
- has bounded internal composition

Output:
- candidate features
- evidence per feature
- confidence level