# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this project. The goal is to ensure consistent, high-quality code generation aligned with our conventions, stack, and best practices.

## 🧠 Context

- **Project Type**: Game Script / CLI Tool / Plugin / Embedded Config
- **Language**: Lua
- **Framework / Libraries**: LÖVE / Neovim / OpenResty / LuaSocket / Busted
- **Architecture**: Modular / Event-Driven / Data-Driven

## 🔧 General Guidelines

- Use idiomatic Lua conventions (e.g., snake_case for variables, PascalCase for modules).
- Prefer local variables and encapsulate state in tables or closures.
- Keep functions short and focused.
- Avoid deeply nested logic and long procedural files.
- Use metatables only when necessary and document their behavior.
- Format consistently (e.g., stylua or lua-fmt).
- Prefer readability over cleverness or optimization.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
src/
  core/
  modules/
  utils/
  config/
  assets/
tests/
  unit/
  integration/
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use `require` and module tables to organize code.
- Prefer composition over inheritance (use tables with methods).
- Use tables and closures to manage state and encapsulate behavior.
- Return module tables from Lua files to expose public APIs.
- Use assert statements and logging for debug purposes.
- For Neovim: use `vim.api.*` safely with fallback logic.

### 🚫 Patterns to Avoid

- Don’t use global variables—always declare with `local`.
- Avoid monkey patching standard libraries.
- Don’t mix logic and configuration in the same file.
- Avoid unnecessary metatable magic or side effects.
- Don’t load or execute dynamic code (`loadstring`, etc.) without strong sandboxing.
- Avoid excessive string concatenation in loops (use `table.concat`).

## 🧪 Testing Guidelines

- Use `busted` for unit testing.
- Structure tests to verify modules/functions independently.
- Use mocks or stubs for I/O or system-level dependencies.
- Validate behavior with positive, edge, and error cases.
- Keep test setup minimal—favor self-contained tests.

## 🧩 Example Prompts

- `Copilot, create a Lua module that exposes two functions: add and subtract.`
- `Copilot, implement a timer system using LÖVE callbacks.`
- `Copilot, write a Neovim Lua config that maps <leader>f to :Telescope find_files.`
- `Copilot, write a test using busted for a function that reverses a string.`
- `Copilot, create a config loader that reads a Lua table from a file.`

## 🔁 Iteration & Review

- Always review Copilot output for global leakage or misused metatables.
- Refactor output to follow Lua idioms and avoid verbose patterns.
- Use comments to describe intent if generating complex logic.
- Test all modules with `busted` before accepting new Copilot code.

## 📚 References

- [Programming in Lua (Official Book)](https://www.lua.org/pil/)
- [Lua 5.4 Reference Manual](https://www.lua.org/manual/5.4/)
- [LÖVE 2D Documentation](https://love2d.org/wiki/Main_Page)
- [Busted Testing Framework](https://github.com/lunarmodules/busted)
- [Stylua Formatter](https://github.com/JohnnyMorganz/StyLua)
