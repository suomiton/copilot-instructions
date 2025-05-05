# GitHub Copilot Custom Instructions

## Global Principles
- Prioritise clear, performant, sustainable code; favour guard clauses, SOLID, DRY.
- Obey project **.editorconfig**, **SonarLint**, and existing folder/namespace conventions.
- Use language‑idiomatic patterns; prefer native JS/TS over Lodash and follow design patterns (Refactoring Guru) where sensible.
- Provide concise comments for non‑obvious logic; prefer self‑documenting names.

## Language / Technology Rules
### C#
- Use latest language features (file‑scoped namespaces, records, target‑typed `new`).
- Async methods return `Task`/`Task<T>` and end with `Async`; use `ConfigureAwait(false)` off UI threads.
- Optimise LINQ for translation to NHibernate HQL; avoid client‑side evaluation.
- Manage resources with `using`; minimise allocations; prefer structs when value‑semantics.

### React (TSX)
- Functional components only; hooks over classes.  
- Internal functions → arrow syntax; top‑level helpers → `function` syntax.
- Memoise with `useMemo`/`useCallback` pragmatically; split bundles with dynamic import.

### JavaScript / TypeScript
- Strict types, `const`/`let`, no implicit `any`; use functional array methods.
- Enforce strict null checks; avoid high‑frequency timers.

### SQL Server
- No `SELECT *`; parameterise queries; design indexes deliberately.

### Azure (code focus only)
- Prefer Azure SDK v2+ / track2 libraries.  
- Use async I/O (`BlobClient.UploadAsync` etc.).  
- Default to serverless (Azure Functions, Logic Apps) where sample requires execution context.  
- Apply `DefaultAzureCredential` over connection‑string secrets.

### Rust
- `rustfmt` + `clippy --deny warnings`; forbid unsafe unless justified (`// SAFETY:`).
- No `unwrap()`/`expect()` in production paths; use `Result<T,E>` + `?`.
- Exploit iterators & zero‑copy slices; embrace ownership & borrowing.
- Use `tokio` (or runtime in project) for async; avoid blocking in async contexts.

## Environmental Sustainability
- Minimise network calls & allocations; prefer event‑driven over polling; cache where feasible.

## Output Expectations
- Short, complete snippets; highlight required imports; avoid deprecated APIs.
