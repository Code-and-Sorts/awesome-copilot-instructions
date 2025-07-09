# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Terraform project. The goal is to ensure consistent, secure, and modular infrastructure aligned with our conventions, cloud platform, and Terraform best practices.

## 🧠 Context

- **Project Type**: Cloud Infrastructure Provisioning / Platform Engineering
- **Language / Tool**: Terraform
- **Cloud Providers**: Azure / AWS / GCP / Kubernetes
- **Architecture**: Modular / Multi-environment / Remote State / GitOps

## 🔧 General Guidelines

- Use idiomatic Terraform syntax (`.tf` and `.tfvars` files).
- Follow HCL formatting using `terraform fmt`.
- Always declare variable types and add descriptions.
- Use `locals` for repeated values and naming conventions.
- Use modules to encapsulate reusable infrastructure components.
- Keep each resource file small and single-purpose.
- Prefer resource-specific files (e.g. `network.tf`, `compute.tf`) for clarity.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
terraform/
  modules/
    network/
    compute/
    storage/
  environments/
    dev/
      main.tf
      variables.tf
      backend.tf
    staging/
    prod/
  shared/
    providers.tf
    variables.tf
    locals.tf
    outputs.tf
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Use modules to avoid duplication and enforce standardization.
- Separate environments using workspaces or folders with unique backends.
- Use `terraform.tfvars` for environment-specific values.
- Tag all resources (e.g. `project`, `env`, `owner`).
- Use `terraform output` to expose values for integration.
- Secure sensitive variables with `sensitive = true`.
- Use remote state storage with locking (e.g. S3 + DynamoDB, Azure Storage + Blob Lock).

### 🚫 Patterns to Avoid

- Don’t commit `.terraform/` or `.tfstate` files—use `.gitignore`.
- Avoid hardcoding values—use variables or locals.
- Don’t use `terraform apply` without reviewing `terraform plan`.
- Avoid overly nested or dynamic expressions that reduce readability.
- Don’t write all resources in a single file—split by concern or service.
- Avoid depending on resource ordering—use `depends_on` where required.

## 🧪 Testing Guidelines

- Use `terraform validate` and `terraform plan` to verify correctness.
- Use `tflint`, `terraform-docs`, and `checkov` for static analysis.
- Run `terraform plan` in CI for preview-only validation on PRs.
- Use `terratest` or `kitchen-terraform` for end-to-end infrastructure tests.
- Document expectations and constraints for each module.

## 🧩 Example Prompts

- `Copilot, create a Terraform module that provisions an Azure App Service with a storage account and app settings.`
- `Copilot, define input variables for a VPC module with cidr_block and public_subnets.`
- `Copilot, write an output.tf that returns the public IP of an EC2 instance.`
- `Copilot, generate a backend.tf file using Azure Storage Account with locking enabled.`
- `Copilot, write a GitHub Actions workflow that runs terraform fmt, validate, plan on PR.`

## 🔁 Iteration & Review

- Review all Copilot-generated code with `terraform validate` and `terraform plan`.
- Add inline comments before invoking Copilot to clarify resource behavior.
- Refactor repetitive blocks into modules.
- Perform manual review of IAM, firewall, or public exposure changes.
- Ensure all modules include `README.md`, `variables.tf`, `outputs.tf`.

## 📚 References

- [Terraform Language Docs](https://developer.hashicorp.com/terraform/language)
- [Terraform CLI Command Docs](https://developer.hashicorp.com/terraform/cli/commands)
- [Terraform Registry](https://registry.terraform.io/)
- [Terraform Azure Provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [TFLint](https://github.com/terraform-linters/tflint)
- [Checkov](https://www.checkov.io/)
- [Terratest](https://terratest.gruntwork.io/)
- [GitHub Actions for Terraform](https://github.com/hashicorp/setup-terraform)
