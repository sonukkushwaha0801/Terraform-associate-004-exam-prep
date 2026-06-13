# Objective: 5c - Use Modules in Configuration

## Definition

Terraform modules allow infrastructure code to be packaged, reused, and shared.

Instead of duplicating resources across multiple configurations, a module can be written once and reused many times.

Modules are a core Terraform feature and are heavily used in production environments.

This objective focuses on:

- Module Blocks
- Calling Modules
- Passing Inputs
- Consuming Outputs
- Root and Child Module Communication

---

## Core Concepts

### What Is a Module?

A module is a collection of Terraform configuration files stored together.

Example:

```text
modules/
└── vpc/
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```

The module encapsulates infrastructure logic.

---

## Root Module

The configuration where Terraform commands are executed.

Example:

```text
project/
│
├── main.tf
├── variables.tf
└── outputs.tf
```

Terraform commands:

```bash
terraform init
terraform plan
terraform apply
```

are executed here.

---

## Child Module

Any module called from another module.

Example:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

The VPC module becomes a child module.

---

# Module Block Syntax

## General Syntax

```hcl
module "<MODULE_NAME>" {
  source = "<MODULE_SOURCE>"
}
```

Example:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

Terraform downloads and evaluates the module.

---

# Calling a Module

Example:

```hcl
module "network" {
  source = "./modules/network"
}
```

Terraform:

```text
Read Module Block
       ↓
Locate Module
       ↓
Load Module
       ↓
Process Resources
```

---

# Passing Variables to Modules

## Child Module

variables.tf

```hcl
variable "cidr_block" {
  type = string
}
```

main.tf

```hcl
resource "aws_vpc" "main" {
  cidr_block = var.cidr_block
}
```

---

## Root Module

```hcl
module "vpc" {
  source = "./modules/vpc"

  cidr_block = "10.0.0.0/16"
}
```

Terraform passes:

```text
10.0.0.0/16
```

into the module.

---

# Module Inputs

Inputs are values passed into a module.

Example:

```hcl
module "network" {
  source = "./modules/network"

  cidr_block = "10.0.0.0/16"
  environment = "prod"
}
```

Inputs:

```text
cidr_block
environment
```

---

# Using Variables Inside Modules

Child Module:

```hcl
variable "environment" {
  type = string
}
```

Resource:

```hcl
resource "aws_vpc" "main" {
  tags = {
    Environment = var.environment
  }
}
```

Terraform injects the provided value.

---

# Creating Outputs

Child Module:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

Terraform exposes:

```text
vpc_id
```

to the root module.

---

# Consuming Outputs

Root Module:

```hcl
module.vpc.vpc_id
```

General Syntax:

```hcl
module.<MODULE_NAME>.<OUTPUT_NAME>
```

Example:

```hcl
output "network_id" {
  value = module.vpc.vpc_id
}
```

---

# Complete Example

## Child Module

variables.tf

```hcl
variable "cidr_block" {
  type = string
}
```

main.tf

```hcl
resource "aws_vpc" "main" {
  cidr_block = var.cidr_block
}
```

outputs.tf

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---

## Root Module

main.tf

```hcl
module "vpc" {
  source = "./modules/vpc"

  cidr_block = "10.0.0.0/16"
}
```

outputs.tf

```hcl
output "vpc_id" {
  value = module.vpc.vpc_id
}
```

---

# Module Communication Flow

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
Resources
      │
      ▼
Outputs
      │
      ▼
Root Module
```

---

# Multiple Module Example

```hcl
module "network" {
  source = "./modules/network"
}

module "security" {
  source = "./modules/security"
}

module "compute" {
  source = "./modules/compute"
}
```

Terraform loads all modules.

---

# Reusing Modules

One module can be used multiple times.

Example:

```hcl
module "dev_vpc" {
  source = "./modules/vpc"

  cidr_block = "10.0.0.0/16"
}
```

```hcl
module "prod_vpc" {
  source = "./modules/vpc"

  cidr_block = "172.16.0.0/16"
}
```

Same module.

Different inputs.

Different infrastructure.

---

# How It Works

```text
terraform init
      │
      ▼
Download Module
      │
      ▼
Pass Inputs
      │
      ▼
Create Resources
      │
      ▼
Generate Outputs
      │
      ▼
Return Values
```

---

# Terraform Perspective

Module:

```hcl
module "vpc" {
  source = "./modules/vpc"

  cidr_block = var.cidr_block
}
```

Terraform treats the module like a reusable building block.

---

# Real-World Example

Enterprise Platform:

```text
Network Module
Security Module
EKS Module
Database Module
Monitoring Module
```

Root Module:

```hcl
module "network" {}
module "security" {}
module "eks" {}
module "database" {}
```

Reusable architecture.

---

# Production Use Case

Most organizations maintain:

```text
Shared Module Repository
```

Examples:

- VPC Module
- EKS Module
- IAM Module
- Monitoring Module
- Security Module

Teams consume approved modules instead of writing infrastructure from scratch.

---

# Important Exam Points

- Modules are called using module blocks.
- source defines module location.
- Inputs are passed through variables.
- Outputs expose values.
- Module output syntax:

```hcl
module.<module_name>.<output_name>
```

- Root modules call child modules.
- Modules improve reusability.
- Modules reduce code duplication.

---

# Common Exam Traps

### Trap 1

Question:

How is a module called?

Correct:

```hcl
module
```

block.

---

### Trap 2

Question:

How are values passed into modules?

Correct:

Variables.

---

### Trap 3

Question:

How are values exposed from modules?

Correct:

Outputs.

---

### Trap 4

Question:

How are outputs referenced?

Correct:

```hcl
module.vpc.vpc_id
```

---

### Trap 5

Question:

Can a module be reused multiple times?

Correct:

Yes.

---

# Interview Questions

### What is a Terraform module?

A reusable collection of Terraform configuration files.

### How do you call a module?

Using a module block.

### How are values passed into modules?

Through variables.

### How are values exposed from modules?

Through outputs.

### How are outputs referenced?

```hcl
module.<module_name>.<output_name>
```

### Why use modules?

To improve reusability and reduce duplication.

---

# Practice Questions

### Question 1

Which block is used to call a module?

A. resource

B. module

C. output

D. provider

**Answer:** B

---

### Question 2

Which argument specifies module location?

A. backend

B. provider

C. source

D. output

**Answer:** C

---

### Question 3

How are values passed into modules?

A. Outputs

B. Variables

C. Resources

D. Providers

**Answer:** B

---

### Question 4

How are module outputs referenced?

A.

```hcl
output.vpc.id
```

B.

```hcl
module.vpc.vpc_id
```

C.

```hcl
resource.vpc.id
```

D.

```hcl
module.output.vpc
```

**Answer:** B

---

### Question 5

What is the primary benefit of modules?

A. State Storage

B. Provider Installation

C. Reusability

D. Logging

**Answer:** C

---

## Related Objectives

- 5a Explain How Terraform Sources Modules
- 5b Variable Scope Within Modules
- 5d Manage Module Versions
- 4c Variables and Outputs

---

## Key Takeaways

- Modules are reusable Terraform configurations.
- Modules are called using module blocks.
- source specifies module location.
- Variables provide module inputs.
- Outputs expose module values.
- Module outputs use module.<name>.<output>.
- Modules improve consistency and reduce duplication.
- Module usage is a high-frequency Terraform Associate exam topic.
