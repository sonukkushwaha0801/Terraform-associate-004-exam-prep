# Domain 5 Revision Sheet

## Terraform Modules

### Objectives Covered

- 5a Module Sources
- 5b Variable Scope Within Modules
- 5c Use Modules in Configuration
- 5d Manage Module Versions

---

# What Is A Module?

A module is a reusable collection of Terraform configuration files.

Purpose:

- Reusability
- Standardization
- Reduced Duplication
- Easier Maintenance

---

## Exam Memory Trick

```text
Module = Reusable Terraform Code
```

---

# Root Module

## Definition

The directory where Terraform commands are executed.

Example:

```bash
terraform init
terraform plan
terraform apply
```

Executed from:

```text
project/
```

This becomes the Root Module.

---

# Child Module

## Definition

A module called by another module.

Example:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

The VPC module is a Child Module.

---

# Root vs Child Module

| Root Module             | Child Module             |
| ----------------------- | ------------------------ |
| Execution Location      | Called by Another Module |
| Runs Terraform Commands | Provides Reusable Logic  |
| Top-Level Configuration | Nested Configuration     |

---

# Module Block

## Syntax

```hcl
module "vpc" {

  source = "./modules/vpc"

}
```

---

## Required Argument

```hcl
source
```

Every module requires:

```hcl
source
```

---

# Module Sources

Terraform supports multiple module source types.

---

## Local Module

```hcl
source = "./modules/vpc"
```

Most common for development.

---

## Registry Module

```hcl
source = "terraform-aws-modules/vpc/aws"
```

Format:

```text
namespace/module/provider
```

---

## Git Module

```hcl
source = "git::https://github.com/company/vpc-module.git"
```

---

## HTTP Module

```hcl
source = "https://example.com/module.zip"
```

---

## Private Registry

Examples:

```text
HCP Terraform
Terraform Enterprise
Private Registry
```

---

# Module Download Process

Modules are downloaded during:

```bash
terraform init
```

---

## Download Location

```text
.terraform/modules
```

---

# Module Inputs

Modules receive values through:

```hcl
variable
```

---

## Example

Child Module:

```hcl
variable "cidr_block" {
  type = string
}
```

Root Module:

```hcl
module "vpc" {

  source = "./modules/vpc"

  cidr_block = "10.0.0.0/16"

}
```

---

## Flow

```text
Root Module
      │
      ▼
Variable
      │
      ▼
Child Module
```

---

# Module Outputs

Modules expose values through:

```hcl
output
```

---

## Example

Child Module:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---

## Consuming Output

Root Module:

```hcl
module.vpc.vpc_id
```

---

## Output Syntax

```hcl
module.<module_name>.<output_name>
```

Example:

```hcl
module.network.subnet_id
```

---

# Module Communication

```text
Root Module
      │
      ▼
Input Variables
      │
      ▼
Child Module
      │
      ▼
Outputs
      │
      ▼
Root Module
```

---

# Variable Scope Rules

## Rule 1

Variables are local to their module.

---

## Rule 2

Modules do NOT automatically share variables.

---

## Rule 3

Values must be passed explicitly.

---

## Exam Trap

Question:

Can a child module automatically access root module variables?

Answer:

```text
NO
```

---

# Module Reuse

One module can be instantiated multiple times.

Example:

```hcl
module "dev_vpc" {
  source = "./modules/vpc"
}
```

```hcl
module "prod_vpc" {
  source = "./modules/vpc"
}
```

Same module.

Different deployments.

---

# Module Versioning

Registry modules support:

```hcl
version
```

argument.

---

## Example

```hcl
module "vpc" {

  source  = "terraform-aws-modules/vpc/aws"

  version = "5.0.0"

}
```

---

# Semantic Versioning

Format:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
5.2.1
```

---

## MAJOR

```text
Breaking Changes
```

Example:

```text
6.0.0
```

---

## MINOR

```text
New Features
```

Example:

```text
5.3.0
```

---

## PATCH

```text
Bug Fixes
```

Example:

```text
5.3.2
```

---

# Version Constraints

## Exact Version

```hcl
version = "5.0.0"
```

---

## Greater Than

```hcl
version = ">= 5.0.0"
```

---

## Less Than

```hcl
version = "< 6.0.0"
```

---

## Range

```hcl
version = ">= 5.0.0, < 6.0.0"
```

---

# Pessimistic Constraint (~>)

## Most Important Exam Topic

```hcl
version = "~> 5.0"
```

Meaning:

```text
>= 5.0.0
< 6.0.0
```

Allowed:

```text
5.1.0
5.8.0
5.9.2
```

Blocked:

```text
6.0.0
```

---

## Example 2

```hcl
version = "~> 5.2.0"
```

Meaning:

```text
>= 5.2.0
< 5.3.0
```

Allowed:

```text
5.2.1
5.2.9
```

Blocked:

```text
5.3.0
```

---

# Module Upgrades

Terraform does NOT automatically upgrade modules.

---

## Upgrade Command

```bash
terraform init -upgrade
```

---

## Purpose

Upgrades:

- Modules
- Providers

---

# Git Module Versioning

Git modules commonly use:

```text
?ref=
```

---

## Tag

```hcl
?ref=v1.0.0
```

---

## Branch

```hcl
?ref=main
```

---

## Commit

```hcl
?ref=a1b2c3d
```

---

# Top 20 Exam Facts

### Modules improve reusability.

### Root module executes Terraform commands.

### Child module is called by another module.

### source is required.

### Modules download during terraform init.

### Modules stored in .terraform/modules.

### Local module:

```hcl
./modules/vpc
```

### Registry format:

```text
namespace/module/provider
```

### Git modules use:

```text
git::
```

### Modules receive inputs through variables.

### Modules expose outputs through outputs.

### Output syntax:

```hcl
module.vpc.vpc_id
```

### Variables are not automatically shared.

### Modules communicate using inputs and outputs.

### Semantic Versioning:

```text
MAJOR.MINOR.PATCH
```

### MAJOR = Breaking Changes.

### MINOR = Features.

### PATCH = Fixes.

### ~> = Pessimistic Constraint.

### terraform init -upgrade upgrades modules.

---

# Most Common Exam Traps

## Trap 1

Root Module

```text
Directory where Terraform commands are executed.
```

---

## Trap 2

Child Module

```text
Module called by another module.
```

---

## Trap 3

Module Communication

```text
Input  → Variables
Output → Outputs
```

---

## Trap 4

Module Output Syntax

Correct:

```hcl
module.vpc.vpc_id
```

---

## Trap 5

Registry Module Format

Correct:

```text
namespace/module/provider
```

---

## Trap 6

Git Module Prefix

Correct:

```text
git::
```

---

## Trap 7

Downloaded Module Location

Correct:

```text
.terraform/modules
```

---

## Trap 8

Upgrade Command

Correct:

```bash
terraform init -upgrade
```

---

## Trap 9

Pessimistic Constraint

```hcl
~> 5.0
```

means:

```text
>= 5.0.0
< 6.0.0
```

---

## Trap 10

Variable Scope

Modules DO NOT automatically share variables.

---

# 30-Second Exam Revision

Remember:

```text
Module = Reusable Code
```

```text
Root = Execute Commands
```

```text
Child = Called Module
```

```hcl
source
```

```hcl
variable
```

```hcl
output
```

```hcl
module.vpc.vpc_id
```

```text
namespace/module/provider
```

```text
git::
```

```text
MAJOR.MINOR.PATCH
```

```text
~>
```

```bash
terraform init
```

```bash
terraform init -upgrade
```

---

# Domain Completion Checklist

- [ ] Completed 5a Module Sources
- [ ] Completed 5b Variable Scope
- [ ] Completed 5c Use Modules
- [ ] Completed 5d Manage Module Versions
- [ ] Completed Practice Questions
- [ ] Scored 27+/30
- [ ] Reviewed All Mistakes
- [ ] Ready For Domain 6 State Management
