# Objective: 2d - Explain How Terraform Uses and Manages State

## Definition

Terraform state is a snapshot of infrastructure that Terraform manages.

State allows Terraform to map resources defined in configuration files to real-world infrastructure resources.

Without state, Terraform would not know:

* What resources exist
* Which resources it manages
* What changes are required

Terraform stores state in a state file called:

```text
terraform.tfstate
```

---

## Core Concepts

### State File

Terraform stores infrastructure information inside:

```text
terraform.tfstate
```

This file contains:

* Managed resources
* Resource attributes
* Metadata
* Resource relationships

---

### Current State

The current infrastructure Terraform believes exists.

Stored in:

```text
terraform.tfstate
```

---

### Desired State

The infrastructure defined in Terraform configuration files.

Example:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

---

### State Mapping

Terraform uses state to map:

```text
Terraform Configuration
          │
          ▼
Terraform State
          │
          ▼
Real Infrastructure
```

---

### Resource Tracking

Terraform tracks resources using unique identifiers.

Example:

```text
aws_instance.web
```

Terraform knows:

* Resource exists
* Resource location
* Resource attributes

---

## How It Works

Terraform workflow:

### Step 1

Read Configuration

```text
main.tf
```

---

### Step 2

Read State

```text
terraform.tfstate
```

---

### Step 3

Compare

```text
Current State
      vs
Desired State
```

---

### Step 4

Create Execution Plan

```bash
terraform plan
```

---

### Step 5

Apply Changes

```bash
terraform apply
```

---

### Step 6

Update State

Terraform updates:

```text
terraform.tfstate
```

to reflect infrastructure changes.

---

## Terraform Perspective

Example:

Current State:

```text
EC2 Instance
instance_type = t2.micro
```

Desired State:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Terraform detects:

```text
State Difference
```

and generates an execution plan.

---

## Why Terraform Uses State

Without state:

Terraform would need to query every resource every time.

This would be:

* Slow
* Expensive
* Unreliable

State provides a cached representation of managed infrastructure.

---

## Real-World Example

A company manages:

* 500 EC2 Instances
* 200 Security Groups
* 50 Load Balancers

Terraform stores resource information in state.

When:

```bash
terraform plan
```

runs, Terraform quickly determines what must change.

---

## Production Use Case

A platform engineering team manages thousands of cloud resources.

Terraform state enables:

* Fast planning
* Resource tracking
* Change detection
* Dependency tracking

Without state, infrastructure management would become inefficient and error-prone.

---

## Command Reference

### Show State Resources

```bash
terraform state list
```

---

### Show Resource Details

```bash
terraform state show aws_instance.web
```

---

### Pull State

```bash
terraform state pull
```

---

### Refresh State Information

```bash
terraform refresh
```

Note:

Modern Terraform automatically refreshes state during planning and applying operations.

---

## Important Exam Points

* Terraform uses state to track infrastructure.
* Default state file name is terraform.tfstate.
* State maps configuration to real infrastructure.
* Terraform compares current state and desired state.
* State enables change detection.
* State improves performance.
* Terraform updates state after apply.
* State is critical to Terraform operations.

---

## Common Exam Traps

### Trap 1

Question:

Why does Terraform use state?

Correct:

To track managed infrastructure.

---

### Trap 2

Question:

What file stores Terraform state?

Correct:

```text
terraform.tfstate
```

---

### Trap 3

Question:

What does Terraform compare during planning?

Correct:

Current State vs Desired State

---

### Trap 4

Question:

Does Terraform update state after apply?

Correct:

Yes.

---

### Trap 5

Question:

Can Terraform operate without state?

Correct:

No.

State is a fundamental Terraform component.

---

## Interview Questions

### What is Terraform state?

A snapshot of infrastructure managed by Terraform.

### Why is Terraform state required?

Terraform uses state to track resources and determine infrastructure changes.

### What is the default state file name?

```text
terraform.tfstate
```

### What happens during terraform plan?

Terraform compares current state and desired state.

### Why is state important in large environments?

It improves performance and enables efficient resource tracking.

---

## Practice Questions

### Question 1

What is the primary purpose of Terraform state?

A. Store Variables

B. Store Outputs

C. Track Managed Infrastructure

D. Store Modules

**Answer:** C

**Explanation:** Terraform state tracks infrastructure resources managed by Terraform.

---

### Question 2

What is the default Terraform state file name?

A. terraform.state

B. terraform.tfstate

C. state.tf

D. terraform.json

**Answer:** B

**Explanation:** Terraform stores state in terraform.tfstate by default.

---

### Question 3

Terraform compares which two things during planning?

A. Variables and Outputs

B. Providers and Resources

C. Current State and Desired State

D. Modules and Providers

**Answer:** C

**Explanation:** Terraform determines required changes by comparing current and desired state.

---

### Question 4

When is Terraform state updated?

A. During validate

B. During fmt

C. After successful apply operations

D. During provider installation

**Answer:** C

**Explanation:** Terraform updates state after infrastructure changes are applied.

---

### Question 5

Which command lists resources stored in Terraform state?

A. terraform providers

B. terraform state list

C. terraform output

D. terraform graph

**Answer:** B

**Explanation:** terraform state list displays resources tracked in state.

---

## Related Objectives

* 3d Generate and Review an Execution Plan
* 3e Apply Changes to Infrastructure
* 6a Describe the Local Backend
* 6b Describe State Locking
* 6c Configure Remote State Using the Backend Block
* 6d Manage Resource Drift and Terraform State
* 7b Use the CLI to Inspect State

---

## Key Takeaways

* Terraform state tracks infrastructure.
* Default state file is terraform.tfstate.
* Terraform compares current state and desired state.
* State maps configuration to infrastructure.
* State improves performance.
* State is updated after apply operations.
* Understanding state is essential for mastering Terraform.
