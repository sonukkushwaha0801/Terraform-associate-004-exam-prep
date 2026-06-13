# Objective: 5a - Explain How Terraform Sources Modules

## Definition

Terraform modules can be stored in multiple locations.

When Terraform encounters a module block, it downloads the module from the specified source and makes it available for use.

Terraform supports several module source types:

- Local Paths
- Terraform Registry
- Git Repositories
- HTTP URLs
- Private Registries

Understanding module sources is a frequently tested Terraform Associate (004) exam objective.

---

## Core Concepts

### What Is a Module Source?

A module source tells Terraform where to locate and download a module.

Example:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

Terraform reads:

```text
./modules/vpc
```

and loads the module.

---

## Module Source Syntax

General Syntax:

```hcl
module "<NAME>" {
  source = "<SOURCE>"
}
```

Example:

```hcl
module "network" {
  source = "./modules/network"
}
```

---

## How It Works

Module Workflow:

```text
terraform init
       │
       ▼
Read Module Block
       │
       ▼
Locate Source
       │
       ▼
Download Module
       │
       ▼
Store in .terraform
       │
       ▼
Use Module
```

---

# Local Modules

## Definition

Modules stored locally on the filesystem.

Example Structure:

```text
project/
│
├── main.tf
│
└── modules/
     └── vpc/
         ├── main.tf
         ├── variables.tf
         └── outputs.tf
```

---

## Source Example

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

---

## Characteristics

✅ Simple

✅ Fast

✅ Common for Development

❌ Difficult to share across teams

---

## Relative Paths

Current Directory:

```hcl
source = "./modules/vpc"
```

Parent Directory:

```hcl
source = "../modules/vpc"
```

---

# Terraform Registry Modules

## Definition

Modules hosted in the Terraform Registry.

Registry:

```text
registry.terraform.io
```

Contains:

- Official Modules
- Verified Modules
- Community Modules

---

## Source Syntax

```hcl
module "vpc" {
  source = "terraform-aws-modules/vpc/aws"
}
```

---

## Format

```text
<NAMESPACE>/<MODULE>/<PROVIDER>
```

Example:

```text
terraform-aws-modules/vpc/aws
```

Breakdown:

```text
Namespace → terraform-aws-modules
Module    → vpc
Provider  → aws
```

---

## Benefits

✅ Reusable

✅ Community Maintained

✅ Versioned

✅ Production Ready

---

## Real Example

```hcl
module "vpc" {
  source = "terraform-aws-modules/vpc/aws"
}
```

Terraform downloads the module automatically.

---

# Git Repository Modules

## Definition

Modules stored in Git repositories.

Supported:

- GitHub
- GitLab
- Bitbucket
- Self-Hosted Git

---

## Source Syntax

```hcl
module "vpc" {
  source = "git::https://github.com/company/vpc-module.git"
}
```

---

## Specific Branch

```hcl
module "vpc" {
  source = "git::https://github.com/company/vpc-module.git?ref=main"
}
```

---

## Specific Tag

```hcl
module "vpc" {
  source = "git::https://github.com/company/vpc-module.git?ref=v1.0.0"
}
```

---

## Specific Commit

```hcl
module "vpc" {
  source = "git::https://github.com/company/vpc-module.git?ref=a1b2c3d"
}
```

---

## Benefits

✅ Version Control

✅ Team Collaboration

✅ CI/CD Friendly

---

# HTTP URL Modules

## Definition

Modules downloaded from URLs.

Example:

```hcl
module "vpc" {
  source = "https://example.com/modules/vpc.zip"
}
```

Terraform downloads the archive.

---

## Characteristics

✅ Remote Distribution

❌ Less Common

❌ Less Flexible Than Git

---

# Private Registry Modules

## Definition

Modules hosted in private Terraform registries.

Common in enterprises.

Examples:

```text
Terraform Enterprise
HCP Terraform
Private Registry
```

---

## Benefits

✅ Internal Standards

✅ Access Control

✅ Version Management

✅ Central Governance

---

# Module Installation

Modules are downloaded during:

```bash
terraform init
```

Example:

```bash
terraform init
```

Downloads:

- Providers
- Modules

---

## Download Location

Terraform stores downloaded modules inside:

```text
.terraform/
```

Example:

```text
.terraform/modules/
```

---

# Terraform Perspective

Example:

```hcl
module "network" {
  source = "./modules/network"
}
```

Terraform:

```text
Read Module
      │
      ▼
Download Module
      │
      ▼
Evaluate Configuration
```

---

# Real-World Example

Enterprise Structure:

```text
root-module/
│
├── main.tf
│
└── modules/
     ├── vpc/
     ├── eks/
     └── security/
```

Root Module:

```hcl
module "vpc" {
  source = "./modules/vpc"
}

module "eks" {
  source = "./modules/eks"
}
```

---

# Production Use Case

Most organizations use:

```text
Git Repositories
```

or

```text
Private Registries
```

for module distribution.

Benefits:

- Version Control
- Reusability
- Governance
- Standardization

---

# Important Exam Points

- Modules are referenced using source.
- Modules are downloaded during terraform init.
- Registry format:

```text
namespace/module/provider
```

- Git modules use:

```text
git::
```

prefix.
- Modules can be sourced locally or remotely.
- Downloaded modules are stored in:

```text
.terraform/modules
```

- Private registries are common in enterprises.

---

# Common Exam Traps

### Trap 1

Question:

When are modules downloaded?

Correct:

```bash
terraform init
```

---

### Trap 2

Question:

Where are downloaded modules stored?

Correct:

```text
.terraform/modules
```

---

### Trap 3

Question:

What attribute defines a module location?

Correct:

```hcl
source
```

---

### Trap 4

Question:

What is the registry module format?

Correct:

```text
namespace/module/provider
```

---

### Trap 5

Question:

What prefix is used for Git module sources?

Correct:

```text
git::
```

---

## Interview Questions

### What is a Terraform module source?

A location from which Terraform downloads a module.

### What command downloads modules?

```bash
terraform init
```

### What are common module source types?

- Local
- Registry
- Git
- HTTP
- Private Registry

### Where are downloaded modules stored?

```text
.terraform/modules
```

### Which source type is most common in enterprises?

Git repositories and private registries.

---

## Practice Questions

### Question 1

Which argument specifies the location of a Terraform module?

A. provider

B. source

C. module

D. backend

**Answer:** B

---

### Question 2

When does Terraform download modules?

A. terraform plan

B. terraform apply

C. terraform init

D. terraform validate

**Answer:** C

---

### Question 3

Which source format is used for Terraform Registry modules?

A.

```text
provider/module/version
```

B.

```text
namespace/module/provider
```

C.

```text
module/provider/source
```

D.

```text
provider/namespace/module
```

**Answer:** B

---

### Question 4

Which prefix is used for Git-based module sources?

A.

```text
github::
```

B.

```text
registry::
```

C.

```text
git::
```

D.

```text
module::
```

**Answer:** C

---

### Question 5

Where are downloaded modules stored locally?

A.

```text
terraform.tfstate
```

B.

```text
.terraform/modules
```

C.

```text
modules/
```

D.

```text
providers/
```

**Answer:** B

---

## Related Objectives

- 5b Describe Variable Scope Within Modules
- 5c Use Modules in Configuration
- 5d Manage Module Versions
- 3b Initialize a Terraform Working Directory

---

## Key Takeaways

- Modules are downloaded from sources.
- Common sources are local, registry, Git, HTTP, and private registries.
- Modules are downloaded during terraform init.
- Downloaded modules are stored in .terraform/modules.
- Registry modules use namespace/module/provider format.
- Git modules use the git:: prefix.
- Enterprises commonly use Git repositories and private registries for module distribution.
