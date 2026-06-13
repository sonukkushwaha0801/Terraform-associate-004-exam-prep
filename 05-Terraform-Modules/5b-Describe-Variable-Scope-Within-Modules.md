# Objective: 5b - Describe Variable Scope Within Modules

## Definition

Terraform modules have isolated variable scopes.

Variables declared inside one module are not automatically available to other modules.

Communication between modules occurs through:

- Input Variables
- Output Values

Understanding variable scope is essential for building reusable and maintainable Terraform modules.

This is a commonly tested Terraform Associate (004) topic.

---

## Core Concepts

Terraform modules behave like independent units.

Each module has:

- Its Own Variables
- Its Own Resources
- Its Own Outputs

Example:

```text
Root Module
     │
     ├── VPC Module
     │
     └── EKS Module
```

Each module has its own scope.

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

Terraform treats this as the:

```text
Root Module
```

---

## Example Structure

```text
project/
│
├── main.tf
├── variables.tf
├── outputs.tf
│
└── modules/
     └── vpc/
```

---

# Child Module

## Definition

A module called from another module.

Example:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

The VPC module becomes a:

```text
Child Module
```

---

# Variable Scope Rules

## Rule 1

Variables belong only to the module where they are declared.

Example:

```hcl
variable "region" {
  type = string
}
```

If declared inside:

```text
modules/vpc
```

it cannot automatically be used outside that module.

---

## Rule 2

Root module variables are not automatically inherited by child modules.

Incorrect Assumption:

```text
Root Variable
      ↓
Automatically Available
      ↓
Child Module
```

❌ False

Terraform does not automatically pass variables.

---

## Rule 3

Variables must be explicitly passed to child modules.

Example:

Root Module:

```hcl
module "vpc" {
  source = "./modules/vpc"

  region = var.region
}
```

Child Module:

```hcl
variable "region" {
  type = string
}
```

Terraform passes:

```text
Root Variable
      ↓
Child Module Variable
```

---

# Module Inputs

## Definition

Variables passed into a module.

Example:

Root Module:

```hcl
module "vpc" {
  source = "./modules/vpc"

  cidr_block = "10.0.0.0/16"
}
```

Child Module:

```hcl
variable "cidr_block" {
  type = string
}
```

---

## Flow

```text
Root Module
      │
      ▼
Input Variable
      │
      ▼
Child Module
```

---

# Module Outputs

## Definition

Outputs expose values from child modules.

Child Module:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---

## Consuming Outputs

Root Module:

```hcl
module.vpc.vpc_id
```

Terraform retrieves:

```text
Child Module Output
       ↓
Root Module
```

---

# Output Scope Rules

Outputs belong to the module where they are declared.

To expose them externally:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

must exist.

Without outputs:

```text
Resource Values
```

remain internal to the module.

---

# Variable Flow

Example:

```text
Root Module
     │
     ▼
Input Variable
     │
     ▼
Child Module
     │
     ▼
Resource
     │
     ▼
Output
     │
     ▼
Root Module
```

This is the standard Terraform module communication model.

---

# Terraform Perspective

Example:

Root Module:

```hcl
variable "environment" {
  type = string
}

module "vpc" {
  source = "./modules/vpc"

  environment = var.environment
}
```

Child Module:

```hcl
variable "environment" {
  type = string
}
```

Terraform:

```text
Receives Input
       ↓
Passes To Module
       ↓
Uses Inside Module
```

---

# Real-World Example

Root Module:

```hcl
module "network" {
  source = "./modules/network"

  cidr = "10.0.0.0/16"
}
```

Child Module Output:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

Root Module Reference:

```hcl
module.network.vpc_id
```

---

# Production Use Case

Enterprise Modules commonly accept:

Inputs:

```text
Region
CIDR
Environment
Tags
Instance Type
```

Outputs:

```text
VPC ID
Subnet IDs
Security Group IDs
Load Balancer DNS
```

Modules communicate only through inputs and outputs.

---

# Module Communication Diagram

```text
Root Module
     │
     ▼
Module Inputs
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

# Important Exam Points

- Modules have isolated scopes.
- Variables are not automatically shared.
- Root module variables must be passed explicitly.
- Child modules receive values through input variables.
- Child modules expose values through outputs.
- Outputs are accessed using:

```hcl
module.<module_name>.<output_name>
```

- Modules communicate through inputs and outputs.

---

# Common Exam Traps

### Trap 1

Question:

Can child modules automatically access root module variables?

Correct:

No.

---

### Trap 2

Question:

How are values passed into modules?

Correct:

Input Variables.

---

### Trap 3

Question:

How are values exposed from modules?

Correct:

Outputs.

---

### Trap 4

Question:

How are module outputs referenced?

Correct:

```hcl
module.vpc.vpc_id
```

---

### Trap 5

Question:

Are module scopes shared?

Correct:

No.

Modules are isolated.

---

# Interview Questions

### What is a root module?

The directory where Terraform commands are executed.

### What is a child module?

A module called by another module.

### How do modules receive values?

Through input variables.

### How do modules expose values?

Through outputs.

### Are variables automatically shared between modules?

No.

---

# Practice Questions

### Question 1

Can child modules automatically access root module variables?

A. Yes

B. No

**Answer:** B

---

### Question 2

How are values passed into modules?

A. Outputs

B. Variables

C. Providers

D. State

**Answer:** B

---

### Question 3

How are values exposed from modules?

A. Variables

B. Providers

C. Outputs

D. Resources

**Answer:** C

---

### Question 4

What is the correct syntax for accessing a module output?

A.

```hcl
module.output.vpc_id
```

B.

```hcl
vpc.output.id
```

C.

```hcl
module.vpc.vpc_id
```

D.

```hcl
output.vpc.id
```

**Answer:** C

---

### Question 5

Which statement is TRUE?

A. Modules share variables automatically.

B. Modules communicate using inputs and outputs.

C. Outputs are automatically global.

D. Variables bypass module boundaries.

**Answer:** B

---

## Related Objectives

- 4c Variables and Outputs
- 5a Module Sources
- 5c Use Modules in Configuration
- 5d Manage Module Versions

---

## Key Takeaways

- Modules have isolated scopes.
- Variables are local to their module.
- Root module variables must be passed explicitly.
- Child modules receive inputs through variables.
- Child modules expose values through outputs.
- Outputs are referenced using module.<module_name>.<output_name>.
- Module communication occurs through inputs and outputs.
- Variable scope is a frequently tested Terraform Associate topic.
