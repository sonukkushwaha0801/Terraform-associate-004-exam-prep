# HCP Terraform

## Domain Overview

HCP Terraform is HashiCorp's managed platform for provisioning, managing, collaborating on, and governing infrastructure using Terraform.

Instead of running Terraform entirely on a local machine, HCP Terraform provides:

- Remote Execution
- Centralized State Management
- Team Collaboration
- Governance Controls
- Policy Enforcement
- Audit Trails
- VCS Integration
- Infrastructure Automation

HCP Terraform is designed to help teams manage Terraform at scale while improving security, consistency, and operational efficiency.

This domain covers:

- Creating infrastructure with HCP Terraform
- Collaboration and governance capabilities
- Workspaces and projects
- HCP Terraform integrations

---

# Objectives

## 8a - Use HCP Terraform to Create Infrastructure

Understand:

- HCP Terraform Fundamentals
- Remote Operations
- Remote Execution
- Terraform Runs
- State Management
- VCS-driven Workflows
- CLI-driven Workflows

---

## 8b - Describe HCP Terraform Collaboration and Governance Features

Understand:

- Teams
- Role-Based Access Control (RBAC)
- Audit Trails
- Policy Enforcement
- Private Module Registry
- Cost Estimation
- Drift Detection
- Health Assessments
- Variable Sets

---

## 8c - Describe How to Organize and Use HCP Terraform Workspaces and Projects

Understand:

- HCP Terraform Workspaces
- Projects
- Workspace Isolation
- Environment Separation
- Run Triggers
- Workspace Relationships
- Workspace Organization

---

## 8d - Configure and Use HCP Terraform Integration

Understand:

- terraform login
- HCP Terraform Authentication
- VCS Integration
- GitHub Integration
- Remote Backend Configuration
- Cloud Block Configuration
- State Migration
- CLI-Driven Runs
- VCS-Driven Runs

---

# What Is HCP Terraform?

HCP Terraform is a cloud-based platform that manages Terraform workflows.

Without HCP Terraform:

```text
Developer Laptop
        │
        ▼
terraform plan
terraform apply
        │
        ▼
Cloud Infrastructure
```

---

With HCP Terraform:

```text
Developer
      │
      ▼
HCP Terraform
      │
      ▼
Plan
Apply
State
Policies
Collaboration
      │
      ▼
Cloud Infrastructure
```

---

# Why HCP Terraform Exists

As organizations scale Terraform usage, several challenges emerge:

- State Management
- Team Collaboration
- Access Control
- Governance
- Compliance
- Change Visibility

HCP Terraform solves these problems by centralizing Terraform operations.

---

# Key HCP Terraform Features

## Remote State Storage

Stores Terraform state centrally.

Benefits:

- Shared State
- Backups
- Security
- Collaboration

---

## Remote Execution

Runs Terraform remotely.

Benefits:

- Consistency
- Security
- Standardized Workflows

---

## Team Collaboration

Supports:

- Multiple Users
- Teams
- Shared Workspaces
- Approval Workflows

---

## Governance

Provides:

- Policy Enforcement
- Access Controls
- Audit Logging

---

## Integrations

Supports:

- GitHub
- GitLab
- Bitbucket
- Azure DevOps

---

# HCP Terraform Workflow

Typical workflow:

```text
Git Commit
      │
      ▼
VCS Integration
      │
      ▼
HCP Terraform Run
      │
      ▼
Plan
      │
      ▼
Approval
      │
      ▼
Apply
      │
      ▼
State Update
```

---

# Domain Learning Outcomes

After completing this domain, you should be able to:

- Explain HCP Terraform fundamentals
- Create infrastructure using HCP Terraform
- Describe governance capabilities
- Use workspaces and projects
- Configure HCP Terraform integrations
- Understand remote execution workflows

---

# Relationship to Previous Domains

## Domains 1-7

Focused on:

- Terraform CLI
- Local Workflows
- State Management
- Infrastructure Provisioning

---

## Domain 8

Focuses on:

- HCP Terraform Platform
- Team Collaboration
- Governance
- Enterprise Terraform Workflows

---

# High-Probability Exam Topics

HashiCorp commonly tests:

- HCP Terraform
- Remote Execution
- Workspaces
- Projects
- Variable Sets
- Cost Estimation
- Policy Enforcement
- terraform login
- VCS Integration
- Remote State
- CLI-driven Runs
- VCS-driven Runs

---

# Recommended Study Order

1. Use HCP Terraform to Create Infrastructure
2. Collaboration and Governance Features
3. Workspaces and Projects
4. HCP Terraform Integration

---

# Objectives Covered

| Objective                     | Status |
| ----------------------------- | ------ |
| 8a Create Infrastructure      | ⬜      |
| 8b Collaboration & Governance | ⬜      |
| 8c Workspaces & Projects      | ⬜      |
| 8d Integrations               | ⬜      |

---

# Domain Completion Checklist

- [ ] Completed 8a
- [ ] Completed 8b
- [ ] Completed 8c
- [ ] Completed 8d
- [ ] Completed Practice Questions
- [ ] Completed Revision Sheet
- [ ] Terraform Associate (004) Exam Ready
