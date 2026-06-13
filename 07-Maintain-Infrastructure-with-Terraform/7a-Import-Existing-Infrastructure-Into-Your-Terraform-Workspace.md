# Objective: 7a - Import Existing Infrastructure Into Your Terraform Workspace

## Definition

Terraform can only manage resources that exist in its state.

If infrastructure already exists outside Terraform, Terraform must first import those resources into state before it can manage them.

Terraform provides:

```bash
terraform import
```

for this purpose.

Importing infrastructure is a common task when organizations adopt Terraform after resources have already been created manually.

---

## Core Concepts

### Why Import Exists

Example:

An EC2 instance already exists.

Created using:

- AWS Console
- AWS CLI
- CloudFormation
- Another Team

Terraform does not know about it.

Terraform State:

```text
Empty
```

AWS:

```text
EC2 Instance Exists
```

Terraform cannot manage that instance until it is imported.

---

## What Import Does

Import adds existing infrastructure to:

```text
Terraform State
```

Example:

Before Import:

```text
AWS Resource Exists
```

```text
Terraform State Does Not Know About It
```

After Import:

```text
AWS Resource Exists
```

```text
Terraform State Tracks It
```

---

# Import Workflow

```text
Existing Resource
        │
        ▼
Create Terraform Configuration
        │
        ▼
Run terraform import
        │
        ▼
Resource Added To State
        │
        ▼
Terraform Can Manage Resource
```

---

# Import Syntax

General Syntax:

```bash
terraform import ADDRESS ID
```

---

## ADDRESS

Terraform resource address.

Example:

```text
aws_instance.web
```

---

## ID

Provider-specific resource identifier.

Example:

```text
i-0abc123456789
```

---

# Example Import

Terraform Configuration:

```hcl
resource "aws_instance" "web" {

}
```

Import Command:

```bash
terraform import \
aws_instance.web \
i-0abc123456789
```

Terraform:

```text
Adds Resource To State
```

---

# What Happens During Import

Terraform:

```text
Read Resource ID
        │
        ▼
Query Provider API
        │
        ▼
Retrieve Resource Information
        │
        ▼
Write Resource To State
```

---

# Important Requirement

Terraform configuration should exist before importing.

Example:

```hcl
resource "aws_instance" "web" {

}
```

Then:

```bash
terraform import
```

---

# Import Does NOT Create Infrastructure

Example:

```bash
terraform import aws_instance.web i-123456
```

Terraform:

```text
Does NOT Create Resource
```

Resource already exists.

---

# Import Does NOT Modify Infrastructure

Terraform:

```text
Adds State Entry
```

Only.

Infrastructure remains unchanged.

---

# Import Does NOT Generate Terraform Configuration

## Most Important Exam Trap

Many candidates believe:

```bash
terraform import
```

creates Terraform code.

This is FALSE.

Import updates:

```text
Terraform State
```

only.

---

## Example

Terraform Configuration:

```hcl
resource "aws_instance" "web" {

}
```

Import:

```bash
terraform import aws_instance.web i-123456
```

Result:

```text
State Updated
```

Terraform does NOT generate:

```hcl
instance_type = "t3.micro"
ami           = "ami-xxxx"
```

You must write configuration manually.

---

# Import Workflow Example

Current Situation:

```text
AWS EC2 Exists
```

Terraform:

```text
Not Managing Resource
```

---

Step 1

Create Configuration:

```hcl
resource "aws_instance" "web" {

}
```

---

Step 2

Import:

```bash
terraform import aws_instance.web i-123456
```

---

Step 3

Verify:

```bash
terraform state show aws_instance.web
```

---

Step 4

Update Configuration To Match Reality

---

# Verify Imported Resources

List State:

```bash
terraform state list
```

Example:

```text
aws_instance.web
```

---

Show Details:

```bash
terraform state show aws_instance.web
```

---

# Import Multiple Resources

Terraform imports one resource at a time.

Examples:

```bash
terraform import aws_vpc.main vpc-12345
```

```bash
terraform import aws_subnet.public subnet-12345
```

```bash
terraform import aws_security_group.web sg-12345
```

---

# Terraform Perspective

Before Import:

```text
Infrastructure Exists
```

```text
State Missing
```

---

After Import:

```text
Infrastructure Exists
```

```text
State Updated
```

Terraform begins tracking the resource.

---

# Real-World Example

Company Migrating To Terraform:

Existing Resources:

- VPC
- Subnets
- Security Groups
- EC2 Instances

Created manually over years.

Terraform Adoption Process:

```text
Create Configuration
       │
       ▼
Import Resources
       │
       ▼
Validate State
       │
       ▼
Manage With Terraform
```

---

# Production Use Case

Common scenarios:

- Terraform Adoption
- Legacy Infrastructure
- Migrations
- Team Standardization

Import is frequently used during:

```text
Infrastructure Modernization Projects
```

---

# Important Exam Points

- Import adds existing resources to state.
- Import uses:

```bash
terraform import
```

- Import requires resource address and resource ID.
- Import updates state.
- Import does not create resources.
- Import does not modify resources.
- Import does not generate Terraform configuration.
- Imported resources become Terraform-managed.

---

# Common Exam Traps

### Trap 1

Question:

What does terraform import modify?

Correct:

```text
Terraform State
```

---

### Trap 2

Question:

Does terraform import create infrastructure?

Correct:

```text
No
```

---

### Trap 3

Question:

Does terraform import generate configuration?

Correct:

```text
No
```

---

### Trap 4

Question:

What is required for import?

Correct:

```text
Resource Address
Resource ID
```

---

### Trap 5

Question:

Why import a resource?

Correct:

```text
Bring Existing Infrastructure Under Terraform Management
```

---

# Interview Questions

### Why does terraform import exist?

To bring existing infrastructure under Terraform management.

### What does terraform import modify?

Terraform state.

### Does import create infrastructure?

No.

### Does import generate Terraform code?

No.

### What information is required for import?

Resource address and resource ID.

---

# Practice Questions

### Question 1

What command imports existing infrastructure?

A. terraform state import

B. terraform import

C. terraform apply

D. terraform refresh

**Answer:** B

---

### Question 2

What does terraform import primarily modify?

A. Infrastructure

B. Modules

C. Terraform State

D. Providers

**Answer:** C

---

### Question 3

Does terraform import create infrastructure?

A. Yes

B. No

**Answer:** B

---

### Question 4

Does terraform import generate Terraform configuration?

A. Yes

B. No

**Answer:** B

---

### Question 5

Why is terraform import used?

A. Create Resources

B. Delete Resources

C. Manage Existing Infrastructure

D. Install Providers

**Answer:** C

---

## Related Objectives

- 6d Manage Resource Drift and Terraform State
- 7b Use The CLI To Inspect State
- 2d Explain How Terraform Uses And Manages State

---

## Key Takeaways

- Import brings existing infrastructure under Terraform management.
- Command:

```bash
terraform import
```

- Import updates Terraform state.
- Import does not create infrastructure.
- Import does not modify infrastructure.
- Import does not generate Terraform code.
- Resource address and resource ID are required.
- Import is a frequently tested Terraform Associate topic.
