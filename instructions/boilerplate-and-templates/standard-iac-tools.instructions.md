# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this infrastructure-as-code project. The goal is to ensure consistent, secure, and modular infrastructure definitions aligned with our conventions, stack, and best practices.

## 🧠 Context

- **Project Type**: Infrastructure Provisioning / Cloud Architecture
- **Language / Tool**: Terraform / Pulumi / Bicep / AWS CDK / Crossplane
- **Cloud Providers**: Azure / AWS / GCP / Kubernetes
- **Architecture**: Modular / Multi-environment / GitOps / Microservices

## 🔧 General Guidelines

- Follow idiomatic conventions for the IaC tool in use.
- Use modules/components to encapsulate reusable infrastructure logic.
- Use variables and locals for configuration—avoid hardcoded values.
- Prefer secure defaults (e.g., private networks, encryption enabled).
- Include descriptions and constraints on all input variables.
- Use comments to document resource intent and dependencies.
- Format consistently using `terraform fmt`, `bicep format`, or tool-specific formatters.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
infrastructure/
  modules/
    network/
    compute/
    database/
  environments/
    dev/
    staging/
    prod/
  scripts/
  shared/
    variables.tf
    providers.tf
    backend.tf
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use modules to abstract cloud services and encourage reuse.
- Separate state and configuration per environment using workspaces or backends.
- Use remote backends (e.g., Azure Storage, S3) with locking.
- Validate with `terraform validate`, `pulumi preview`, or `bicep build`.
- Tag all resources with project, owner, and environment metadata.
- Follow the principle of least privilege when assigning IAM roles.
- Store secrets in secure services (Key Vault, SSM, Secrets Manager)—never in code.

### 🚫 Patterns to Avoid

- Don’t commit `.tfstate`, `.bicepParams`, or `.env` files.
- Avoid hardcoding cloud credentials—use environment-based auth.
- Don’t repeat configuration across environments—use shared modules or stacks.
- Avoid overly large monolithic files—modularize.
- Don’t use dynamic resource names unless necessary—prefer predictable naming conventions.
- Avoid using `count` or `for_each` for complex logic that obscures intent.

## 🧪 Testing Guidelines

- Use `terraform plan` or `pulumi preview` to validate changes before applying.
- Use `tflint`, `checkov`, or `terraform validate` for static checks.
- Run `terraform validate` or `bicep build` in CI to catch syntax and structure issues.
- Test module input/output behavior in isolated test environments.
- Optionally use integration testing with `terratest` or `kitchen-terraform`.

## 🧩 Example Prompts

- `Copilot, create a Terraform module for an Azure Function App with a storage account and app settings.`
- `Copilot, define input variables and outputs for a reusable AWS VPC module.`
- `Copilot, generate a Pulumi component that provisions a GCP Cloud Run service.`
- `Copilot, write a GitHub Actions workflow that runs terraform fmt, validate, plan, and apply on PR merge.`
- `Copilot, implement a backend.tf configuration using Azure Storage Account for state management.`

## 🔁 Iteration & Review

- Copilot output should be validated with preview/plan tools before merging.
- Use inline comments to explain intent when generating complex infrastructure.
- Refactor large resources or repeated blocks into modules.
- Review all security-sensitive resources (e.g., IAM, firewall rules) manually.

## 📚 References

- [Terraform Language Docs](https://developer.hashicorp.com/terraform/language)
- [Pulumi Documentation](https://www.pulumi.com/docs/)
- [Bicep Language Reference](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/)
- [Terraform Registry](https://registry.terraform.io/)
- [Checkov (IaC Security Scanner)](https://www.checkov.io/)
- [TFLint](https://github.com/terraform-linters/tflint)
- [Terratest](https://terratest.gruntwork.io/)
- [GitHub Actions for Terraform](https://github.com/hashicorp/setup-terraform)
