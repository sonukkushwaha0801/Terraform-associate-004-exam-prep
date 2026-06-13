# Terraform State Management

## Domain Overview

Terraform state is one of the most important concepts in Terraform.

State allows Terraform to:

- Track managed resources
- Compare current and desired infrastructure
- Build execution plans
- Detect drift
- Manage dependencies

Without state, Terraform cannot determine what infrastructure it manages.

This domain covers:

- Local Backend
- State Locking
- Remote State
- Resource Drift
- State Management Commands

This is a high-weight Terraform Associate (004) exam domain.

---

# Objectives

## 6a - Describe the Local Backend

Understand:

- Default Terraform backend
- Local state storage
- terraform.tfstate
- Benefits and limitations

---

## 6b - Describe State Locking

Understand:

- Why state locking exists
- Concurrent operations
- Lock acquisition
- Lock release
- Locking in remote backends

---

## 6c - Configure Remote State Using the Backend Block

Understand:

- Backend block syntax
- Remote state storage
- Team collaboration
- S3 backend concepts
- HCP Terraform backend

---

## 6d - Manage Resource Drift and Terraform State

Understand:

- Resource drift
- Drift detection
- State inspection
- State manipulation
- Terraform state commands

---

# Why Terraform Needs State

Terraform manages infrastructure declaratively.

Example:

Desired State:

```text
2 EC2 Instances
```

Current Infrastructure:

```text
1 EC2 Instance
```

Terraform must know:

- What already exists
- What changed
- What should be created

This information is stored in:

```text
terraform.tfstate
```

---

# What Is State?

State is a snapshot of infrastructure managed by Terraform.

Example:

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

to generate a plan.

---

# Key Components Covered

## Local Backend

Stores state locally.

Example:

```text
terraform.tfstate
```

---

## Remote Backend

Stores state remotely.

Examples:

- AWS S3
- Azure Storage
- Google Cloud Storage
- HCP Terraform

---

## State Locking

Prevents multiple users from modifying state simultaneously.

---

## Resource Drift

Occurs when infrastructure changes outside Terraform.

Example:

```text
AWS Console
```

changes a resource.

Terraform configuration is unchanged.

State becomes inconsistent.

---

## State Commands

Examples:

```bash
terraform state list
terraform state show
terraform state mv
terraform state rm
```

---

# Domain Learning Outcomes

After completing this domain, you should be able to:

- Explain Terraform state
- Describe local backend behavior
- Explain state locking
- Configure remote backends
- Detect resource drift
- Inspect Terraform state
- Use state commands
- Understand collaborative Terraform workflows

---

# High-Probability Exam Topics

HashiCorp frequently tests:

- terraform.tfstate
- Local Backend
- Remote Backend
- State Locking
- Resource Drift
- terraform state list
- terraform state show
- terraform refresh (concept)
- S3 Backend
- Team Collaboration

---

# Recommended Study Order

1. Local Backend
2. Terraform State Fundamentals
3. State Locking
4. Remote State
5. Backend Configuration
6. Resource Drift
7. State Commands

---

# Objectives Covered

| Objective                   | Status |
| --------------------------- | ------ |
| 6a Local Backend            | ⬜      |
| 6b State Locking            | ⬜      |
| 6c Remote State             | ⬜      |
| 6d Drift & State Management | ⬜      |

---

# Domain Completion Checklist

- [ ] Completed 6a
- [ ] Completed 6b
- [ ] Completed 6c
- [ ] Completed 6d
- [ ] Completed Practice Questions
- [ ] Completed Revision Sheet
- [ ] Ready for Domain 7
