# Terraform Associate (004) Exam Day Cheat Sheet

> Last-Minute Revision Guide
>
> Purpose:
>
> * Rapid Revision
> * Exam-Day Refresh
> * Final 30-Minute Review
>
> Focus:
>
> * High-Frequency Concepts
> * Common Exam Topics
> * Terraform Commands
> * Exam Traps

---

# 1. Terraform Workflow (Must Memorize)

```text
Write Configuration
        ↓
terraform init
        ↓
terraform fmt
        ↓
terraform validate
        ↓
terraform plan
        ↓
terraform apply
        ↓
terraform destroy
```

---

# 2. High-Frequency Commands

## Initialize

```bash
terraform init
```

Downloads:

* Providers
* Modules
* Backend Configuration

---

## Format

```bash
terraform fmt
```

Formats Terraform code.

---

## Validate

```bash
terraform validate
```

Checks syntax and configuration validity.

---

## Plan

```bash
terraform plan
```

Shows proposed changes.

Does NOT modify infrastructure.

---

## Apply

```bash
terraform apply
```

Creates, updates, or destroys infrastructure.

---

## Destroy

```bash
terraform destroy
```

Removes Terraform-managed infrastructure.

---

## Show

```bash
terraform show
```

Displays state or plan details.

---

## Output

```bash
terraform output
```

Displays output values.

---

## State Commands

```bash
terraform state list

terraform state show

terraform state mv

terraform state rm
```

---

## Import

```bash
terraform import
```

Brings existing infrastructure under Terraform management.

---

# 3. Resource vs Data

## Resource Block

Used to:

```text
Create
Modify
Delete
```

Infrastructure.

Example:

```hcl
resource "aws_instance" "web" {
}
```

---

## Data Block

Used to:

```text
Read Existing Infrastructure
```

Example:

```hcl
data "aws_ami" "ubuntu" {
}
```

---

## Exam Trap

```text
Resource
≠
Data Source
```

Data sources do NOT create resources.

---

# 4. Variables & Outputs

## Variable

Input to Terraform.

Example:

```hcl
variable "instance_type" {
  type = string
}
```

---

## Output

Returns information after deployment.

Example:

```hcl
output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

---

## Variable Types

```text
string

number

bool

list

map

object

tuple

set
```

---

# 5. Dependencies

## Implicit Dependency

Terraform detects automatically.

Example:

```hcl
subnet_id = aws_subnet.public.id
```

---

## Explicit Dependency

```hcl
depends_on = [
  aws_vpc.main
]
```

---

## Exam Trap

Use:

```text
depends_on
```

only when Terraform cannot infer dependency.

---

# 6. Functions To Remember

## lookup()

```hcl
lookup(map, key, default)
```

---

## length()

```hcl
length(list)
```

---

## merge()

```hcl
merge(map1, map2)
```

---

## concat()

```hcl
concat(list1, list2)
```

---

## upper()

```hcl
upper("terraform")
```

---

## lower()

```hcl
lower("Terraform")
```

---

## tostring()

```hcl
tostring(value)
```

---

## tonumber()

```hcl
tonumber(value)
```

---

# 7. State Facts

## State File

```text
terraform.tfstate
```

Stores:

* Resource Metadata
* Resource IDs
* Mappings

---

## Purpose

Maps:

```text
Configuration
        ↔
Real Infrastructure
```

---

## State Commands

```bash
terraform state list

terraform state show

terraform state mv

terraform state rm
```

---

## Exam Trap

Terraform State:

```text
Required
```

for Terraform operation.

---

# 8. Backend Facts

## Local Backend

Default backend.

```text
terraform.tfstate
```

stored locally.

---

## Remote Backend Benefits

```text
Collaboration

Versioning

Recovery

Centralization
```

---

## Common Backends

```text
local

s3

azurerm

gcs

remote
```

---

## State Locking

Prevents:

```text
Concurrent State Modification
```

---

# 9. Import Facts

## Purpose

Manage existing infrastructure.

---

## Command

```bash
terraform import
```

---

## Workflow

```text
Write Configuration
       ↓
Import Resource
       ↓
terraform plan
       ↓
Validate
```

---

## Exam Trap

Import:

```text
Updates State
```

It does NOT generate Terraform code.

---

# 10. Drift Facts

## Definition

Infrastructure differs from Terraform configuration/state.

---

## Detection

```bash
terraform plan
```

---

## Resolution

```bash
terraform apply
```

---

## Common Causes

```text
Manual Console Changes

CLI Changes

Automation Outside Terraform
```

---

# 11. Sensitive Data Facts

## Sensitive Variable

```hcl
sensitive = true
```

---

## Purpose

Hides value from CLI output.

---

## Exam Trap

```text
Sensitive
≠
Encrypted
```

Sensitive values may still exist in state.

---

## Recommended Secret Stores

```text
HashiCorp Vault

AWS Secrets Manager

Azure Key Vault

Google Secret Manager
```

---

# 12. HCP Terraform Facts

## Features

```text
Remote State

Remote Execution

Collaboration

Governance

Private Registry

Run History
```

---

## Key Components

### Organization

Top-level container.

### Project

Groups related workspaces.

### Workspace

Execution environment.

---

## Governance Features

```text
Sentinel

Run Tasks

Policy Enforcement
```

---

# 13. Top Exam Traps

## Trap 1

```text
terraform plan
```

does NOT change infrastructure.

---

## Trap 2

```text
terraform validate
```

does NOT create infrastructure.

---

## Trap 3

```text
terraform fmt
```

does NOT validate infrastructure.

---

## Trap 4

```text
Sensitive
≠
Encrypted
```

---

## Trap 5

```text
Data Source
≠
Resource
```

---

## Trap 6

```text
Import
≠
Generate Configuration
```

---

## Trap 7

```text
Workspace
≠
Environment
```

---

## Trap 8

Terraform State:

```text
Required
```

for infrastructure management.

---

## Trap 9

Remote State:

```text
Does NOT Automatically Mean Locking
```

Backend dependent.

---

## Trap 10

```text
terraform destroy
```

only affects managed resources.

---

# 14. 50 Rapid-Fire Revision Facts

1. Terraform is declarative.
2. Terraform uses providers.
3. Providers manage APIs.
4. Resources create infrastructure.
5. Data sources read infrastructure.
6. State tracks resources.
7. Plan previews changes.
8. Apply executes changes.
9. Destroy removes resources.
10. Init installs providers.
11. Validate checks syntax.
12. Fmt formats code.
13. Outputs expose values.
14. Variables accept input.
15. Modules promote reuse.
16. Modules can be versioned.
17. Terraform Registry hosts modules.
18. Providers can be versioned.
19. State should be remote in teams.
20. State locking prevents corruption.
21. Drift occurs outside Terraform.
22. Plan detects drift.
23. Apply reconciles drift.
24. Sensitive does not mean encrypted.
25. Vault manages secrets.
26. HCP Terraform supports collaboration.
27. Sentinel provides policy enforcement.
28. Run Tasks support integrations.
29. Workspaces isolate state.
30. Dependencies control ordering.
31. Implicit dependencies are preferred.
32. depends_on creates explicit dependencies.
33. Terraform supports multi-cloud.
34. Terraform is service agnostic.
35. Local backend is default.
36. S3 is a common backend.
37. Import updates state.
38. Import does not generate code.
39. Providers are plugins.
40. Resources belong to providers.
41. Terraform follows desired state.
42. Configuration is stored as code.
43. Git is commonly used with Terraform.
44. Remote execution is available in HCP Terraform.
45. Projects organize workspaces.
46. Private registries store modules.
47. State may contain sensitive data.
48. Terraform compares desired vs actual state.
49. Review plans before apply.
50. Read questions carefully.

---

# 15. Last 5-Minute Checklist

## Must Know

* [ ] Terraform Workflow
* [ ] Resource vs Data
* [ ] Variables & Outputs
* [ ] State Concepts
* [ ] Backends
* [ ] State Locking
* [ ] Import Workflow
* [ ] Drift Detection
* [ ] Sensitive Data
* [ ] HCP Terraform
* [ ] Sentinel
* [ ] Common Commands

---

## Commands To Memorize

```bash
terraform init

terraform fmt

terraform validate

terraform plan

terraform apply

terraform destroy

terraform output

terraform show

terraform import

terraform state list

terraform state show
```

---

## Final Reminder

Read every question carefully.

Most Terraform Associate mistakes come from confusing:

```text
Resource vs Data

Plan vs Apply

Sensitive vs Encrypted

Import vs Configuration

Workspace vs Environment
```

Those distinctions appear repeatedly throughout the exam.

**Good luck.**
