# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Go project. The goal is to ensure consistent, high-quality code generation aligned with Go idioms, the chosen architecture, and our team's best practices.

## 🧠 Context

- **Project Type**: CLI Tool / REST API / Microservice
- **Language**: Go
- **Framework / Libraries**: net/http, gorilla/mux, cobra, go.uber.org/zap, sqlx, testify
- **Architecture**: Clean Architecture with Repository Pattern

## 🔧 General Guidelines

- Follow idiomatic Go conventions (<https://go.dev/doc/effective_go>).
- Use named functions over long anonymous ones.
- Organize logic into small, composable functions.
- Prefer interfaces for dependencies to enable mocking and testing.
- Use `gofmt` or `goimports` to enforce formatting.
- Avoid unnecessary abstraction; keep things simple and readable.
- Use `context.Context` for request-scoped values and cancellation.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
cmd/
  myapp/
    main.go
internal/
  controller/
  service/
  repository/
  model/
  config/
  middleware/
  utils/
pkg/
  logger/
  errors/
tests/
  unit/
  integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use **Clean Architecture** and **Repository Pattern**.
- Implement input validation using Go structs and validation tags (e.g., [go-playground/validator](https://github.com/go-playground/validator)).
- Use custom error types for wrapping and handling business logic errors.
- Logging should be handled via `zap` or `log/slog`.
- Use dependency injection via constructors (avoid global state).
- Keep `main.go` minimal—delegate to `internal`.

### 🚫 Patterns to Avoid

- Don’t use global state unless absolutely required.
- Don’t hardcode config—use environment variables or config files.
- Don’t panic or exit in library code; return errors instead.
- Don’t expose secrets—use `.env` or secret managers.
- Avoid embedding business logic in HTTP handlers.

## 🧪 Testing Guidelines

- Use `testing` and [testify](https://github.com/stretchr/testify) for assertions and mocking.
- Organize tests under `tests/unit/` and `tests/integration/`.
- Mock external services (e.g., DB, APIs) using interfaces and mocks for unit tests.
- Include table-driven tests for functions with many input variants.
- Follow TDD for core business logic.

## 🧩 Example Prompts

- `Copilot, generate a REST endpoint using gorilla/mux that returns a list of users from a repository.`
- `Copilot, write a Go struct for user registration input with validation tags for email and required password.`
- `Copilot, implement a Cobra CLI command called ‘serve’ that reads config from environment variables.`
- `Copilot, write a unit test for the CalculateDiscount function with multiple input cases using testify.`
- `Copilot, create a repository interface and its SQLX implementation for managing books.`

## 🔁 Iteration & Review

- Review Copilot output before committing.
- Refactor generated code to ensure readability and testability.
- Use comments to give Copilot context for better suggestions.
- Regenerate parts that are unidiomatic or too complex.

## 📚 References

- [Go Style Guide](https://google.github.io/styleguide/go/)
- [Effective Go](https://go.dev/doc/effective_go)
- [Standard Go Project Layout](https://github.com/golang-standards/project-layout)
- [Zap Logger](https://pkg.go.dev/go.uber.org/zap)
- [Testify](https://github.com/stretchr/testify)
- [Go Validator](https://github.com/go-playground/validator)
