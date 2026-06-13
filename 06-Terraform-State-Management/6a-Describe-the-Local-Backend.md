# Objective: 6a - Describe the Local Backend

## Definition

A backend determines how Terraform stores and manages state.

Every Terraform configuration uses exactly one backend.

If no backend is explicitly configured, Terraform automatically uses the:

```text
Local Backend
```

The local backend stores state files on the machine where Terraform is executed.

This is Terraform's default backend.

---

## Core Concepts

### What Is a Backend?

A backend is responsible for:

- Storing Terraform State
- Retrieving State
- Updating State
- Managing Operations Related to State

Terraform uses state to track managed infrastructure.

Without a backend:

```text
No State
=
No Infrastructure Tracking
```

---

# Default Backend

Terraform automatically uses:

```text
Local Backend
```

unless another backend is configured.

Example:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

No backend block exists.

Terraform automatically creates:

```text
terraform.tfstate
```

locally.

---

# Local Backend

## Definition

The local backend stores Terraform state files on the local filesystem.

Example:

```text
project/
│
├── main.tf
├── terraform.tfstate
└── terraform.tfstate.backup
```

---

## State File

Primary file:

```text
terraform.tfstate
```

Purpose:

Stores Terraform's current understanding of infrastructure.

---

## Backup File

Backup file:

```text
terraform.tfstate.backup
```

Purpose:

Stores the previous state version.

Created automatically before state modifications.

---

# What Is Stored In State?

Terraform state contains:

- Resource IDs
- Resource Attributes
- Dependency Information
- Metadata
- Output Values

Example:

```json
{
  "resources": [
    {
      "type": "aws_instance",
      "name": "web"
    }
  ]
}
```

---

# Why Terraform Needs State

Example:

Configuration:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Terraform creates:

```text
EC2 Instance
```

During the next execution:

```bash
terraform plan
```

Terraform must know:

```text
What already exists?
```

State provides the answer.

---

# Terraform Workflow With State

```text
Configuration
      │
      ▼
Desired State
      │
      ▼
State File
      │
      ▼
Real Infrastructure
```

Terraform compares:

```text
Desired State
vs
Current State
```

to calculate changes.

---

# Local Backend Workflow

```text
terraform apply
       │
       ▼
Create Resource
       │
       ▼
Update State File
       │
       ▼
Save terraform.tfstate
```

---

# Viewing State

Example:

```bash
terraform show
```

Displays:

```text
State Information
```

---

## State File Location

Default location:

```text
./terraform.tfstate
```

inside the current working directory.

---

# Advantages of Local Backend

## Simple

No additional configuration required.

---

## Fast

State stored directly on local disk.

---

## Easy Learning Environment

Ideal for:

- Labs
- Testing
- Learning Terraform

---

## Default Behavior

Works immediately after:

```bash
terraform init
```

---

# Disadvantages of Local Backend

## No Collaboration

State exists only on one machine.

Problem:

```text
Engineer A
and
Engineer B
```

cannot safely share state.

---

## No State Locking

Local backend does not provide distributed locking for teams.

Risk:

```text
Concurrent Modifications
```

---

## State Loss Risk

If the machine fails:

```text
State May Be Lost
```

---

## Security Risk

State files often contain:

- Passwords
- Tokens
- Resource Metadata

Local storage increases exposure risk.

---

# Local Backend Example

No configuration required.

Terraform automatically uses:

```text
Local Backend
```

Example:

```hcl
resource "aws_s3_bucket" "logs" {
  bucket = "company-logs"
}
```

State stored locally.

---

# Terraform Perspective

Example:

```bash
terraform apply
```

Terraform:

```text
Create Resource
      │
      ▼
Record Resource ID
      │
      ▼
Store In terraform.tfstate
```

---

# Real-World Example

Developer Laptop:

```text
terraform.tfstate
```

stored locally.

Suitable for:

- Personal Projects
- Learning Labs
- Small Demos

Not ideal for:

- Enterprise Teams
- Production Environments

---

# Production Use Case

Production environments typically avoid:

```text
Local Backend
```

and instead use:

- S3 Backend
- Azure Storage Backend
- GCS Backend
- HCP Terraform

Reasons:

- Shared State
- State Locking
- Backups
- Access Control

---

# Local Backend vs Remote Backend

| Feature             | Local Backend | Remote Backend |
| ------------------- | ------------- | -------------- |
| State Location      | Local Machine | Remote Service |
| Team Collaboration  | No            | Yes            |
| State Locking       | No            | Usually Yes    |
| Centralized Storage | No            | Yes            |
| Production Ready    | No            | Yes            |
| Learning Labs       | Yes           | Yes            |

---

# Important Exam Points

- Local backend is Terraform's default backend.
- State file:

```text
terraform.tfstate
```

- Backup file:

```text
terraform.tfstate.backup
```

- Local backend stores state on the local filesystem.
- Terraform uses state to track infrastructure.
- State may contain sensitive information.
- Local backend is suitable for learning and testing.
- Remote backends are preferred for production.

---

# Common Exam Traps

### Trap 1

Question:

Which backend is used by default?

Correct:

```text
Local Backend
```

---

### Trap 2

Question:

What file stores Terraform state?

Correct:

```text
terraform.tfstate
```

---

### Trap 3

Question:

What file stores previous state?

Correct:

```text
terraform.tfstate.backup
```

---

### Trap 4

Question:

Does the local backend support team collaboration?

Correct:

```text
No
```

---

### Trap 5

Question:

Should local backend be used in production?

Correct:

```text
Generally No
```

---

### Trap 6

Question:

Can state files contain secrets?

Correct:

```text
Yes
```

---

# Interview Questions

### What is a Terraform backend?

A component responsible for storing and managing Terraform state.

### What is Terraform's default backend?

Local backend.

### Where is local state stored?

```text
terraform.tfstate
```

### What is terraform.tfstate.backup?

A backup of the previous state.

### Why is local backend unsuitable for production?

Lack of centralized storage, collaboration, locking, and resilience.

---

# Practice Questions

### Question 1

Which backend does Terraform use by default?

A. S3 Backend

B. Local Backend

C. Azure Backend

D. HCP Backend

**Answer:** B

---

### Question 2

What file stores Terraform state?

A.

```text
terraform.lock.hcl
```

B.

```text
terraform.tfvars
```

C.

```text
terraform.tfstate
```

D.

```text
main.tf
```

**Answer:** C

---

### Question 3

What file stores the previous state version?

A.

```text
terraform.tfstate.backup
```

B.

```text
terraform.backup
```

C.

```text
state.bak
```

D.

```text
terraform.old
```

**Answer:** A

---

### Question 4

Which statement is TRUE?

A. Local backend is recommended for large teams.

B. Local backend stores state remotely.

C. Local backend stores state locally.

D. Local backend provides centralized state.

**Answer:** C

---

### Question 5

Why do production environments typically use remote backends?

A. Smaller State Files

B. Team Collaboration and State Management

C. Faster Providers

D. Faster Resource Creation

**Answer:** B

---

## Related Objectives

- 2d Explain How Terraform Uses and Manages State
- 6b State Locking
- 6c Remote State Backends
- 6d Resource Drift and State Management

---

## Key Takeaways

- A backend manages Terraform state.
- Local backend is Terraform's default backend.
- State is stored in terraform.tfstate.
- Backup state is stored in terraform.tfstate.backup.
- State tracks Terraform-managed resources.
- State can contain sensitive information.
- Local backend is useful for learning and testing.
- Production environments typically use remote backends.
