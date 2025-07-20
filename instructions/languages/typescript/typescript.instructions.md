# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this TypeScript project. The goal is to ensure consistent, high-quality code generation aligned with TypeScript conventions, modern tooling, and our architecture standards.

## 🧠 Context

- **Project Type**: REST API / Frontend UI / CLI Tool / Library
- **Language**: TypeScript
- **Framework / Libraries**: Express / React / Next.js / NestJS / Zod / Prisma / Axios / ts-node
- **Architecture**: Modular Monolith / Clean Architecture / Microservices / Domain-Driven Design

## 🔧 General Guidelines

- Use idiomatic TypeScript—always prefer type safety and inference.
- Use `interface` or `type` aliases to define data structures.
- Always enable `strict` mode and follow the project's `tsconfig.json`.
- Prefer named functions, especially for reuse and testability.
- Use `async/await` over raw Promises and avoid `.then().catch()` chains.
- Keep files small, focused, and well-organized.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
src/
  controllers/
  services/
  repositories/
  schemas/
  middlewares/
  utils/
  config/
  types/
tests/
  unit/
  integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use **Dependency Injection** and **Separation of Concerns**.
- Validate input using [Zod](https://zod.dev/) or class-validator.
- Use custom error classes for API and business logic errors.
- Handle errors with centralized middleware.
- Use `dotenv` or similar for config management.
- Prefer `axios` or `fetch` with interceptors for API calls.
- Structure logic around clear modules and services.

### 🚫 Patterns to Avoid

- Avoid using `any` unless explicitly needed.
- Don’t duplicate logic across controllers and services.
- Avoid deeply nested callbacks or overly clever code.
- Do not commit hardcoded secrets or tokens.
- Avoid global state unless using scoped context providers (in React).

## 🧪 Testing Guidelines

- Use `Jest` or `Vitest` for unit and integration tests.
- Test business logic in services; mock dependencies using `ts-mockito` or `jest.mock` for unit tests.
- Use `supertest` for API route integration tests (Express/Nest).
- Follow TDD when feasible for critical features.
- Include coverage reports and snapshot testing for UI.

## 🧩 Example Prompts

- `Copilot, generate an Express route handler that creates a new user with Zod validation.`

- `Copilot, define a TypeScript interface for a Product with optional description and required id and price.`

- `Copilot, write a React hook that debounces a search input.`

- `Copilot, implement a service method to fetch user data using Axios and handle retry on 500 errors.`

- `Copilot, write a Jest test for the calculateDiscount function with mock inputs.`

## 🔁 Iteration & Review

- Always review and refine Copilot output.
- If output doesn’t follow these conventions, rewrite the prompt or break the task into smaller pieces.
- Add a comment above your cursor with intent if Copilot is giving poor suggestions.
- Avoid merging Copilot-generated code without a review.

## 📚 References

- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [Zod Docs](https://zod.dev/)
- [Jest Docs](https://jestjs.io/docs/getting-started)
- [Project Style Guide](https://ts.dev/style/)
