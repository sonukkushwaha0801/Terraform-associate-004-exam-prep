# Objective: 3d - Generate and Review an Execution Plan for Terraform

## Definition

An execution plan is Terraform's preview of the actions it will perform to make infrastructure match the desired configuration.

Execution plans are generated using:

```bash
terraform plan
```

Before modifying infrastructure, Terraform compares:

```text
Current State
      vs
Desired State
```

and determines what actions are required.

The execution plan allows users to review changes before they are applied.

---

## Core Concepts

### Execution Plan

An execution plan describes:

* Resources to Create
* Resources to Modify
* Resources to Destroy

Terraform does not make changes during planning.

---

### Desired State

Infrastructure defined in Terraform configuration files.

Example:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

---

### Current State

Infrastructure recorded in:

```text
terraform.tfstate
```

Terraform uses state to understand existing infrastructure.

---

### Plan Review

Execution plans should always be reviewed before applying changes.

Benefits:

* Detect mistakes
* Prevent outages
* Prevent accidental deletions
* Improve deployment safety

---

## How It Works

Terraform planning workflow:

```text
Read Configuration
        │
        ▼
Read State
        │
        ▼
Compare Current vs Desired State
        │
        ▼
Determine Changes
        │
        ▼
Generate Execution Plan
```

---

## Terraform Perspective

Configuration:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Current State:

```text
Instance does not exist
```

Plan:

```bash
terraform plan
```

Output:

```text
+ aws_instance.web
```

Terraform plans to create the resource.

---

## Plan Symbols

### Create

```text
+
```

Example:

```text
+ aws_instance.web
```

Meaning:

```text
Terraform will create a resource.
```

---

### Update

```text
~
```

Example:

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

Meaning:

```text
Terraform will modify a resource.
```

---

### Destroy

```text
-
```

Example:

```text
- aws_instance.web
```

Meaning:

```text
Terraform will destroy a resource.
```

---

### Replace

```text
-/+
```

Meaning:

```text
Destroy and recreate resource.
```

Terraform cannot perform an in-place update.

---

## Real-World Example

Current:

```text
EC2 Instance
t2.micro
```

Desired:

```text
EC2 Instance
t3.micro
```

Execution Plan:

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

Terraform detects and displays the modification before applying it.

---

## Production Use Case

Production deployment workflow:

```text
Developer Changes Configuration
            │
            ▼
terraform fmt
            │
            ▼
terraform validate
            │
            ▼
terraform plan
            │
            ▼
Review Plan
            │
            ▼
terraform apply
```

Organizations often require approval before applying plans.

---

## Saved Execution Plans

Terraform can save a plan:

```bash
terraform plan -out=tfplan
```

Purpose:

* Review changes
* Apply exact approved plan
* Improve deployment consistency

---

### Apply Saved Plan

```bash
terraform apply tfplan
```

Terraform applies the saved plan exactly as generated.

---

## Command Reference

### Generate Plan

```bash
terraform plan
```

---

### Save Plan

```bash
terraform plan -out=tfplan
```

---

### Apply Saved Plan

```bash
terraform apply tfplan
```

---

## Important Exam Points

* terraform plan generates an execution plan.
* terraform plan does not modify infrastructure.
* Terraform compares current state and desired state.
* Plans should be reviewed before applying.
* * means create.
* ~ means update.
* * means destroy.
* -/+ means replace.
* terraform plan -out saves execution plans.

---

## Common Exam Traps

### Trap 1

Question:

Does terraform plan create resources?

Correct:

No.

---

### Trap 2

Question:

Which command previews infrastructure changes?

Correct:

```bash
terraform plan
```

---

### Trap 3

Question:

What symbol indicates resource creation?

Correct:

```text
+
```

---

### Trap 4

Question:

What symbol indicates resource modification?

Correct:

```text
~
```

---

### Trap 5

Question:

What symbol indicates resource destruction?

Correct:

```text
-
```

---

### Trap 6

Question:

What command saves an execution plan?

Correct:

```bash
terraform plan -out=tfplan
```

---

### Trap 7

Question:

What command applies a saved plan?

Correct:

```bash
terraform apply tfplan
```

---

## Interview Questions

### What is an execution plan?

A preview of infrastructure changes Terraform intends to perform.

### Why should plans be reviewed?

To identify unintended changes before infrastructure is modified.

### Does terraform plan modify infrastructure?

No.

It only generates a preview.

### What does the ~ symbol indicate?

Terraform will modify an existing resource.

### Why save execution plans?

To ensure reviewed and approved changes are applied consistently.

---

## Practice Questions

### Question 1

Which command generates an execution plan?

A. terraform validate

B. terraform apply

C. terraform plan

D. terraform fmt

**Answer:** C

**Explanation:** terraform plan generates a preview of infrastructure changes.

---

### Question 2

Does terraform plan modify infrastructure?

A. Yes

B. No

**Answer:** B

**Explanation:** Planning only previews changes.

---

### Question 3

What symbol indicates resource creation?

A. -

B. ~

C. +

D. *

**Answer:** C

**Explanation:** + indicates Terraform will create a resource.

---

### Question 4

What command saves an execution plan?

A. terraform apply

B. terraform plan -out=tfplan

C. terraform validate

D. terraform state pull

**Answer:** B

**Explanation:** -out saves the generated plan.

---

### Question 5

Terraform generates plans by comparing:

A. Variables and Outputs

B. Providers and Resources

C. Current State and Desired State

D. Modules and Providers

**Answer:** C

**Explanation:** Terraform determines required changes by comparing current and desired state.

---

## Related Objectives

* 2d Explain How Terraform Uses and Manages State
* 3a Describe the Terraform Workflow
* 3e Apply Changes to Infrastructure
* 6d Manage Resource Drift and Terraform State

---

## Key Takeaways

* terraform plan previews infrastructure changes.
* Planning does not modify infrastructure.
* Terraform compares current state and desired state.
* Review plans before applying changes.
* * = Create
* ~ = Modify
* * = Destroy
* -/+ = Replace
* Saved plans improve deployment consistency.
