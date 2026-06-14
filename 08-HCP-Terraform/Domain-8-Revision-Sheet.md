# Domain 8 Revision Sheet

## HCP Terraform

### Objectives Covered

- 8a Use HCP Terraform to Create Infrastructure
- 8b Describe HCP Terraform Collaboration and Governance Features
- 8c Describe How to Organize and Use HCP Terraform Workspaces and Projects
- 8d Configure and Use HCP Terraform Integration

---

# What Is HCP Terraform?

HCP Terraform is HashiCorp's managed platform for Terraform.

Provides:

- Remote Execution
- Remote State Storage
- Collaboration
- Governance
- Automation
- Policy Enforcement

---

## Core Idea

Without HCP Terraform:

```text
Developer
      │
      ▼
terraform apply
      │
      ▼
Infrastructure
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
      │
      ▼
Infrastructure
```

---

# Objective 8a

## Use HCP Terraform to Create Infrastructure

---

# Terraform Runs

A Run is:

```text
Terraform Operation
```

Examples:

```text
Plan
Apply
Destroy
```

---

# Run Workflow

```text
Configuration Change
         │
         ▼
Plan
         │
         ▼
Review
         │
         ▼
Apply
         │
         ▼
State Update
```

---

# Remote Execution

Terraform runs execute inside:

```text
HCP Terraform
```

instead of:

```text
Developer Laptop
```

---

## Benefits

✅ Consistency

✅ Security

✅ Collaboration

✅ Governance

---

# Remote State

State stored centrally inside:

```text
Workspace
```

Benefits:

✅ Shared State

✅ Backups

✅ Security

✅ Team Access

---

# Workflow Types

## CLI-Driven

```bash
terraform login
terraform plan
terraform apply
```

---

## VCS-Driven

```text
Git Commit
      │
      ▼
GitHub
      │
      ▼
HCP Terraform Run
```

---

## Exam Favorite

Most common enterprise workflow:

```text
VCS-Driven
```

---

# Objective 8b

## Collaboration & Governance

---

# Teams

Group users together.

Example:

```text
Platform Team
```

```text
Security Team
```

```text
Network Team
```

---

# RBAC

Role-Based Access Control

Controls:

```text
Permissions
```

Examples:

- Read
- Write
- Admin

---

## Exam Memory

```text
RBAC = Permissions
```

---

# Audit Trails

Track:

```text
Who
What
When
```

---

Examples:

```text
Who Applied
Who Approved
Who Modified Variables
```

---

## Exam Memory

```text
Audit Trail = Activity History
```

---

# Sentinel

HashiCorp Policy-as-Code Framework

Purpose:

```text
Enforce Governance
```

---

Examples:

```text
No Public S3 Buckets
```

```text
Approved Regions Only
```

---

## Exam Memory

```text
Sentinel = Policies
```

---

# Cost Estimation

Shows estimated infrastructure cost before deployment.

Purpose:

```text
Cost Visibility
```

---

# Private Module Registry

Stores reusable approved modules.

Examples:

```text
VPC Module
```

```text
EKS Module
```

---

# Variable Sets

Share variables across multiple workspaces.

Example:

```text
AWS_REGION=us-east-1
```

---

## Exam Memory

```text
Variable Sets = Shared Variables
```

---

# Drift Detection

Detects:

```text
Infrastructure Drift
```

---

Definition:

```text
Actual Infrastructure
≠
Terraform State
```

---

# Objective 8c

## Workspaces & Projects

---

# Workspace

Primary operational unit.

Contains:

- State
- Variables
- Outputs
- Runs
- Configuration

---

## Exam Memory

```text
Workspace = Do Work
```

---

# Project

Collection of related workspaces.

Example:

```text
E-Commerce Project
```

Contains:

```text
network-prod
```

```text
app-prod
```

```text
db-prod
```

---

## Exam Memory

```text
Project = Organize Work
```

---

# Workspace Isolation

Each workspace has:

```text
Independent State
Independent Variables
Independent Runs
```

---

# Environment Separation

Common Pattern:

```text
dev
```

↓

```text
staging
```

↓

```text
prod
```

---

# Run Triggers

Automatically start runs in dependent workspaces.

Example:

```text
Network Workspace
```

↓

```text
Apply Success
```

↓

```text
Application Workspace Starts
```

---

# Major Exam Trap

## HCP Workspace

Cloud-based resource.

Contains:

```text
State
Variables
Runs
```

---

## CLI Workspace

Created using:

```bash
terraform workspace new
```

Purpose:

```text
Local State Separation
```

---

## Remember

```text
HCP Workspace
≠
CLI Workspace
```

---

# Objective 8d

## HCP Terraform Integration

---

# terraform login

Authenticate Terraform CLI.

Command:

```bash
terraform login
```

---

## Workflow

```text
Browser Login
       │
       ▼
Token Generated
       │
       ▼
CLI Authenticated
```

---

# Cloud Block

Connects Terraform to HCP Terraform.

Example:

```hcl
terraform {

  cloud {

    organization = "my-org"

    workspaces {

      name = "production"

    }

  }

}
```

---

## Exam Memory

```text
cloud {}
=
HCP Terraform Connection
```

---

# State Migration

Command:

```bash
terraform init
```

Purpose:

```text
Migrate Local State
```

↓

```text
HCP Terraform State
```

---

# VCS Integration

Supported:

- GitHub
- GitLab
- Bitbucket
- Azure DevOps

---

# VCS Workflow

```text
Git Commit
      │
      ▼
Repository
      │
      ▼
HCP Terraform
      │
      ▼
Plan
      │
      ▼
Apply
```

---

# CLI vs VCS Workflow

| Feature          | CLI    | VCS        |
| ---------------- | ------ | ---------- |
| Trigger          | User   | Git Commit |
| Automation       | Lower  | Higher     |
| Enterprise Usage | Medium | High       |
| Most Common      | ❌      | ✅          |

---

# HCP Terraform Feature Map

| Feature          | Purpose                |
| ---------------- | ---------------------- |
| Workspace        | Operational Unit       |
| Project          | Workspace Organization |
| Run              | Terraform Operation    |
| Team             | User Group             |
| RBAC             | Permissions            |
| Sentinel         | Policy Enforcement     |
| Variable Set     | Shared Variables       |
| Audit Trail      | Activity Tracking      |
| Run Trigger      | Workspace Automation   |
| Cost Estimation  | Cost Visibility        |
| Drift Detection  | Drift Monitoring       |
| Private Registry | Module Sharing         |

---

# Workspace vs Project

| Workspace        | Project               |
| ---------------- | --------------------- |
| Stores State     | Contains Workspaces   |
| Executes Runs    | Organizes Workspaces  |
| Stores Variables | Groups Infrastructure |
| Operational Unit | Organizational Unit   |

---

# HCP Workspace vs CLI Workspace

| HCP Workspace      | CLI Workspace   |
| ------------------ | --------------- |
| HCP Feature        | CLI Feature     |
| Cloud-Based        | Local           |
| Stores State       | Separates State |
| Supports Runs      | No Runs         |
| Team Collaboration | Local Usage     |

---

# Top 25 Exam Facts

### HCP Terraform is a managed Terraform platform.

### Runs execute remotely.

### State stored in Workspaces.

### Run = Terraform Operation.

### Plan + Apply are core run phases.

### VCS-driven workflow is most common.

### Teams group users.

### RBAC controls permissions.

### Audit Trails record activity.

### Sentinel enforces policies.

### Policies can block applies.

### Cost Estimation predicts costs.

### Variable Sets share variables.

### Drift Detection identifies drift.

### Private Registry stores modules.

### Workspace is the primary operational unit.

### Project contains Workspaces.

### Workspaces isolate environments.

### Run Triggers automate dependent runs.

### HCP Workspace ≠ CLI Workspace.

### terraform login authenticates CLI.

### cloud block connects Terraform to HCP Terraform.

### terraform init performs state migration.

### GitHub integration supports automated runs.

### HCP Terraform centralizes collaboration and governance.

---

# 60-Second Exam Revision

```text
Workspace
=
State + Variables + Runs
```

---

```text
Project
=
Collection Of Workspaces
```

---

```text
RBAC
=
Permissions
```

---

```text
Audit Trail
=
Who Did What
```

---

```text
Sentinel
=
Policy As Code
```

---

```text
Variable Set
=
Shared Variables
```

---

```text
Run Trigger
=
Automatic Workspace Execution
```

---

```bash
terraform login
```

↓

```text
Authenticate CLI
```

---

```hcl
cloud {}
```

↓

```text
Connect To HCP Terraform
```

---

```bash
terraform init
```

↓

```text
State Migration
```

---

```text
VCS Driven
```

↓

```text
Most Common Enterprise Workflow
```

---

# Domain Completion Checklist

- [ ] Completed 8a Create Infrastructure
- [ ] Completed 8b Collaboration & Governance
- [ ] Completed 8c Workspaces & Projects
- [ ] Completed 8d Integrations
- [ ] Completed Practice Questions
- [ ] Scored 35+/40
- [ ] Reviewed Incorrect Answers
- [ ] Terraform Associate (004) Exam Ready

---

# Terraform Associate (004) Completion Checklist

- [ ] Domain 1 Completed
- [ ] Domain 2 Completed
- [ ] Domain 3 Completed
- [ ] Domain 4 Completed
- [ ] Domain 5 Completed
- [ ] Domain 6 Completed
- [ ] Domain 7 Completed
- [ ] Domain 8 Completed
- [ ] Completed All Practice Questions
- [ ] Completed All Revision Sheets
- [ ] Ready To Schedule Terraform Associate (004) Exam
