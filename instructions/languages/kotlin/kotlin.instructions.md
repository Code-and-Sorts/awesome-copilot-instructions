# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this project. The goal is to ensure consistent, high-quality code generation aligned with our conventions, stack, and best practices.

## 🧠 Context

- **Project Type**: Android App / REST API / CLI Tool / Multiplatform Library
- **Language**: Kotlin
- **Framework / Libraries**: Ktor / Spring Boot / Exposed / Retrofit / Koin / Coroutines
- **Architecture**: MVVM / Clean Architecture / Hexagonal / Modular

## 🔧 General Guidelines

- Use Kotlin-idiomatic syntax and features (e.g., data classes, extension functions).
- Prefer immutable data (`val`) over mutable (`var`).
- Use null safety, smart casting, and Elvis operators effectively.
- Favor expression-style syntax and scoped functions (`let`, `apply`, `run`, `with`).
- Keep files and functions concise and focused.
- Use `ktlint` or `detekt` for formatting and code style.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
src/
  main/
    kotlin/
      com/
        example/
          app/
            controller/
            service/
            repository/
            model/
            config/
    resources/
  test/
    kotlin/
      com/
        example/
          app/
            unit/
            integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use data classes for DTOs and model representations.
- Use sealed classes and `when` expressions for state/result handling.
- Leverage Coroutines for async and non-blocking operations.
- Use dependency injection via Koin or Hilt.
- Validate input using annotations (`javax.validation`) or custom validators.
- Handle errors using `Result`, `sealed class`, or exception mapping.
- Prefer composition over inheritance.
- Document public classes and functions with KDoc.

### 🚫 Patterns to Avoid

- Don’t ignore nullability warnings—handle them explicitly.
- Avoid excessive use of `!!` (force unwrap).
- Don’t expose mutable internal state—prefer immutable interfaces.
- Avoid using `lateinit` unless absolutely necessary.
- Don’t overuse global objects or singletons without lifecycle management.
- Avoid mixing UI and business logic in ViewModels or controllers.

## 🧪 Testing Guidelines

- Use `JUnit 5` or `Kotest` for unit and integration tests.
- Use `MockK` for mocking and verifying interactions.
- Use Coroutines test utilities for suspending functions.
- Structure tests by feature and follow the AAA (Arrange-Act-Assert) pattern.
- Test state flows and edge/error conditions.

## 🧩 Example Prompts

- `Copilot, create a Ktor route that handles a GET request for a list of users.`
- `Copilot, define a sealed class for representing success and failure states.`
- `Copilot, write a Kotlin data class for a Book with title, author, and optional year.`
- `Copilot, write a unit test for the fetchWeatherData() function using MockK.`
- `Copilot, implement a ViewModel with a StateFlow for UI state management.`

## 🔁 Iteration & Review

- Always review Copilot output for idiomatic Kotlin usage and safety.
- Guide Copilot with inline comments when generating complex logic.
- Refactor verbose Java-style patterns into concise Kotlin equivalents.
- Run linters (`ktlint`, `detekt`) as part of your CI/CD pipeline.

## 📚 References

- [Kotlin Language Documentation](https://kotlinlang.org/docs/home.html)
- [Kotlin Coding Conventions](https://kotlinlang.org/docs/coding-conventions.html)
- [Ktor Framework Docs](https://ktor.io/docs/)
- [Spring Boot with Kotlin](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#getting-started.kotlin)
- [Koin for Kotlin](https://insert-koin.io/)
- [MockK](https://mockk.io/)
- [Kotest](https://kotest.io/docs/)
- [Coroutines Guide](https://kotlinlang.org/docs/coroutines-guide.html)
- [KDoc Reference](https://kotlinlang.org/docs/kotlin-doc.html)
