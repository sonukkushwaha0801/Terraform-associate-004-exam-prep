# Objective: 8b - Describe HCP Terraform Collaboration and Governance Features

## Definition

HCP Terraform provides collaboration and governance capabilities that enable teams to safely manage infrastructure at scale.

These features help organizations:

- Improve Collaboration
- Enforce Security Controls
- Standardize Deployments
- Maintain Compliance
- Increase Visibility
- Reduce Operational Risk

Unlike local Terraform workflows, HCP Terraform is designed for multi-user and enterprise environments.

---

## Core Concepts

### What Is Collaboration?

Collaboration allows multiple users and teams to work together on infrastructure.

Example:

```text
Developer
      │
      ▼
HCP Terraform Workspace
      │
      ▼
Reviewer
      │
      ▼
Approver
```

Infrastructure changes become visible and manageable across teams.

---

### What Is Governance?

Governance ensures infrastructure follows organizational policies and standards.

Examples:

- Security Policies
- Naming Standards
- Compliance Requirements
- Cost Controls
- Access Controls

---

# Teams

## Definition

Teams are collections of users with shared permissions.

Example:

```text
Network Team
```

```text
Platform Team
```

```text
Security Team
```

---

## Benefits

- Simplified Permission Management
- Role Assignment
- Centralized Access Control

---

# Role-Based Access Control (RBAC)

## Definition

RBAC controls what users can do within HCP Terraform.

Permissions are assigned through roles.

---

## Example

### Read Only

Can:

```text
View Workspaces
```

Cannot:

```text
Apply Changes
```

---

### Write

Can:

```text
Create Runs
Modify Variables
```

---

### Admin

Can:

```text
Manage Workspaces
Manage Teams
Manage Permissions
```

---

## Benefits

- Least Privilege Access
- Improved Security
- Better Governance

---

# Audit Trails

## Definition

HCP Terraform records activity history.

Examples:

```text
Who Created A Run
```

```text
Who Approved A Run
```

```text
Who Modified Variables
```

---

## Benefits

- Accountability
- Compliance
- Troubleshooting

---

# Policy Enforcement

## Definition

Policies automatically evaluate Terraform runs.

Purpose:

```text
Prevent Non-Compliant Infrastructure
```

---

## Example

Organization Rule:

```text
No Public S3 Buckets
```

Terraform Plan:

```text
Creates Public Bucket
```

Result:

```text
Policy Fails
```

Apply Blocked.

---

# Sentinel

## Definition

Sentinel is HashiCorp's policy-as-code framework.

Used to enforce governance rules.

---

## Example Policies

### Security

```text
No Public Resources
```

---

### Compliance

```text
Approved Regions Only
```

---

### Cost Control

```text
Restrict Large Instances
```

---

# Cost Estimation

## Definition

Estimates infrastructure cost before deployment.

---

## Example

Terraform Plan:

```text
5 EC2 Instances
```

Cost Estimation:

```text
Monthly Cost Projection
```

shown before approval.

---

## Benefits

- Cost Awareness
- Budget Control
- Change Visibility

---

# Private Module Registry

## Definition

Organizations can publish reusable Terraform modules.

Example:

```text
Approved VPC Module
```

```text
Approved EKS Module
```

---

## Benefits

- Standardization
- Reusability
- Reduced Duplication

---

# Variable Sets

## Definition

Variable Sets allow variables to be shared across multiple workspaces.

---

## Example

Shared Variable:

```text
AWS_REGION=us-east-1
```

Instead of defining it repeatedly:

```text
Workspace A
Workspace B
Workspace C
```

Use:

```text
Variable Set
```

---

## Benefits

- Centralized Management
- Consistency
- Reduced Duplication

---

# Drift Detection

## Definition

HCP Terraform can identify infrastructure drift.

Drift occurs when:

```text
Actual Infrastructure
≠
Terraform State
```

---

## Example

AWS Console Change:

```text
Instance Type Modified
```

HCP Terraform:

```text
Detects Drift
```

---

# Health Assessments

## Definition

Evaluates workspace health.

Monitors:

- Drift
- Failed Runs
- Operational Status

---

# Collaboration Workflow

```text
Developer
      │
      ▼
Git Commit
      │
      ▼
Workspace Run
      │
      ▼
Policy Checks
      │
      ▼
Review
      │
      ▼
Apply
```

---

# Governance Workflow

```text
Terraform Plan
       │
       ▼
Policy Evaluation
       │
       ▼
Pass
       │
       ▼
Apply Allowed
```

or

```text
Terraform Plan
       │
       ▼
Policy Evaluation
       │
       ▼
Fail
       │
       ▼
Apply Blocked
```

---

# Terraform Perspective

Local Terraform:

```text
Minimal Governance
```

---

HCP Terraform:

```text
Teams
RBAC
Policies
Auditing
Cost Controls
```

---

# Real-World Example

Enterprise:

```text
100 Engineers
```

Requirements:

- Access Control
- Compliance
- Auditability

HCP Terraform provides:

- RBAC
- Sentinel
- Audit Trails
- Policy Enforcement

---

# Production Use Cases

Organizations use HCP Terraform governance features for:

- Regulatory Compliance
- Security Standards
- Multi-Team Collaboration
- Cost Management
- Infrastructure Standardization

---

# Important Exam Points

- Teams simplify permission management.
- RBAC controls access.
- Audit Trails track activity.
- Sentinel provides policy-as-code.
- Policies can block deployments.
- Cost Estimation predicts deployment costs.
- Private Registry stores reusable modules.
- Variable Sets share variables across workspaces.
- Drift Detection identifies infrastructure drift.
- Governance improves security and compliance.

---

# Common Exam Traps

### Trap 1

Question:

What feature enforces organizational policies?

Correct:

```text
Sentinel
```

---

### Trap 2

Question:

What controls user permissions?

Correct:

```text
RBAC
```

---

### Trap 3

Question:

What records user activity?

Correct:

```text
Audit Trails
```

---

### Trap 4

Question:

What shares variables across workspaces?

Correct:

```text
Variable Sets
```

---

### Trap 5

Question:

Can policies block applies?

Correct:

```text
Yes
```

---

### Trap 6

Question:

What feature estimates deployment cost?

Correct:

```text
Cost Estimation
```

---

# Interview Questions

### What is RBAC?

Role-Based Access Control used to manage permissions.

### What is Sentinel?

HashiCorp's policy-as-code framework.

### What are Variable Sets?

Shared variables used across multiple workspaces.

### What is Drift Detection?

Detection of infrastructure changes outside Terraform.

### What is the purpose of Audit Trails?

Track user actions and infrastructure changes.

---

# Practice Questions

### Question 1

What feature controls user permissions?

A. Variable Sets

B. Sentinel

C. RBAC

D. Workspaces

**Answer:** C

---

### Question 2

What is Sentinel?

A. State Backend

B. Policy-as-Code Framework

C. Module Registry

D. Workspace Type

**Answer:** B

---

### Question 3

What feature records user activity?

A. Audit Trails

B. Workspaces

C. Variable Sets

D. Outputs

**Answer:** A

---

### Question 4

What feature allows variables to be shared across workspaces?

A. Outputs

B. Projects

C. Variable Sets

D. Teams

**Answer:** C

---

### Question 5

Can Sentinel policies prevent an apply operation?

A. No

B. Yes

**Answer:** B

---

## Related Objectives

- 8a Use HCP Terraform to Create Infrastructure
- 8c Workspaces and Projects
- 8d HCP Terraform Integration

---

## Key Takeaways

- Teams enable collaboration.
- RBAC controls permissions.
- Audit Trails provide accountability.
- Sentinel enforces governance policies.
- Policies can block non-compliant deployments.
- Cost Estimation predicts infrastructure costs.
- Variable Sets centralize shared variables.
- Drift Detection identifies infrastructure drift.
- Governance features are a major benefit of HCP Terraform.
