# Objective: 6d - Manage Resource Drift and Terraform State

## Definition

Terraform state represents Terraform's understanding of managed infrastructure.

Over time, infrastructure may change outside Terraform.

These unexpected changes create:

```text
Resource Drift
```

Terraform provides mechanisms to:

- Detect Drift
- Inspect State
- Modify State
- Import Existing Resources

This objective is heavily tested in Terraform Associate (004).

---

## Core Concepts

### What Is Resource Drift?

Resource drift occurs when real infrastructure differs from Terraform's expected state.

Example:

Terraform Configuration:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

---

Terraform State:

```text
t3.micro
```

---

AWS Console Change:

```text
t3.large
```

---

Result:

```text
Drift
```

Terraform configuration and real infrastructure no longer match.

---

# Causes of Drift

Common causes:

- AWS Console Changes
- Azure Portal Changes
- GCP Console Changes
- Manual CLI Commands
- Third-Party Automation

---

## Example

Terraform creates:

```text
Security Group
```

Administrator manually deletes it.

Terraform state still believes:

```text
Resource Exists
```

Drift occurs.

---

# Drift Detection

Terraform detects drift during:

```bash
terraform plan
```

and

```bash
terraform apply
```

Terraform compares:

```text
Configuration
     vs
State
     vs
Infrastructure
```

---

## Workflow

```text
Terraform Config
        │
        ▼
Terraform State
        │
        ▼
Actual Infrastructure
```

Differences become:

```text
Drift
```

---

# Example Drift Detection

Command:

```bash
terraform plan
```

Output:

```text
~ instance_type
  t3.large -> t3.micro
```

Terraform plans corrective action.

---

# Terraform State Commands

Terraform provides a dedicated:

```bash
terraform state
```

command family.

Purpose:

- Inspect State
- Modify State
- Repair State

---

# terraform state list

## Purpose

Lists all resources currently tracked in state.

Command:

```bash
terraform state list
```

Example Output:

```text
aws_vpc.main
aws_subnet.public
aws_instance.web
```

---

## Exam Tip

Question:

Which command lists resources tracked by state?

Answer:

```bash
terraform state list
```

---

# terraform state show

## Purpose

Displays detailed information about a resource in state.

Command:

```bash
terraform state show aws_instance.web
```

Output:

```text
Resource Attributes
```

including:

- IDs
- Tags
- Configuration Values

---

## Exam Tip

Question:

Which command displays resource details from state?

Answer:

```bash
terraform state show
```

---

# terraform state mv

## Purpose

Moves resources within state.

Used when:

- Renaming Resources
- Refactoring Code
- Module Reorganization

---

## Example

Before:

```text
aws_instance.web
```

After:

```text
aws_instance.app
```

Command:

```bash
terraform state mv \
aws_instance.web \
aws_instance.app
```

---

## Benefit

Avoids:

```text
Destroy + Recreate
```

operations.

---

# terraform state rm

## Purpose

Removes a resource from state.

Command:

```bash
terraform state rm aws_instance.web
```

Terraform:

```text
Stops Tracking Resource
```

---

## Important

Terraform does NOT destroy the resource.

Only removes it from state.

---

## Exam Favorite

Question:

Does terraform state rm delete infrastructure?

Answer:

```text
No
```

Only state is modified.

---

# terraform import

## Definition

Imports existing infrastructure into Terraform state.

Useful when resources already exist.

---

## Example

Existing Resource:

```text
AWS EC2 Instance
```

Terraform State:

```text
Not Managed
```

---

Command:

```bash
terraform import \
aws_instance.web i-123456789
```

Terraform:

```text
Adds Resource To State
```

---

## Important

Import:

```text
State Only
```

Terraform configuration must still exist.

---

## Exam Trap

Import does NOT generate Terraform code.

It only updates state.

---

# State Inspection Workflow

```text
terraform state list
        │
        ▼
terraform state show
        │
        ▼
Inspect Resource
```

---

# State Modification Workflow

```text
terraform state mv
```

↓

```text
Move Resource
```

---

```text
terraform state rm
```

↓

```text
Remove Resource From State
```

---

# Terraform Perspective

Terraform stores:

```text
Resource IDs
Attributes
Metadata
Dependencies
```

inside state.

Commands allow controlled management of that data.

---

# Real-World Example

Team imports existing infrastructure:

```text
Existing VPC
Existing Subnets
Existing Security Groups
```

Using:

```bash
terraform import
```

Terraform begins tracking them.

---

# Production Use Cases

## Drift Detection

```bash
terraform plan
```

Regularly executed in CI/CD.

---

## State Inspection

```bash
terraform state show
```

Used during troubleshooting.

---

## Refactoring

```bash
terraform state mv
```

Used when reorganizing modules.

---

## Importing Legacy Resources

```bash
terraform import
```

Used when adopting Terraform.

---

# Important Exam Points

- Drift occurs when infrastructure changes outside Terraform.
- terraform plan detects drift.
- terraform state list lists tracked resources.
- terraform state show displays resource details.
- terraform state mv moves state entries.
- terraform state rm removes resources from state.
- terraform state rm does not destroy infrastructure.
- terraform import adds existing resources to state.
- Import does not generate Terraform code.

---

# Common Exam Traps

### Trap 1

Question:

What causes resource drift?

Correct:

```text
Infrastructure Changes Outside Terraform
```

---

### Trap 2

Question:

Which command detects drift?

Correct:

```bash
terraform plan
```

---

### Trap 3

Question:

Which command lists tracked resources?

Correct:

```bash
terraform state list
```

---

### Trap 4

Question:

Which command shows resource details?

Correct:

```bash
terraform state show
```

---

### Trap 5

Question:

Does terraform state rm delete infrastructure?

Correct:

```text
No
```

---

### Trap 6

Question:

Does terraform import generate Terraform code?

Correct:

```text
No
```

---

### Trap 7

Question:

What does terraform import update?

Correct:

```text
Terraform State
```

---

# Interview Questions

### What is resource drift?

Infrastructure changes that occur outside Terraform.

### How is drift detected?

Using:

```bash
terraform plan
```

### What does terraform state list do?

Lists resources tracked by state.

### What does terraform state show do?

Displays resource details from state.

### What does terraform import do?

Adds existing infrastructure to Terraform state.

---

# Practice Questions

### Question 1

What is resource drift?

A. Provider Upgrade

B. Infrastructure Changes Outside Terraform

C. State Lock Failure

D. Module Upgrade

**Answer:** B

---

### Question 2

Which command commonly detects drift?

A.

```bash
terraform init
```

B.

```bash
terraform plan
```

C.

```bash
terraform fmt
```

D.

```bash
terraform validate
```

**Answer:** B

---

### Question 3

Which command lists resources tracked by state?

A.

```bash
terraform show
```

B.

```bash
terraform state list
```

C.

```bash
terraform state show
```

D.

```bash
terraform refresh
```

**Answer:** B

---

### Question 4

Which command displays details of a resource in state?

A.

```bash
terraform state show
```

B.

```bash
terraform state list
```

C.

```bash
terraform show state
```

D.

```bash
terraform inspect
```

**Answer:** A

---

### Question 5

What does terraform state rm do?

A. Deletes Infrastructure

B. Removes Resource From State

C. Destroys Provider

D. Removes Module

**Answer:** B

---

## Related Objectives

- 2d Explain How Terraform Uses and Manages State
- 6a Local Backend
- 6b State Locking
- 7a Import Existing Infrastructure

---

## Key Takeaways

- Resource drift occurs when infrastructure changes outside Terraform.
- terraform plan detects drift.
- terraform state list lists tracked resources.
- terraform state show displays resource details.
- terraform state mv moves state entries.
- terraform state rm removes resources from state only.
- terraform import adds existing resources to state.
- Import does not generate Terraform code.
- State management commands are common Terraform Associate exam topics.
