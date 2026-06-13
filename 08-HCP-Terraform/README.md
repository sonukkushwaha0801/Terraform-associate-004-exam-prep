# HCP Terraform

## Domain Overview

HCP Terraform is HashiCorp's managed SaaS platform for Terraform.

It provides:

- Remote State Storage
- State Locking
- Team Collaboration
- Remote Runs
- Policy Enforcement
- Centralized Infrastructure Management

HCP Terraform allows teams to manage Terraform workflows without maintaining their own Terraform infrastructure.

---

# Objectives

## 8a - Explain HCP Terraform and Its Benefits

Understand:

- What HCP Terraform is
- Why organizations use it
- Benefits over local workflows
- SaaS Terraform management

---

## 8b - Describe HCP Terraform Workspaces

Understand:

- Workspace concepts
- Workspace isolation
- State separation
- Environment management

---

## 8c - Understand the HCP Terraform Workflow

Understand:

- VCS-driven workflows
- Remote execution
- Plan and Apply process
- Team collaboration

---

# What Is HCP Terraform?

HCP Terraform is a cloud-hosted platform that manages Terraform operations.

Instead of running Terraform locally:

```text
Developer Laptop
      │
      ▼
Terraform CLI
```

Terraform runs in:

```text
HCP Terraform
```

---

# Why HCP Terraform Exists

Local Terraform works well for:

- Learning
- Small Projects
- Individual Developers

However larger teams need:

- Shared State
- Collaboration
- Access Control
- Auditing
- Governance

HCP Terraform provides these capabilities.

---

# Key Features

## Remote State Storage

Stores Terraform state centrally.

---

## State Locking

Prevents concurrent state modifications.

---

## Remote Execution

Runs Terraform remotely.

---

## Team Collaboration

Multiple engineers share workflows.

---

## Audit Trails

Tracks infrastructure changes.

---

## Version Control Integration

Connects with:

- GitHub
- GitLab
- Bitbucket
- Azure DevOps

---

# HCP Terraform Architecture

```text
Developer
     │
     ▼
Git Repository
     │
     ▼
HCP Terraform
     │
     ▼
Cloud Provider
```

---

# Benefits

## Centralized State

Single source of truth.

---

## Security

Credentials remain centralized.

---

## Collaboration

Teams share infrastructure workflows.

---

## Consistency

Standardized execution environment.

---

## Governance

Policies and approvals can be enforced.

---

# Exam-Relevant Topics

HashiCorp commonly tests:

- What HCP Terraform is
- Benefits of HCP Terraform
- Remote State Storage
- Remote Execution
- Collaboration Features
- Workspaces
- VCS Integration

---

# Recommended Study Order

1. HCP Terraform Basics
2. Workspaces
3. Remote Workflow
4. Practice Questions
5. Revision Sheet

---

# Objectives Covered

| Objective                 | Status |
| ------------------------- | ------ |
| 8a HCP Terraform Benefits | ⬜      |
| 8b Workspaces             | ⬜      |
| 8c Workflow               | ⬜      |

---

# Domain Completion Checklist

- [ ] Completed 8a
- [ ] Completed 8b
- [ ] Completed 8c
- [ ] Completed Practice Questions
- [ ] Completed Revision Sheet
- [ ] Terraform Associate (004) Syllabus Complete
