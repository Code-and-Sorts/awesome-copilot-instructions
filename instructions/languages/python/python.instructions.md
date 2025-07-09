# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this project. The goal is to ensure consistent, high-quality code generation aligned with our conventions, stack, and best practices.

## 🧠 Context

- **Project Type**: Web API / Data Pipeline / CLI Tool / ML App
- **Language**: Python
- **Framework / Libraries**: FastAPI / Flask / Django / Pandas / Pydantic / Poetry
- **Architecture**: MVC / Clean Architecture / Event-Driven / Microservices

## 🔧 General Guidelines

- Use Pythonic patterns (PEP8, PEP257).
- Prefer named functions and class-based structures over inline lambdas.
- Use type hints where applicable (`typing` module).
- Follow black or isort for formatting and import order.
- Use meaningful naming; avoid cryptic variables.
- Emphasize simplicity, readability, and DRY principles.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
src/
  controllers/
  services/
  repositories/
  schemas/
  utils/
  config/
tests/
  unit/
  integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use the Repository Pattern and Dependency Injection (e.g., via `Depends` in FastAPI).
- Validate data using Pydantic models.
- Use custom exceptions and centralized error handling.
- Use environment variables via `dotenv` or `os.environ`.
- Use logging via the `logging` module or structlog.
- Write modular, reusable code organized by concerns (e.g., controller, service, data layer).
- Favor async endpoints for I/O-bound services (FastAPI, aiohttp).
- Document functions and classes with docstrings.

### 🚫 Patterns to Avoid

- Don’t use wildcard imports (`from module import *`).
- Avoid global state unless encapsulated in a singleton or config manager.
- Don’t hardcode secrets or config values—use `.env`.
- Don’t expose internal stack traces in production environments.
- Avoid business logic inside views/routes.

## 🧪 Testing Guidelines

- Use `pytest` or `unittest` for unit and integration tests.
- Mock external services with `unittest.mock` or `pytest-mock`.
- Use fixtures to set up and tear down test data.
- Aim for high coverage on core logic and low-level utilities.
- Test both happy paths and edge cases.

## 🧩 Example Prompts

- `Copilot, create a FastAPI endpoint that returns all users from the database.`
- `Copilot, write a Pydantic model for a product with id, name, and optional price.`
- `Copilot, implement a CLI command that uploads a CSV file and logs a summary.`
- `Copilot, write a pytest test for the transform_data function using a mock input.`

## 🔁 Iteration & Review

- Review Copilot output before committing.
- Add comments to clarify intent if Copilot generates incorrect or unclear suggestions.
- Use linters (flake8, pylint) and formatters (black, isort) as part of the review pipeline.
- Refactor output to follow project conventions.

## 📚 References

- [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
- [PEP 484 – Type Hints](https://peps.python.org/pep-0484/)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Django Documentation](https://docs.djangoproject.com/en/stable/)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Pytest Documentation](https://docs.pytest.org/en/stable/)
- [Pydantic Documentation](https://docs.pydantic.dev/)
- [Python Logging Best Practices](https://docs.python.org/3/howto/logging.html)
- [Black Code Formatter](https://black.readthedocs.io/)
- [Poetry](https://python-poetry.org/docs/)
