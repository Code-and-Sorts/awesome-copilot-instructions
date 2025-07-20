# GitHub Copilot Instructions

These instructions define how GitHub Copilot should assist with this Terraform + Atmos project. The goal is to ensure consistent, modular, and environment-aware infrastructure generation aligned with our team's conventions and deployment workflows.

## 🧠 Context

- **Project Type**: Cloud Infrastructure Provisioning / Platform Engineering
- **Language / Tool**: Terraform with Atmos (YAML + HCL)
- **Cloud Providers**: AWS / Azure / GCP / Kubernetes
- **Architecture**: Modular Components / Multi-Environment / GitOps / CI-Driven

## 🔧 General Guidelines

- Follow idiomatic Atmos conventions using the `components/` and `stacks/` folders.
- Use YAML stack configurations to compose environments from reusable components.
- Prefer variables and inheritance through Atmos hierarchy rather than hardcoding.
- Structure `terraform` components under `components/terraform/`, using separate modules for reusable infrastructure.
- Ensure all components are tested independently and parameterized via `inputs`.

## 📁 File Structure

Use this structure as a guide when creating or updating files:

```text
components/
  terraform/
    vpc/
    eks/
    app/
    dns/
  atmos.yaml

stacks/
  orgs/
    acme/
      tenant1/
        dev/
          us-west-2/
            vpc.yaml
            eks.yaml
            app.yaml
        staging/
        prod/

  globals/
    globals.yaml

vendor/
  <imported components from git registries>

terraform/
  <provider.tf, backend.tf, shared locals>
```

## 🧶 Patterns

### ✅ Patterns to Follow

- Define inputs in `inputs:` blocks inside stack YAML files.
- Use `vars`, `env`, and `backend` blocks to configure state and secrets.
- Break infrastructure into composable components (e.g., `vpc`, `eks`, `alb`).
- Inherit shared settings via `import:` or `globals:` in stack files.
- Use naming conventions for stacks like `<tenant>/<stage>/<region>`.
- Validate changes using `atmos terraform plan <component> -s <stack>` before apply.
- Use Atmos CLI (`atmos terraform apply`, `atmos describe`, etc.) for all workflows.

### 🚫 Patterns to Avoid

- Don’t hardcode configuration—define everything via stack inputs or shared globals.
- Avoid modifying vendor components directly—extend or wrap instead.
- Don’t run `terraform` commands directly—always use `atmos terraform`.
- Avoid deeply nested inputs in YAML—flatten and document clearly.
- Don’t create large, monolithic components—break into logical units.
- Avoid committing `.terraform` directories or local state.

## 🧪 Testing Guidelines

- Validate YAML syntax with CI linters (`yamllint`).
- Run `atmos terraform plan` on all changed components in PRs.
- Use `tflint`, `checkov`, or `tfsec` on individual components.
- Use `atmos validate stacks/` to check stack references and structure.
- Create preview environments using short-lived stacks (e.g. `pr-123/preview`).

## 🧩 Example Prompts

- `Copilot, generate an Atmos stack YAML that deploys the vpc, eks, and app components to staging/us-west-2.`
- `Copilot, create a Terraform component for an S3 bucket with versioning and encryption enabled.`
- `Copilot, write a globals.yaml that includes standard tags and default region.`
- `Copilot, define a backend configuration block in the app component using s3 and dynamodb for state.`
- `Copilot, create a GitHub Actions job that runs atmos terraform plan on all changed stacks.`

## 🔁 Iteration & Review

- Review all stack and component changes via `atmos terraform plan`.
- Keep stack files small and focused; split by component when needed.
- Refactor stack duplication into `import:`ed globals or partials.
- Validate all inputs are documented, typed, and overridable.

## 📚 References

- [Atmos Documentation](https://atmos.tools/cli)
- [Terraform Language Docs](https://developer.hashicorp.com/terraform/language)
- [Terraform Best Practices](https://atmos.tools/best-practices/terraform/)
- [Atmos Stack Cheatsheet](https://atmos.tools/cheatsheets/stacks)
- [TFLint](https://github.com/terraform-linters/tflint)
- [Checkov](https://www.checkov.io/)
- [Yamllint](https://yamllint.readthedocs.io/)
- [Terraform GitHub Actions](https://github.com/hashicorp/setup-terraform)
