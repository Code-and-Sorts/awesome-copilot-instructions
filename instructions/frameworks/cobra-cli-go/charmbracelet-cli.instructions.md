# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Go project. The goal is to ensure consistent, high-quality code generation aligned with Go idioms, the chosen architecture, and our team's best practices.

## 🧠 Context

- **Project Type**: CLI Tool
- **Language**: Go
- **Framework / Libraries**: cobra, testify, charmbracelet/bubbles
- **Architecture**: Modular MVU (Model-View-Update) + Command Pattern

## 🔧 General Guidelines

- Follow idiomatic Go conventions (<https://go.dev/doc/effective_go>).
- Use named functions over long anonymous ones.
- Organize logic into small, composable functions.
- Prefer interfaces for dependencies to enable mocking and testing.
- Use `gofmt` or `goimports` to enforce formatting.
- Avoid unnecessary abstraction; keep things simple and readable.
- Use `context.Context` for request-scoped values and cancellation.

## 👾 TUI Guidelines

- **Component Structure:**
  - Each distinct UI element or view should generally be implemented as its own `bubble`.
  - Follow the standard `bubbles` pattern:
    - `Model`: Struct containing the component's state.
    - `Init()`: Returns the initial command (often `nil`).
    - `Update(msg tea.Msg)`: Handles incoming messages/events and updates the model. Returns `(tea.Model, tea.Cmd)`.
    - `View()`: Renders the component's UI as a string based on the current model state.
  - Keep `Update` functions focused; delegate complex logic to helper methods or separate functions.
  - Use `tea.BatchMsg` to batch multiple commands returned from `Update`.

- **State Management:**
  - Prefer local state within each component's `Model`.
  - For shared state or communication between components, use `tea.Msg` passing:
    - Parent components can pass messages down during their `Update`.
    - Child components can send messages up for the parent (or root) `Update` function to handle.
  - Avoid global state for TUI components. If necessary, inject shared dependencies (like services or data repositories) into the root TUI model during initialization.

- **Interaction & Messages:**
  - Define custom `tea.Msg` types (structs or simple types) for specific application events (e.g., `dataLoadedMsg`, `errorOccurredMsg`, `itemSelectedMsg`).
  - Use `tea.KeyMsg` for handling keyboard input within `Update`. Check `key.Type` or use `key.Matches`.
  - Commands (`tea.Cmd`) should be used for I/O operations (API calls, DB access, timers) to avoid blocking the `Update` loop. The results of these commands should be sent back as `tea.Msg`.

- **Styling:**
  - Use `lipgloss` for styling text, borders, layouts, etc.
  - Define reusable styles in `internal/util/styles.go` and reference them within component `View` methods.
  - Ensure styles adapt reasonably to different terminal sizes where possible.

- **Layout:**
  - Use `lipgloss` functions like `lipgloss.JoinVertical`, `lipgloss.JoinHorizontal`, and `lipgloss.Place` for arranging components.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
app/
  app.go
cmd/
  root.go
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
- Logging should be handled via `charmbracelet/log`.
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

## 🔁 Iteration & Review

- Review Copilot output before committing.
- Refactor generated code to ensure readability and testability.
- Use comments to give Copilot context for better suggestions.
- Regenerate parts that are unidiomatic or too complex.

## 📚 References

- [Go Style Guide](https://google.github.io/styleguide/go/)
- [Effective Go](https://go.dev/doc/effective_go)
- [Standard Go Project Layout](https://github.com/golang-standards/project-layout)
- [Testify](https://github.com/stretchr/testify)
- [Go Validator](https://github.com/go-playground/validator)
- [Charmbracelet Bubbletea Documentation](https://pkg.go.dev/github.com/charmbracelet/bubbletea)
