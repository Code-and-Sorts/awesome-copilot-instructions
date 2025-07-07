<!--lint disable remark-lint:awesome-badge-->

#

<!-- [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re) -->
<div align="center">
  <img src="./imgs/awesome-github-copilot.svg" alt="Awesome Copilot Instructions" height="300">
</div>

<h4 align="center">✨ A curated list of awesome GitHub copilot-instructions.md files for enhancing your GitHub Copilot AI experience.</h4>

<!--lint enable remark-lint:awesome-badge-->

<p align="center">
  <a href="hhttps://awesome.re">
    <img src="https://awesome.re/badge-flat2.svg" alt="Awesome">
  </a>
</p>

<hr>

<hr>
<p align="center">
 <a href="CONTRIBUTING.md">📖 Contribution Guide</a>
</p>
<br>

## Contents

- [Why Copilot Instructions](#why-copilot-instructions)
- [Copilot Instructions](#copilot-instructions)
  - [Boilerplates & Templates](#boilerplates--templates)
  - [Language & Stack](#language--stack)
  - [Framework / Library](#framework--library)
  - [Tools](#tools)
  - [Workflows](#workflows)
- [How to Use](#how-to-use)

## Why Copilot Instructions

`copilot-instructions.md` and `*.instructions.md` files help guide GitHub Copilot by providing contextual details about your repository such as the type of workflow your team follows, tools and other project specific details such as coding style, frameworks used or project specific rules.

**Tip**: Learn more about Copilot Instructions in the [VS Code documentation](https://code.visualstudio.com/docs/copilot/copilot-customization).

## Copilot Instructions

### Boilerplates & Templates

#### Language Templates

- [Standard Language Template](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/templates/standard-language/copilot-instructions.md)

### Language & Stack

#### C

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/c/standard-focus/copilot-instructions.md)

#### C-Sharp

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/csharp/standard-focus/copilot-instructions.md)

#### C++

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/cplusplus/standard-focus/copilot-instructions.md)

#### Go

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/go/standard-focus/copilot-instructions.md)

#### Java

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/java/standard-focus/copilot-instructions.md)

#### JavaScript

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/javascript/standard-focus/copilot-instructions.md)

#### Kotlin

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/kotlin/standard-focus/copilot-instructions.md)

#### Lua

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/lua/standard-focus/copilot-instructions.md)

#### Python

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/python/standard-focus/copilot-instructions.md)

#### Rust

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/rust/standard-focus/copilot-instructions.md)

#### Swift

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/swift/standard-focus/copilot-instructions.md)

#### TypeScript

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/languages/typescript/standard-focus/copilot-instructions.md)

### Framework / Library

#### Cobra CLI (Go)

- [Charmbracelet Bubbles CLI](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/frameworks/cobra-cli-go/charmbracelet-cli/copilot-instructions.md)

#### Node.js (TypeScript)

- [Azure Function App](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/frameworks/nodejs-typescript/azure-function-app/copilot-instructions.md)
- [Express API](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/frameworks/nodejs-typescript/express-api/copilot-instructions.md)

### Tools

#### Content Management Systems (CMS)

##### Drupal

- [Standard Focus for Drupal 11](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/tools/cms/drupal/11/standard-focus/copilot-instructions.md)

#### Infra as Code (IaC)

##### Terraform

- [Standard Focus](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/tools/infra-as-code/terraform/standard-focus/copilot-instructions.md)
- [Atmos](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/tools/infra-as-code/terraform/atmos/copilot-instructions.md)

### Workflows

#### AI Development Tasks

A comprehensive workflow for AI-assisted development featuring structured approaches to planning, task generation, and execution:

- [PRD Creation](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/prd-creation/prd-creation.instructions.md) - Create detailed Product Requirements Documents. ([prompt](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/prd-creation/prd-creation.prompt.md))
- [Task Generation](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/task-generation/task-generation.instructions.md) - Break PRDs into actionable development tasks. ([prompt](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/task-generation/task-generation.prompt.md))
- [Task Execution](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/task-execution/task-execution.instructions.md) - Systematic task execution with proper testing and git practices. ([prompt](https://github.com/osiris/awesome-copilot-instructions/blob/main/instructions/workflows/ai-development-tasks/task-execution/task-execution.prompt.md))

## How to Use

### Setup Copilot in VSCode

1. Hover over the Copilot icon in the Status Bar and select Set up Copilot.
2. Select **Sign in** to sign in to your GitHub account or **Use Copilot** if you're already signed in.

**Tip**: Read more about setup [here](https://code.visualstudio.com/docs/copilot/setup).

### Setup Instructions

1. Set the `github.copilot.chat.codeGeneration.useInstructionFiles` setting to `true` to instruct Copilot in VS Code to use the custom instructions file.
2. Create instruction files using the latest naming conventions: **Workspace instructions** (place `*.instructions.md` files in `.github/instructions/` directory), **Workspace prompts** (place `*.prompt.md` files in `.github/prompts/` directory), or **Legacy format** (`.github/copilot-instructions.md` still supported).

#### File Types

**`.instructions.md`**: Contextual instructions that apply to specific files or file types.

**`.prompt.md`**: Reusable prompts for specific tasks or workflows.

**Front matter**: Use YAML front matter to specify metadata like `applyTo`, `mode`, and `description`.

**Tip**: Read more about the latest naming conventions in the VS Code documentation.

## Contributing

All contributions are welcome! If you would like to share instruction files (`.instructions.md`) or prompt files (`.prompt.md`), see the [contribution guide](CONTRIBUTING.md) for details.
