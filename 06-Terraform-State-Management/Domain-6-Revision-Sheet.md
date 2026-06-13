# Domain 6 Revision Sheet

## Terraform State Management

### Objectives Covered

- 6a Describe the Local Backend
- 6b Describe State Locking
- 6c Configure Remote State Using the Backend Block
- 6d Manage Resource Drift and Terraform State

---

# What Is Terraform State?

Terraform state is Terraform's record of managed infrastructure.

Terraform uses state to:

- Track Resources
- Track Resource IDs
- Build Execution Plans
- Detect Drift
- Manage Dependencies

---

## Exam Memory Trick

```text
State = Terraform Memory
```

Without state:

```text
Terraform Cannot Track Infrastructure
```

---

# State Workflow

```text
Terraform Configuration
          │
          ▼
Desired State
          │
          ▼
Terraform State
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

to generate plans.

---

# Local Backend

## Definition

Default Terraform backend.

Stores state locally.

---

## State File

```text
terraform.tfstate
```

---

## Backup File

```text
terraform.tfstate.backup
```

---

## Default Behavior

No backend configuration:

```hcl
resource "aws_instance" "web" {
}
```

Terraform automatically uses:

```text
Local Backend
```

---

## Advantages

✅ Simple

✅ Fast

✅ Ideal For Learning

---

## Disadvantages

❌ No Centralized Storage

❌ Poor Collaboration

❌ No Distributed Locking

❌ State Loss Risk

---

# Remote Backend

## Definition

Stores Terraform state remotely.

---

## Benefits

✅ Team Collaboration

✅ Centralized State

✅ State Locking

✅ Backup & Recovery

✅ Access Control

---

# Common Remote Backends

## AWS

```hcl
backend "s3" {}
```

---

## Azure

```hcl
backend "azurerm" {}
```

---

## Google Cloud

```hcl
backend "gcs" {}
```

---

## HCP Terraform

```hcl
cloud {}
```

---

# Backend Block

## Syntax

```hcl
terraform {

  backend "s3" {

  }

}
```

---

## Important Rule

Only:

```text
ONE BACKEND
```

per configuration.

---

# Backend Initialization

Command:

```bash
terraform init
```

Purpose:

- Configure Backend
- Download Providers
- Download Modules
- Migrate State

---

# State Locking

## Purpose

Prevents:

```text
Concurrent State Modifications
```

---

## Problem Without Locking

Engineer A:

```bash
terraform apply
```

Engineer B:

```bash
terraform apply
```

Both modify:

```text
Same State File
```

Result:

```text
State Corruption
```

---

## Locking Workflow

```text
Acquire Lock
      │
      ▼
Modify Infrastructure
      │
      ▼
Update State
      │
      ▼
Release Lock
```

---

## Lock Acquired

Before:

```text
State Modification
```

---

## Lock Released

After:

```text
Operation Completion
```

---

# Stale Locks

Causes:

- Crash
- Network Failure
- Interrupted Terraform Process

---

## Remove Stale Lock

Command:

```bash
terraform force-unlock LOCK_ID
```

---

## Exam Trap

Question:

What command removes stale locks?

Answer:

```bash
terraform force-unlock
```

---

# Resource Drift

## Definition

Infrastructure changes outside Terraform.

---

## Example

Terraform:

```text
t3.micro
```

AWS Console:

```text
t3.large
```

Result:

```text
Drift
```

---

## Common Causes

- AWS Console
- Azure Portal
- GCP Console
- Manual CLI Changes
- Third-Party Tools

---

# Drift Detection

Command:

```bash
terraform plan
```

Terraform compares:

```text
Configuration
State
Infrastructure
```

---

## Exam Trap

Question:

Which command commonly detects drift?

Answer:

```bash
terraform plan
```

---

# State Commands

## List Resources

```bash
terraform state list
```

Purpose:

```text
Show All Resources Tracked By State
```

---

## Show Resource Details

```bash
terraform state show RESOURCE
```

Example:

```bash
terraform state show aws_instance.web
```

---

## Move Resource

```bash
terraform state mv SOURCE DESTINATION
```

Example:

```bash
terraform state mv \
aws_instance.web \
aws_instance.app
```

---

## Remove Resource From State

```bash
terraform state rm RESOURCE
```

Example:

```bash
terraform state rm aws_instance.web
```

---

## Important

```bash
terraform state rm
```

does:

```text
NOT DELETE INFRASTRUCTURE
```

Only removes tracking.

---

# Import Existing Infrastructure

## Command

```bash
terraform import ADDRESS ID
```

---

## Example

```bash
terraform import \
aws_instance.web i-123456789
```

---

## Purpose

Adds existing infrastructure to Terraform state.

---

## Exam Trap

Import:

```text
Updates State
```

Import:

```text
DOES NOT Generate Terraform Code
```

---

# State Command Cheat Sheet

| Command                | Purpose                  |
| ---------------------- | ------------------------ |
| terraform state list   | List Resources           |
| terraform state show   | Show Resource Details    |
| terraform state mv     | Move State Entry         |
| terraform state rm     | Remove From State        |
| terraform import       | Import Existing Resource |
| terraform force-unlock | Remove Stale Lock        |

---

# Local vs Remote Backend

| Feature           | Local         | Remote         |
| ----------------- | ------------- | -------------- |
| State Location    | Local Machine | Remote Service |
| Shared State      | ❌             | ✅              |
| Collaboration     | ❌             | ✅              |
| State Locking     | Limited       | ✅              |
| Backup & Recovery | Weak          | Strong         |
| Production Ready  | ❌             | ✅              |

---

# Top 20 Exam Facts

### State tracks managed infrastructure.

### State file:

```text
terraform.tfstate
```

### Backup file:

```text
terraform.tfstate.backup
```

### Local backend is default.

### Backend controls state storage.

### Only one backend per configuration.

### Remote state enables collaboration.

### terraform init initializes backends.

### State locking prevents concurrent modifications.

### Locks acquired before state updates.

### Locks released after operations.

### terraform force-unlock removes stale locks.

### Drift = Infrastructure changed outside Terraform.

### terraform plan detects drift.

### terraform state list lists resources.

### terraform state show displays resource details.

### terraform state mv moves state entries.

### terraform state rm removes state tracking only.

### terraform import updates state.

### Import does not generate Terraform code.

---

# Most Common Exam Traps

## Trap 1

Default backend?

```text
Local Backend
```

---

## Trap 2

State file?

```text
terraform.tfstate
```

---

## Trap 3

Backup state file?

```text
terraform.tfstate.backup
```

---

## Trap 4

Drift detection command?

```bash
terraform plan
```

---

## Trap 5

Remove stale lock?

```bash
terraform force-unlock
```

---

## Trap 6

Import generates code?

```text
NO
```

---

## Trap 7

state rm deletes infrastructure?

```text
NO
```

---

## Trap 8

Multiple backends supported?

```text
NO
```

---

## Trap 9

Remote state primary benefit?

```text
Team Collaboration
```

---

## Trap 10

State locking purpose?

```text
Prevent Concurrent Modifications
```

---

# 60-Second Exam Revision

```text
State = Terraform Memory
```

```text
terraform.tfstate
```

```text
Local Backend = Default
```

```text
Remote Backend = Collaboration
```

```bash
terraform init
```

```bash
terraform plan
```

```bash
terraform state list
```

```bash
terraform state show
```

```bash
terraform state mv
```

```bash
terraform state rm
```

```bash
terraform import
```

```bash
terraform force-unlock
```

```text
Drift = External Changes
```

```text
Import = State Only
```

```text
state rm ≠ Delete Resource
```

---

# Domain Completion Checklist

- [ ] Completed 6a Local Backend
- [ ] Completed 6b State Locking
- [ ] Completed 6c Remote State
- [ ] Completed 6d Drift and State Management
- [ ] Completed Practice Questions
- [ ] Scored 35+/40
- [ ] Reviewed All Mistakes
- [ ] Ready For Domain 7
