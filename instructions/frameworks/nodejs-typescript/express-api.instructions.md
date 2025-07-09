# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Node.js TypeScript Express API project. The goal is to ensure consistent, high-quality code generation aligned with our conventions, Express best practices, and TypeScript standards.

## 🧠 Context

- **Project Type**: REST API
- **Language**: TypeScript (Node.js)
- **Framework / Libraries**: Express / Zod / dotenv / tslog / ts-node / cors
- **Architecture**: Modular / MVC / Clean Architecture / Layered Services

## 🔧 General Guidelines

- Use idiomatic TypeScript with strict type checking enabled.
- Use named `async` functions and avoid long inline callbacks.
- Validate input using Zod schemas and return structured error responses.
- Organize code with clear separation of concerns (routes → controller → service → repository).
- Use centralized error handling middleware.
- Format code with Prettier and enforce standards with ESLint.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
src/
  routes/
    user.routes.ts
    product.routes.ts
  controllers/
    user.controller.ts
  services/
    user.service.ts
  repositories/
    user.repository.ts
  schemas/
    user.schema.ts
  middleware/
    error.middleware.ts
    auth.middleware.ts
  utils/
  config/
  types/
tests/
  unit/
  integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use `express.Router()` for grouping route handlers by domain.
- Validate request bodies and query params with Zod inside middleware or controllers.
- Return consistent JSON responses with `status`, `message`, and `data`.
- Use dependency injection for service and repository layers when needed.
- Store config and secrets in `.env` and load with `dotenv`.
- Use a logging library (e.g. `tslog`) for structured logging.
- Separate side-effect code (e.g., DB access) from pure functions.

### 🚫 Patterns to Avoid

- Don’t put business logic directly in route handlers.
- Avoid using `any` — always type inputs and outputs.
- Don’t use `console.log` in production — use a logger.
- Don’t hardcode values — pull from config or env vars.
- Avoid monolithic controllers — break down logic into services and helpers.

## 🧪 Testing Guidelines

- Use `Jest` or `Vitest` for unit and integration tests.
- Use `supertest` for HTTP layer testing.
- Mock services and DB calls to isolate controller behavior.
- Use test doubles or stubs for external APIs.
- Test Zod schemas for valid/invalid cases where applicable.

## 🧩 Example Prompts

- `Copilot, create a POST /users endpoint using Express that validates the request body with Zod.`
- `Copilot, implement a user controller that delegates to a user service and returns 201 Created.`
- `Copilot, generate a Zod schema for a product with id, name, and price.`
- `Copilot, write a middleware that handles Zod validation errors and formats a response.`
- `Copilot, create a Jest unit test for the user controller’s createUser function using mocks.`

## 🔁 Iteration & Review

- Review Copilot output with Prettier and ESLint before committing.
- Use comments to guide Copilot when generating controller logic or complex validation.
- Refactor repeated logic into shared utilities or middleware.
- Validate schema contracts and function signatures with type checking.

## 📚 References

- [Express.js Documentation](https://expressjs.com/)
- [Zod Documentation](https://zod.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [tslog Logging](https://github.com/fullstack-build/tslog)
- [dotenv Config Docs](https://github.com/motdotla/dotenv)
- [Jest Documentation](https://jestjs.io/)
- [Supertest for Express](https://github.com/visionmedia/supertest)
- [ESLint Rules for TypeScript](https://typescript-eslint.io/rules/)
- [Prettier Formatter](https://prettier.io/)
