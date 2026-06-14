# Objective: 8c - Describe How to Organize and Use HCP Terraform Workspaces and Projects

## Definition

HCP Terraform uses Workspaces and Projects to organize infrastructure and Terraform workflows.

These organizational units help teams:

- Separate Environments
- Manage Infrastructure at Scale
- Control Access
- Group Related Resources
- Improve Visibility

Understanding Workspaces and Projects is one of the most heavily tested HCP Terraform topics.

---

## Core Concepts

### What Is a Workspace?

A workspace is the primary working unit in HCP Terraform.

A workspace contains:

- Terraform Configuration
- Terraform State
- Variables
- Run History
- Outputs
- Settings

Think of a workspace as:

```text
A Container For Terraform Operations
```

---

## Workspace Example

```text
production-network
```

Contains:

```text
Terraform Code
Terraform State
Variables
Run History
```

for the production network infrastructure.

---

# Workspace Architecture

```text
Workspace
     │
     ├── Terraform Configuration
     │
     ├── State
     │
     ├── Variables
     │
     ├── Outputs
     │
     └── Run History
```

---

# Why Workspaces Exist

Without workspaces:

```text
All Infrastructure
One Location
```

Becomes difficult to manage.

---

With workspaces:

```text
Dev Workspace

Test Workspace

Prod Workspace
```

Each environment remains isolated.

---

# Workspace Isolation

Every workspace has:

- Independent State
- Independent Variables
- Independent Runs
- Independent Outputs

Example:

```text
dev-network
```

State:

```text
dev.tfstate
```

---

```text
prod-network
```

State:

```text
prod.tfstate
```

Completely separate.

---

# Environment Separation

Common Structure:

```text
Development
```

↓

```text
Testing
```

↓

```text
Production
```

Example:

```text
network-dev
network-test
network-prod
```

Each environment uses a separate workspace.

---

# Workspace Runs

Terraform runs occur within a workspace.

Example:

```text
Workspace
      │
      ▼
Plan
      │
      ▼
Apply
```

All run history remains associated with the workspace.

---

# Workspace Variables

Each workspace can have:

- Terraform Variables
- Environment Variables

Example:

```text
instance_type=t3.micro
```

stored inside a workspace.

---

# What Is a Project?

## Definition

A project is a collection of related workspaces.

Projects provide higher-level organization.

---

## Example

Project:

```text
E-Commerce Platform
```

Contains:

```text
network-prod
```

```text
app-prod
```

```text
database-prod
```

All related workspaces grouped together.

---

# Project Hierarchy

```text
Project
      │
      ├── Workspace A
      │
      ├── Workspace B
      │
      └── Workspace C
```

---

# Why Projects Exist

Projects improve:

- Organization
- Visibility
- Access Management
- Infrastructure Ownership

---

# Workspace vs Project

| Workspace                | Project                       |
| ------------------------ | ----------------------------- |
| Contains Terraform State | Contains Workspaces           |
| Executes Runs            | Organizes Workspaces          |
| Stores Variables         | Groups Related Infrastructure |
| Operational Unit         | Organizational Unit           |

---

## Exam Memory Trick

```text
Workspace = Do Work
```

```text
Project = Organize Work
```

---

# Variable Sets

Projects and workspaces can use:

```text
Variable Sets
```

to share common variables.

Example:

```text
AWS_REGION=us-east-1
```

Shared across multiple workspaces.

---

# Run Triggers

## Definition

Run triggers automatically start runs in another workspace.

---

## Example

Network Workspace:

```text
Applied Successfully
```

↓

Application Workspace:

```text
Automatically Starts
```

---

## Benefits

- Dependency Management
- Workflow Automation
- Infrastructure Coordination

---

# Workspace Relationships

Example:

```text
network
```

↓

```text
security
```

↓

```text
application
```

Workspaces may depend on one another.

Run triggers help coordinate deployments.

---

# Workspace Creation Workflow

```text
Create Workspace
        │
        ▼
Connect Configuration
        │
        ▼
Configure Variables
        │
        ▼
Run Plan
        │
        ▼
Apply
```

---

# Workspace Types

Common organizational approach:

```text
dev
```

```text
staging
```

```text
prod
```

---

Example:

```text
network-dev
```

```text
network-staging
```

```text
network-prod
```

---

# Major Exam Trap

## HCP Terraform Workspace

```text
Cloud Workspace
```

Contains:

- State
- Variables
- Runs

---

## Terraform CLI Workspace

Created using:

```bash
terraform workspace new
```

Purpose:

```text
Local State Separation
```

---

These are NOT the same thing.

---

# HCP Workspace vs CLI Workspace

| HCP Workspace         | CLI Workspace         |
| --------------------- | --------------------- |
| HCP Terraform Feature | Terraform CLI Feature |
| Stores State          | Separates Local State |
| Supports Runs         | No Remote Runs        |
| Team Collaboration    | Local Usage           |
| Cloud-Based           | CLI-Based             |

---

## Exam Favorite

Question:

Are HCP Terraform Workspaces and Terraform CLI Workspaces the same?

Answer:

```text
No
```

---

# Terraform Perspective

```text
Project
     │
     ▼
Workspace
     │
     ▼
Terraform Runs
     │
     ▼
Infrastructure
```

---

# Real-World Example

Company:

```text
E-Commerce Platform
```

Project:

```text
ecommerce
```

Workspaces:

```text
network-prod
```

```text
application-prod
```

```text
database-prod
```

Everything organized under one project.

---

# Production Use Case

Organizations use:

Projects for:

- Ownership
- Organization
- Visibility

Workspaces for:

- Environment Isolation
- Terraform Execution
- State Management

---

# Important Exam Points

- Workspace is the primary operational unit.
- Workspace contains state, variables, runs, and configuration.
- Project groups related workspaces.
- Workspaces isolate environments.
- Variable Sets can be shared across workspaces.
- Run Triggers automate dependent workflows.
- Projects improve organization.
- HCP Workspaces and CLI Workspaces are different concepts.

---

# Common Exam Traps

### Trap 1

Question:

What stores Terraform state?

Correct:

```text
Workspace
```

---

### Trap 2

Question:

What contains workspaces?

Correct:

```text
Project
```

---

### Trap 3

Question:

What groups related infrastructure?

Correct:

```text
Project
```

---

### Trap 4

Question:

Can workspaces isolate environments?

Correct:

```text
Yes
```

---

### Trap 5

Question:

What automates runs between workspaces?

Correct:

```text
Run Triggers
```

---

### Trap 6

Question:

Are HCP Workspaces and CLI Workspaces identical?

Correct:

```text
No
```

---

# Interview Questions

### What is an HCP Terraform Workspace?

The primary unit used to manage Terraform infrastructure.

### What does a workspace contain?

State, variables, runs, outputs, and configuration.

### What is a Project?

A collection of related workspaces.

### Why use Projects?

To organize infrastructure and ownership.

### What are Run Triggers?

Mechanisms that automatically start runs in dependent workspaces.

---

# Practice Questions

### Question 1

What is the primary unit used to manage Terraform infrastructure in HCP Terraform?

A. Team

B. Project

C. Workspace

D. Policy

**Answer:** C

---

### Question 2

What does a Project contain?

A. Providers

B. Workspaces

C. Variables

D. Outputs

**Answer:** B

---

### Question 3

Which feature helps automate runs between workspaces?

A. Variable Sets

B. Audit Trails

C. Run Triggers

D. Outputs

**Answer:** C

---

### Question 4

What is the primary purpose of a Project?

A. Execute Terraform Runs

B. Store State

C. Organize Related Workspaces

D. Store Variables

**Answer:** C

---

### Question 5

Are HCP Terraform Workspaces the same as Terraform CLI Workspaces?

A. Yes

B. No

**Answer:** B

---

## Related Objectives

- 8a Use HCP Terraform to Create Infrastructure
- 8b Collaboration and Governance Features
- 8d Configure and Use HCP Terraform Integration

---

## Key Takeaways

- Workspaces are the primary operational unit in HCP Terraform.
- Workspaces contain state, variables, runs, outputs, and configuration.
- Projects organize related workspaces.
- Workspaces provide environment isolation.
- Variable Sets can be shared across multiple workspaces.
- Run Triggers automate dependent workspace workflows.
- HCP Workspaces and CLI Workspaces are different concepts.
- Workspace vs Project is a frequently tested exam topic.
