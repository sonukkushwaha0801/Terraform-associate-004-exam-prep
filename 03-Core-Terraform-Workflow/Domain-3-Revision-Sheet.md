# Domain 3 Revision Sheet

## Core Terraform Workflow

### Objectives Covered

- 3a - Describe the Terraform Workflow
- 3b - Initialize a Terraform Working Directory
- 3c - Validate a Terraform Configuration
- 3d - Generate and Review an Execution Plan
- 3e - Apply Changes to Infrastructure with Terraform
- 3f - Destroy Terraform-Managed Infrastructure
- 3g - Apply Formatting and Style Adjustments

---

# Terraform Workflow Overview

## Standard Workflow

```text
Write Configuration
        ↓
terraform init
        ↓
terraform validate
        ↓
terraform plan
        ↓
terraform apply
```

Infrastructure Removal:

```text
terraform destroy
```

---

# terraform init

## Purpose

Initialize Terraform working directory.

## Responsibilities

- Download Providers
- Download Modules
- Configure Backend
- Create .terraform Directory

## Commands

```bash
terraform init
```

Upgrade Providers:

```bash
terraform init -upgrade
```

Reconfigure Backend:

```bash
terraform init -reconfigure
```

## Important Facts

✅ First Terraform command

✅ Downloads providers

❌ Does NOT create infrastructure

---

# terraform validate

## Purpose

Validate configuration correctness.

## Checks

- Syntax
- References
- Internal Consistency

## Command

```bash
terraform validate
```

## Important Facts

✅ Checks configuration

❌ Creates resources

❌ Generates plans

❌ Formats code

---

# terraform plan

## Purpose

Preview infrastructure changes.

## Compares

```text
Current State
      vs
Desired State
```

## Command

```bash
terraform plan
```

## Save Plan

```bash
terraform plan -out=tfplan
```

## Important Facts

✅ Generates execution plan

✅ Safe to run

❌ Does NOT modify infrastructure

---

# Plan Symbols

## Create

```text
+
```

Example:

```text
+ aws_instance.web
```

---

## Modify

```text
~
```

Example:

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

---

## Destroy

```text
-
```

Example:

```text
- aws_instance.web
```

---

## Replace

```text
-/+
```

Meaning:

```text
Destroy and Recreate Resource
```

---

# terraform apply

## Purpose

Execute infrastructure changes.

## Command

```bash
terraform apply
```

## Auto Approve

```bash
terraform apply -auto-approve
```

## Apply Saved Plan

```bash
terraform apply tfplan
```

## Important Facts

✅ Creates resources

✅ Updates resources

✅ Destroys resources when required

✅ Updates state

---

# terraform destroy

## Purpose

Remove Terraform-managed infrastructure.

## Command

```bash
terraform destroy
```

## Auto Approve

```bash
terraform destroy -auto-approve
```

## Preview Destruction

```bash
terraform plan -destroy
```

## Important Facts

✅ Removes resources

✅ Updates state

❌ Does NOT delete configuration files

---

# terraform fmt

## Purpose

Format Terraform code.

## Command

```bash
terraform fmt
```

## Check Only

```bash
terraform fmt -check
```

## Recursive Formatting

```bash
terraform fmt -recursive
```

## Important Facts

✅ Formats code

❌ Validates configuration

❌ Creates resources

❌ Updates state

---

# Most Important Files

## State File

```text
terraform.tfstate
```

Stores:

- Managed Resources
- Resource Metadata
- Infrastructure State

---

## Lock File

```text
.terraform.lock.hcl
```

Stores:

- Provider Version Selections

---

## Terraform Directory

```text
.terraform/
```

Stores:

- Downloaded Providers
- Downloaded Modules
- Initialization Metadata

---

# Command Comparison

| Command            | Purpose                |
| ------------------ | ---------------------- |
| terraform init     | Initialize Project     |
| terraform validate | Validate Configuration |
| terraform plan     | Preview Changes        |
| terraform apply    | Execute Changes        |
| terraform destroy  | Remove Infrastructure  |
| terraform fmt      | Format Code            |

---

# Common Exam Traps

## Trap 1

Which command creates infrastructure?

✅ terraform apply

❌ terraform plan

---

## Trap 2

Which command downloads providers?

✅ terraform init

❌ terraform apply

---

## Trap 3

Which command validates configuration?

✅ terraform validate

❌ terraform fmt

---

## Trap 4

Which command formats code?

✅ terraform fmt

❌ terraform validate

---

## Trap 5

Which command previews changes?

✅ terraform plan

❌ terraform apply

---

## Trap 6

Which command removes infrastructure?

✅ terraform destroy

❌ terraform apply

---

## Trap 7

What updates terraform.tfstate?

✅ terraform apply

✅ terraform destroy

---

## Trap 8

Can terraform plan modify infrastructure?

❌ No

---

## Trap 9

Can terraform validate contact cloud APIs?

❌ No

---

## Trap 10

Can terraform fmt validate configuration?

❌ No

---

# High-Probability Exam Questions

### Which command should normally run first?

```bash
terraform init
```

---

### Which command previews changes?

```bash
terraform plan
```

---

### Which command applies changes?

```bash
terraform apply
```

---

### Which command destroys resources?

```bash
terraform destroy
```

---

### Which command validates configuration?

```bash
terraform validate
```

---

### Which command formats code?

```bash
terraform fmt
```

---

### What does + mean?

Create Resource

---

### What does ~ mean?

Modify Resource

---

### What does - mean?

Destroy Resource

---

### What does -/+ mean?

Replace Resource

---

### How do you save a plan?

```bash
terraform plan -out=tfplan
```

---

### How do you apply a saved plan?

```bash
terraform apply tfplan
```

---

# 60-Second Final Revision

Remember:

- init = Initialize
- validate = Check Configuration
- plan = Preview Changes
- apply = Execute Changes
- destroy = Remove Infrastructure
- fmt = Format Code

Plan Symbols:

```text
+    Create
~    Modify
-    Destroy
-/+  Replace
```

Workflow:

```text
Init
 ↓
Validate
 ↓
Plan
 ↓
Apply
```

State Updates:

```text
apply   → Updates State
destroy → Updates State
```

Most Tested Commands:

```bash
terraform init
terraform validate
terraform plan
terraform apply
terraform destroy
terraform fmt
```

---

## Domain Completion Checklist

- [ ] Completed Domain 3 Theory
- [ ] Completed Practice Questions
- [ ] Reviewed Answer Explanations
- [ ] Memorized Workflow Order
- [ ] Memorized Plan Symbols
- [ ] Practiced Core Commands
- [ ] Ready for Domain 4
