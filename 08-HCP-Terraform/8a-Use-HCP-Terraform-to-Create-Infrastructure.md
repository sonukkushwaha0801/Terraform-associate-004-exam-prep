# Objective: 8a - Use HCP Terraform to Create Infrastructure

## Definition

HCP Terraform is HashiCorp's managed platform for provisioning, managing, and operating infrastructure using Terraform.

It enables teams to execute Terraform remotely while providing:

- Centralized State Management
- Collaboration
- Governance
- Security
- Automation

Instead of running Terraform entirely from a local machine, Terraform operations can be executed within HCP Terraform.

---

## Core Concepts

### What Is HCP Terraform?

HCP Terraform is a Software-as-a-Service (SaaS) platform that manages Terraform workflows.

It provides:

- Remote Execution
- State Management
- Team Collaboration
- Policy Enforcement
- Audit Trails
- VCS Integration

---

## Traditional Terraform Workflow

Without HCP Terraform:

```text
Developer Laptop
       │
       ▼
terraform plan
terraform apply
       │
       ▼
Cloud Provider
```

Problems:

- Local State
- Credential Management
- Limited Collaboration
- Lack of Governance

---

## HCP Terraform Workflow

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
Cloud Provider
```

Benefits:

- Centralized Operations
- Shared State
- Team Collaboration
- Governance Controls

---

# HCP Terraform Architecture

## Components

### Users

Developers interact with HCP Terraform.

---

### Workspaces

Contain:

- Terraform Configuration
- Variables
- State
- Run History

---

### Runs

Represent Terraform operations.

Examples:

```text
Plan
Apply
Destroy
```

---

### State Storage

State stored centrally by HCP Terraform.

---

### Integrations

Examples:

- GitHub
- GitLab
- Bitbucket
- Azure DevOps

---

# Creating Infrastructure with HCP Terraform

Typical workflow:

```text
Terraform Code
      │
      ▼
Workspace
      │
      ▼
Plan
      │
      ▼
Apply
      │
      ▼
Infrastructure Created
```

---

# Terraform Runs

## Definition

A run is a Terraform operation executed within HCP Terraform.

Examples:

```text
Plan Run
Apply Run
Destroy Run
```

---

## Run Workflow

```text
Configuration Change
          │
          ▼
Run Created
          │
          ▼
Plan Generated
          │
          ▼
Review
          │
          ▼
Apply
          │
          ▼
State Updated
```

---

# Plan Phase

Terraform evaluates:

```text
Current State
vs
Desired State
```

Output:

```text
Execution Plan
```

---

# Apply Phase

Terraform performs:

```text
Create
Modify
Destroy
```

operations.

Infrastructure changes occur here.

---

# Remote Execution

## Definition

Terraform runs execute inside HCP Terraform instead of the local machine.

---

## Example

Local Workflow:

```bash
terraform apply
```

runs on:

```text
Developer Laptop
```

---

HCP Workflow:

```text
terraform apply
```

runs on:

```text
HCP Terraform Workers
```

---

## Benefits

### Consistency

Same execution environment.

---

### Security

Credentials remain centralized.

---

### Collaboration

Everyone uses the same execution platform.

---

### Governance

Policies can be enforced before deployment.

---

# Remote State Management

## Definition

HCP Terraform stores state centrally.

Example:

```text
Workspace
      │
      ▼
Terraform State
```

---

## Benefits

- Shared State
- Automatic Backups
- Security
- Team Access

---

# CLI-Driven Workflow

Developers use:

```bash
terraform login
```

to authenticate.

---

## Example Workflow

```bash
terraform login
```

↓

```bash
terraform init
```

↓

```bash
terraform plan
```

↓

```bash
terraform apply
```

Runs execute through HCP Terraform.

---

# VCS-Driven Workflow

Most common enterprise workflow.

---

## Example

```text
Git Commit
      │
      ▼
GitHub
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

## Benefits

- Automation
- Version Control
- Review Process
- Auditability

---

# Local vs HCP Terraform

| Feature       | Local Terraform | HCP Terraform |
| ------------- | --------------- | ------------- |
| State Storage | Local/Backend   | Managed       |
| Execution     | Local Machine   | Remote        |
| Collaboration | Limited         | Built-In      |
| Governance    | Limited         | Strong        |
| Audit Trail   | No              | Yes           |
| Team Support  | Basic           | Enterprise    |

---

# Terraform Perspective

Without HCP Terraform:

```text
User
  │
  ▼
Terraform CLI
  │
  ▼
Infrastructure
```

---

With HCP Terraform:

```text
User
  │
  ▼
HCP Terraform
  │
  ▼
Runs
Policies
State
  │
  ▼
Infrastructure
```

---

# Real-World Example

Company:

```text
50 Engineers
```

Infrastructure:

- AWS
- Azure
- Kubernetes

All Terraform runs occur in:

```text
HCP Terraform
```

Benefits:

- Consistent Deployments
- Shared State
- Governance Controls

---

# Production Use Case

Organizations use HCP Terraform for:

- Multi-Team Collaboration
- Compliance
- Security
- Centralized Operations
- Infrastructure Automation

---

# Important Exam Points

- HCP Terraform is a managed Terraform platform.
- Supports remote execution.
- Stores state centrally.
- Uses workspaces to manage infrastructure.
- Runs consist of Plan and Apply phases.
- Supports CLI-driven workflows.
- Supports VCS-driven workflows.
- Improves collaboration and governance.

---

# Common Exam Traps

### Trap 1

Question:

Where do Terraform runs execute in HCP Terraform?

Correct:

```text
Remote Execution Environment
```

---

### Trap 2

Question:

Where is state stored?

Correct:

```text
HCP Terraform
```

---

### Trap 3

Question:

What is a run?

Correct:

```text
Terraform Operation
```

---

### Trap 4

Question:

Most common enterprise workflow?

Correct:

```text
VCS-Driven Workflow
```

---

### Trap 5

Question:

Does HCP Terraform support local execution only?

Correct:

```text
No
```

---

# Interview Questions

### What is HCP Terraform?

A managed platform for operating Terraform workflows.

### What is remote execution?

Terraform runs execute within HCP Terraform instead of a local machine.

### What is a Terraform run?

A plan, apply, or destroy operation executed by HCP Terraform.

### What are the benefits of HCP Terraform?

Collaboration, governance, centralized state, and automation.

### What workflow is most common in enterprises?

VCS-driven workflow.

---

# Practice Questions

### Question 1

What is HCP Terraform?

A. A Cloud Provider

B. A Managed Terraform Platform

C. A Kubernetes Distribution

D. A Configuration Language

**Answer:** B

---

### Question 2

Where does Terraform execution occur when remote execution is enabled?

A. Developer Laptop

B. Cloud Provider

C. HCP Terraform

D. GitHub

**Answer:** C

---

### Question 3

What is a Terraform run?

A. Variable Set

B. Terraform Operation

C. Provider Plugin

D. Backend

**Answer:** B

---

### Question 4

Which workflow is most common for enterprises?

A. Manual Workflow

B. Spreadsheet Workflow

C. VCS-Driven Workflow

D. SSH Workflow

**Answer:** C

---

### Question 5

What is a primary benefit of HCP Terraform?

A. Smaller Terraform Files

B. Centralized State and Collaboration

C. Faster Internet

D. Fewer Resources

**Answer:** B

---

## Related Objectives

- 8b Collaboration and Governance Features
- 8c Workspaces and Projects
- 8d HCP Terraform Integrations

---

## Key Takeaways

- HCP Terraform is HashiCorp's managed Terraform platform.
- Supports remote execution.
- Stores state centrally.
- Uses runs to execute Terraform operations.
- Supports CLI-driven and VCS-driven workflows.
- Improves collaboration, security, and governance.
- Commonly used in enterprise Terraform environments.
