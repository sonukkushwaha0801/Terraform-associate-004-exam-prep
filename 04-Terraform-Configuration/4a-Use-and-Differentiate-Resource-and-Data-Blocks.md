# Objective: 4a - Use and Differentiate Resource and Data Blocks

## Definition

Terraform uses two primary block types for interacting with infrastructure:

- Resource Blocks
- Data Blocks

Understanding the difference between them is critical because they serve completely different purposes.

A common Terraform Associate exam question is:

> When should you use a resource block versus a data block?

The answer depends on whether Terraform is creating/managing infrastructure or simply reading existing infrastructure.

---

## Core Concepts

### Resource Block

A resource block creates and manages infrastructure.

Terraform becomes responsible for the lifecycle of the resource.

Examples:

- EC2 Instances
- S3 Buckets
- VPCs
- Azure Resource Groups
- Kubernetes Deployments

General Syntax:

```hcl
resource "<TYPE>" "<NAME>" {

}
```

Example:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

Terraform will:

- Create the instance
- Track it in state
- Modify it when configuration changes
- Destroy it when removed

---

### Data Block

A data block reads information from existing infrastructure.

Terraform does not manage the lifecycle of resources retrieved through data sources.

General Syntax:

```hcl
data "<TYPE>" "<NAME>" {

}
```

Example:

```hcl
data "aws_ami" "latest" {
  most_recent = true

  owners = ["amazon"]
}
```

Terraform retrieves information only.

Terraform will NOT:

- Create AMIs
- Modify AMIs
- Destroy AMIs

---

## Resource vs Data Source

### Resource

Purpose:

```text
Create and Manage Infrastructure
```

Example:

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "company-app-bucket"
}
```

Terraform owns the resource lifecycle.

---

### Data Source

Purpose:

```text
Read Existing Infrastructure
```

Example:

```hcl
data "aws_caller_identity" "current" {}
```

Terraform retrieves information only.

---

## How It Works

Resource Workflow:

```text
Terraform
     │
     ▼
Create Resource
     │
     ▼
Track in State
     │
     ▼
Manage Lifecycle
```

---

Data Source Workflow:

```text
Terraform
     │
     ▼
Query API
     │
     ▼
Retrieve Information
     │
     ▼
Use Returned Values
```

---

## Terraform Perspective

### Resource Example

```hcl
resource "aws_security_group" "web" {
  name = "web-sg"
}
```

Terraform:

- Creates security group
- Stores in state
- Manages future changes

---

### Data Source Example

```hcl
data "aws_region" "current" {}
```

Terraform:

- Reads current AWS region
- Returns information
- Does not manage region

---

## Real-World Example

Create VPC:

```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}
```

Retrieve Latest Amazon Linux AMI:

```hcl
data "aws_ami" "latest" {
  most_recent = true

  owners = ["amazon"]
}
```

Use Data Source Result:

```hcl
resource "aws_instance" "web" {
  ami           = data.aws_ami.latest.id
  instance_type = "t3.micro"
}
```

Terraform:

- Creates EC2 Instance
- Reads existing AMI information

---

## Production Use Case

Enterprise Deployment:

Resources:

```text
VPC
Subnets
Security Groups
EC2 Instances
```

Data Sources:

```text
Latest AMI
Current AWS Account
Availability Zones
Existing VPC IDs
```

Most Terraform projects use both resources and data sources together.

---

## Common Data Sources

### AWS Account Information

```hcl
data "aws_caller_identity" "current" {}
```

---

### AWS Region

```hcl
data "aws_region" "current" {}
```

---

### Availability Zones

```hcl
data "aws_availability_zones" "available" {}
```

---

### Latest AMI

```hcl
data "aws_ami" "latest" {
  most_recent = true
}
```

---

## Command Reference

Validate:

```bash
terraform validate
```

Plan:

```bash
terraform plan
```

Apply:

```bash
terraform apply
```

Data sources are refreshed during planning and applying.

---

## Important Exam Points

- Resource blocks create and manage infrastructure.
- Data blocks read existing infrastructure.
- Resources are tracked in state.
- Data sources are not managed by Terraform.
- Resource syntax begins with resource.
- Data source syntax begins with data.
- Data sources are commonly used to retrieve existing information.
- Most Terraform configurations use both resources and data sources.

---

## Common Exam Traps

### Trap 1

Question:

Which block creates infrastructure?

Correct:

```hcl
resource
```

---

### Trap 2

Question:

Which block reads existing infrastructure?

Correct:

```hcl
data
```

---

### Trap 3

Question:

Does a data source create resources?

Correct:

No.

---

### Trap 4

Question:

Does Terraform manage the lifecycle of data sources?

Correct:

No.

---

### Trap 5

Question:

Which block is stored and managed through state?

Correct:

Resource Block.

---

## Interview Questions

### What is a Terraform resource?

A block that creates and manages infrastructure.

### What is a Terraform data source?

A block that retrieves information about existing infrastructure.

### What is the primary difference between resources and data sources?

Resources manage infrastructure.
Data sources only read information.

### Can data sources create resources?

No.

### Why are data sources useful?

They allow Terraform to use information about existing infrastructure.

---

## Practice Questions

### Question 1

Which Terraform block creates infrastructure?

A. data

B. variable

C. resource

D. output

**Answer:** C

**Explanation:** Resource blocks create and manage infrastructure.

---

### Question 2

Which Terraform block retrieves information about existing infrastructure?

A. resource

B. data

C. output

D. local

**Answer:** B

**Explanation:** Data blocks read information from existing infrastructure.

---

### Question 3

Which statement is TRUE?

A. Data sources create resources.

B. Resources retrieve information only.

C. Resources manage infrastructure lifecycle.

D. Data sources are stored as managed infrastructure.

**Answer:** C

**Explanation:** Resources are responsible for lifecycle management.

---

### Question 4

Which block type would you use to retrieve the latest AWS AMI?

A. resource

B. variable

C. output

D. data

**Answer:** D

**Explanation:** Existing AMI information is retrieved using a data source.

---

### Question 5

What is the correct syntax for a resource block?

A.

```hcl
data "aws_instance" "web" {}
```

B.

```hcl
resource "aws_instance" "web" {}
```

C.

```hcl
variable "aws_instance" "web" {}
```

D.

```hcl
output "aws_instance" "web" {}
```

**Answer:** B

**Explanation:** Resources use the resource keyword.

---

## Related Objectives

- 4b Refer to Resource Attributes and Create Cross-Resource References
- 4c Use Variables and Outputs
- 4f Define Resource Dependencies
- 6d Manage Resource Drift and Terraform State

---

## Key Takeaways

- Resources create and manage infrastructure.
- Data sources read existing infrastructure.
- Resources are lifecycle-managed by Terraform.
- Data sources are read-only.
- Resource syntax uses resource.
- Data source syntax uses data.
- Most Terraform configurations use both together.
- Resource vs Data Source is a very common Terraform Associate exam topic.
