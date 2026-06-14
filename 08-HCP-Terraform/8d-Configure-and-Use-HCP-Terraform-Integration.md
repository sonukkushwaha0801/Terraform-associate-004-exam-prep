# Objective: 8d - Configure and Use HCP Terraform Integration

## Definition

HCP Terraform integrates with:

- Terraform CLI
- Version Control Systems (VCS)
- Cloud Providers
- Remote State Management
- Team Workflows

These integrations enable centralized infrastructure management, collaboration, and automation.

This objective focuses on connecting Terraform configurations and workflows to HCP Terraform.

---

## Core Concepts

### Why Integrations Matter

Without HCP Terraform:

```text
Developer
      │
      ▼
Local Terraform
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
Runs
State
Policies
Collaboration
      │
      ▼
Cloud Infrastructure
```

Integrations enable this workflow.

---

# Terraform CLI Integration

## terraform login

Used to authenticate the Terraform CLI with HCP Terraform.

---

## Command

```bash
terraform login
```

---

## What Happens?

Terraform:

```text
Opens Browser
```

↓

```text
User Authenticates
```

↓

```text
API Token Generated
```

↓

```text
Credentials Stored Locally
```

---

## Purpose

Allows Terraform CLI to communicate with:

```text
HCP Terraform
```

---

# Authentication Workflow

```text
terraform login
        │
        ▼
Browser Authentication
        │
        ▼
Token Issued
        │
        ▼
CLI Authenticated
```

---

# Cloud Block

## Definition

The cloud block connects Terraform configurations to HCP Terraform.

---

## Example

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

## Purpose

Tells Terraform:

```text
Use HCP Terraform
```

for:

- State Management
- Runs
- Collaboration

---

# Cloud Block Components

## organization

Specifies:

```text
HCP Terraform Organization
```

---

## workspace

Specifies:

```text
Target Workspace
```

---

# Example Workflow

```text
Terraform Configuration
         │
         ▼
Cloud Block
         │
         ▼
HCP Workspace
```

---

# Remote Execution Configuration

When a cloud block exists:

Terraform can execute remotely.

---

## Example

```bash
terraform apply
```

Instead of:

```text
Local Execution
```

Terraform uses:

```text
HCP Terraform Run Environment
```

---

# Remote State Integration

HCP Terraform automatically stores:

```text
Terraform State
```

within workspaces.

Benefits:

- Centralization
- Security
- Collaboration

---

# State Migration

Organizations often migrate from:

```text
Local State
```

to:

```text
HCP Terraform State
```

---

## Migration Workflow

```text
Local State
       │
       ▼
Cloud Block Added
       │
       ▼
terraform init
       │
       ▼
State Migration
```

---

## Command

```bash
terraform init
```

Terraform prompts:

```text
Copy Existing State?
```

---

Answer:

```text
Yes
```

State migrates automatically.

---

# VCS Integration

## Definition

Connects HCP Terraform to source code repositories.

---

## Supported Systems

- GitHub
- GitLab
- Bitbucket
- Azure DevOps

---

# GitHub Workflow

```text
Git Commit
      │
      ▼
GitHub Repository
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

# Benefits

- Automation
- Version Control
- Change Tracking
- Collaboration

---

# VCS-Driven Workflow

## Definition

Terraform runs start automatically after repository changes.

---

## Example

```text
Developer Pushes Code
```

↓

```text
GitHub Webhook
```

↓

```text
HCP Terraform Run
```

↓

```text
Plan
```

↓

```text
Apply
```

---

# CLI-Driven Workflow

## Definition

Terraform commands initiated directly from the CLI.

---

## Example

```bash
terraform login
```

↓

```bash
terraform plan
```

↓

```bash
terraform apply
```

---

Runs still occur within:

```text
HCP Terraform
```

---

# CLI-Driven vs VCS-Driven

| Feature                    | CLI-Driven | VCS-Driven |
| -------------------------- | ---------- | ---------- |
| Trigger Source             | CLI        | Git Commit |
| Automation                 | Lower      | Higher     |
| Enterprise Usage           | Moderate   | High       |
| Version Control Dependency | No         | Yes        |
| Most Common                | No         | Yes        |

---

## Exam Favorite

Question:

Which workflow is most common in enterprise environments?

Answer:

```text
VCS-Driven Workflow
```

---

# Run Triggers

## Definition

Automatically trigger runs in dependent workspaces.

---

## Example

```text
Network Workspace
```

↓

```text
Apply Successful
```

↓

```text
Application Workspace Run Starts
```

---

# Terraform Perspective

Local Terraform:

```text
Developer Controlled
```

---

HCP Terraform:

```text
Integrated
Automated
Collaborative
```

---

# Real-World Example

Organization:

```text
GitHub
```

+

```text
HCP Terraform
```

Workflow:

```text
Pull Request
      │
      ▼
Plan
      │
      ▼
Review
      │
      ▼
Apply
```

All infrastructure changes follow a standardized process.

---

# Production Use Cases

Organizations use integrations for:

- GitOps
- Automation
- Governance
- CI/CD Pipelines
- Infrastructure Standardization

---

# Important Exam Points

- terraform login authenticates Terraform CLI.
- Cloud block connects Terraform to HCP Terraform.
- HCP Terraform supports remote execution.
- HCP Terraform stores state centrally.
- terraform init can migrate state.
- VCS integrations support GitHub, GitLab, Bitbucket, and Azure DevOps.
- VCS-driven workflows are common in enterprises.
- CLI-driven workflows are also supported.
- Run Triggers automate dependent runs.

---

# Common Exam Traps

### Trap 1

Question:

Which command authenticates Terraform CLI with HCP Terraform?

Correct:

```bash
terraform login
```

---

### Trap 2

Question:

What block connects Terraform to HCP Terraform?

Correct:

```hcl
cloud {}
```

---

### Trap 3

Question:

Which command migrates state after adding a cloud block?

Correct:

```bash
terraform init
```

---

### Trap 4

Question:

Which workflow is most common for enterprises?

Correct:

```text
VCS-Driven Workflow
```

---

### Trap 5

Question:

Can HCP Terraform execute Terraform runs remotely?

Correct:

```text
Yes
```

---

### Trap 6

Question:

Where is state stored when using HCP Terraform?

Correct:

```text
Workspace State
```

---

# Interview Questions

### What does terraform login do?

Authenticates the Terraform CLI with HCP Terraform.

### What is the purpose of the cloud block?

Connects Terraform configurations to HCP Terraform.

### What command migrates local state?

terraform init

### What is a VCS-driven workflow?

A workflow where Git commits automatically trigger Terraform runs.

### Which workflow is most common in enterprises?

VCS-driven workflow.

---

# Practice Questions

### Question 1

Which command authenticates Terraform CLI with HCP Terraform?

A. terraform auth

B. terraform login

C. terraform connect

D. terraform init

**Answer:** B

---

### Question 2

Which block connects Terraform to HCP Terraform?

A. provider

B. backend

C. cloud

D. resource

**Answer:** C

---

### Question 3

Which command commonly performs state migration after adding a cloud block?

A. terraform validate

B. terraform fmt

C. terraform init

D. terraform graph

**Answer:** C

---

### Question 4

Which workflow automatically starts runs after Git commits?

A. CLI-Driven Workflow

B. Manual Workflow

C. VCS-Driven Workflow

D. Workspace Workflow

**Answer:** C

---

### Question 5

Which system is commonly integrated with HCP Terraform?

A. GitHub

B. GitLab

C. Bitbucket

D. All of the Above

**Answer:** D

---

## Related Objectives

- 8a Use HCP Terraform to Create Infrastructure
- 8b Collaboration and Governance Features
- 8c Workspaces and Projects

---

## Key Takeaways

- `terraform login` authenticates the Terraform CLI.
- The `cloud` block connects Terraform to HCP Terraform.
- HCP Terraform supports remote execution.
- State can be migrated using `terraform init`.
- VCS integrations automate Terraform workflows.
- VCS-driven workflows are common in enterprise environments.
- CLI-driven workflows are also supported.
- Run Triggers automate workspace dependencies.
- Integrations are foundational to HCP Terraform operations.
