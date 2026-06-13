# Objective: 4c - Use Variables and Outputs

## Definition

Variables and outputs are fundamental Terraform constructs used to make configurations reusable, flexible, and easier to maintain.

Variables allow input values to be supplied to Terraform configurations.

Outputs allow Terraform to expose information after infrastructure has been created.

Together they enable:

- Reusable configurations
- Environment-specific deployments
- Module communication
- Infrastructure visibility

Variables and outputs are among the most frequently tested Terraform Associate exam topics.

---

## Core Concepts

### Variables

Variables act as input parameters for Terraform configurations.

Instead of hardcoding values:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Use variables:

```hcl
variable "instance_type" {
  type = string
}
```

```hcl
resource "aws_instance" "web" {
  instance_type = var.instance_type
}
```

---

### Outputs

Outputs expose values after infrastructure deployment.

Example:

```hcl
output "instance_id" {
  value = aws_instance.web.id
}
```

Terraform displays:

```text
instance_id = i-123456789
```

after apply.

---

## Variable Block Syntax

General Syntax:

```hcl
variable "<NAME>" {

}
```

Example:

```hcl
variable "region" {
  type = string
}
```

---

## Variable Types

### String

```hcl
variable "region" {
  type = string
}
```

Example:

```text
us-east-1
```

---

### Number

```hcl
variable "instance_count" {
  type = number
}
```

Example:

```text
3
```

---

### Boolean

```hcl
variable "enable_monitoring" {
  type = bool
}
```

Example:

```text
true
```

---

## Variable Assignment Methods

Terraform supports multiple ways to assign values.

---

### Default Values

```hcl
variable "instance_type" {
  type    = string
  default = "t3.micro"
}
```

---

### terraform.tfvars

```hcl
instance_type = "t3.small"
```

Automatically loaded by Terraform.

---

### CLI Argument

```bash
terraform apply -var="instance_type=t3.small"
```

---

### Environment Variables

```bash
export TF_VAR_instance_type=t3.small
```

Terraform automatically loads:

```text
TF_VAR_<variable_name>
```

---

## Variable Reference Syntax

Variables are referenced using:

```text
var.<VARIABLE_NAME>
```

Example:

```hcl
resource "aws_instance" "web" {
  instance_type = var.instance_type
}
```

---

## Output Block Syntax

General Syntax:

```hcl
output "<NAME>" {
  value = <EXPRESSION>
}
```

---

## Output Example

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

Result:

```text
vpc_id = vpc-123456
```

---

## Output Reference in Modules

Child Module:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

Root Module:

```hcl
module.network.vpc_id
```

Outputs are the primary mechanism for sharing values between modules.

---

## Sensitive Variables

Terraform supports sensitive variables.

Example:

```hcl
variable "db_password" {
  type      = string
  sensitive = true
}
```

Purpose:

- Prevent accidental exposure
- Hide values in CLI output

---

## Sensitive Outputs

```hcl
output "database_password" {
  value     = var.db_password
  sensitive = true
}
```

Terraform hides the value.

---

## How It Works

Variable Flow:

```text
User Input
      │
      ▼
Variable
      │
      ▼
Resource Configuration
      │
      ▼
Infrastructure
```

---

Output Flow:

```text
Infrastructure
      │
      ▼
Resource Attribute
      │
      ▼
Output
      │
      ▼
User / Module
```

---

## Terraform Perspective

Variable:

```hcl
variable "bucket_name" {
  type = string
}
```

Resource:

```hcl
resource "aws_s3_bucket" "app" {
  bucket = var.bucket_name
}
```

Output:

```hcl
output "bucket_arn" {
  value = aws_s3_bucket.app.arn
}
```

Terraform receives input through variables and exposes results through outputs.

---

## Real-World Example

Deploy the same application to:

```text
Development
Staging
Production
```

Variable:

```hcl
variable "instance_type" {
  type = string
}
```

Values:

```text
Development → t3.micro
Staging     → t3.small
Production  → t3.large
```

Same Terraform code.

Different environments.

---

## Production Use Case

Enterprise modules commonly use:

Inputs:

```text
VPC CIDR
Region
Instance Type
Environment
Tags
```

Outputs:

```text
VPC ID
Subnet IDs
Load Balancer DNS
Security Group IDs
```

Variables and outputs make modules reusable.

---

## Command Reference

View Outputs:

```bash
terraform output
```

---

View Specific Output:

```bash
terraform output vpc_id
```

---

JSON Output:

```bash
terraform output -json
```

Useful for automation.

---

## Important Exam Points

- Variables provide input values.
- Outputs expose information.
- Variables use:

```text
var.<name>
```

- Outputs use:

```hcl
output
```

blocks.
- terraform.tfvars is automatically loaded.
- Variables support types.
- Variables support defaults.
- Sensitive variables hide values.
- Outputs enable module communication.

---

## Common Exam Traps

### Trap 1

Question:

How are variables referenced?

Correct:

```text
var.instance_type
```

---

### Trap 2

Question:

How are outputs created?

Correct:

```hcl
output
```

block.

---

### Trap 3

Question:

Which file is automatically loaded?

Correct:

```text
terraform.tfvars
```

---

### Trap 4

Question:

Can outputs reference resource attributes?

Correct:

Yes.

---

### Trap 5

Question:

How do modules expose values?

Correct:

Outputs.

---

### Trap 6

Question:

How do modules receive values?

Correct:

Variables.

---

## Interview Questions

### What are Terraform variables?

Inputs used to parameterize configurations.

### What are Terraform outputs?

Values exposed after infrastructure deployment.

### How are variables referenced?

```text
var.variable_name
```

### What is terraform.tfvars?

A file used to provide variable values.

### Why are outputs important?

They expose infrastructure information and enable module communication.

---

## Practice Questions

### Question 1

What is the primary purpose of variables?

A. Expose Infrastructure Information

B. Store State

C. Provide Input Values

D. Install Providers

**Answer:** C

---

### Question 2

How are variables referenced?

A.

```text
variable.region
```

B.

```text
var.region
```

C.

```text
region.var
```

D.

```text
input.region
```

**Answer:** B

---

### Question 3

What is the purpose of outputs?

A. Store State

B. Install Providers

C. Expose Values

D. Create Resources

**Answer:** C

---

### Question 4

Which file is automatically loaded for variable values?

A. outputs.tf

B. state.tf

C. terraform.tfvars

D. variables.json

**Answer:** C

---

### Question 5

Which statement is TRUE?

A. Outputs provide input values.

B. Variables expose resource information.

C. Variables provide input values and outputs expose results.

D. Variables replace providers.

**Answer:** C

---

## Related Objectives

- 4a Use and Differentiate Resource and Data Blocks
- 4b Refer to Resource Attributes and Create Cross-Resource References
- 4d Understand and Use Complex Types
- 4h Manage Sensitive Data

---

## Key Takeaways

- Variables provide inputs.
- Outputs expose results.
- Variables are referenced using var.<name>.
- Outputs expose resource attributes.
- terraform.tfvars is automatically loaded.
- Variables support defaults and types.
- Sensitive variables and outputs hide values.
- Variables and outputs are essential for reusable Terraform configurations and modules.
