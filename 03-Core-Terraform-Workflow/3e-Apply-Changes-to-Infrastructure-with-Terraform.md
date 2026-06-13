# Objective: 3e - Apply Changes to Infrastructure with Terraform

## Definition

Terraform applies infrastructure changes using:

```bash
terraform apply
```

This command executes the actions required to make infrastructure match the desired configuration.

Terraform uses the execution plan to determine which resources must be:

* Created
* Modified
* Destroyed

After successfully applying changes, Terraform updates the state file.

---

## Core Concepts

### Apply Operation

The apply operation is responsible for executing infrastructure changes.

Terraform:

1. Reads configuration
2. Reads state
3. Compares current and desired state
4. Generates execution plan
5. Executes changes
6. Updates state

---

### Infrastructure Creation

Example:

Configuration:

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "company-app-bucket"
}
```

Execution:

```bash
terraform apply
```

Terraform creates the bucket.

---

### Infrastructure Modification

Current State:

```text
instance_type = t2.micro
```

Desired State:

```text
instance_type = t3.micro
```

Terraform modifies the resource.

---

### Infrastructure Destruction

If a resource is removed from configuration:

```hcl
resource "aws_instance" "web" {}
```

Terraform may plan:

```text
- aws_instance.web
```

and remove it during apply.

---

## How It Works

Terraform apply workflow:

```text
Read Configuration
        │
        ▼
Read State
        │
        ▼
Generate Execution Plan
        │
        ▼
User Approval
        │
        ▼
Execute Changes
        │
        ▼
Update State
```

---

## Terraform Perspective

Example:

Configuration:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Execution:

```bash
terraform apply
```

Terraform:

* Calls providers
* Sends API requests
* Creates or modifies resources
* Updates terraform.tfstate

---

## Interactive Approval

Default behavior:

```bash
terraform apply
```

Terraform displays:

```text
Do you want to perform these actions?

Only 'yes' will be accepted to approve.
```

User must type:

```text
yes
```

before changes are executed.

---

## Auto Approval

Terraform supports automatic approval:

```bash
terraform apply -auto-approve
```

Purpose:

* CI/CD Pipelines
* Automated Deployments

Warning:

Infrastructure changes occur without manual confirmation.

---

## Applying Saved Plans

Generate Plan:

```bash
terraform plan -out=tfplan
```

Apply Saved Plan:

```bash
terraform apply tfplan
```

Benefits:

* Approved plan execution
* Predictable deployments
* Reduced deployment risk

---

## Real-World Example

Developer:

```bash
terraform plan
```

Reviews output:

```text
+ aws_instance.web
```

After approval:

```bash
terraform apply
```

Terraform creates the EC2 instance.

State file is updated.

---

## Production Use Case

Enterprise Workflow:

```text
Developer Creates Change
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
Review & Approval
            │
            ▼
terraform apply
```

This workflow minimizes production risk.

---

## State Updates

After successful apply:

Terraform updates:

```text
terraform.tfstate
```

State reflects:

* New resources
* Modified resources
* Deleted resources

---

## Command Reference

### Apply Changes

```bash
terraform apply
```

---

### Apply Without Prompt

```bash
terraform apply -auto-approve
```

---

### Apply Saved Plan

```bash
terraform apply tfplan
```

---

## Important Exam Points

* terraform apply executes infrastructure changes.
* terraform apply creates, modifies, and destroys resources.
* terraform apply updates state.
* Default apply requires approval.
* -auto-approve skips approval.
* Saved plans can be applied.
* Providers perform API operations during apply.

---

## Common Exam Traps

### Trap 1

Question:

Which command actually creates infrastructure?

Correct:

```bash
terraform apply
```

---

### Trap 2

Question:

Does terraform plan create resources?

Correct:

No.

Only apply modifies infrastructure.

---

### Trap 3

Question:

What happens after successful apply?

Correct:

State is updated.

---

### Trap 4

Question:

Which flag skips approval?

Correct:

```bash
terraform apply -auto-approve
```

---

### Trap 5

Question:

Can Terraform apply a saved plan?

Correct:

Yes.

```bash
terraform apply tfplan
```

---

### Trap 6

Question:

Who performs infrastructure changes?

Correct:

Providers.

Terraform Core determines actions, providers execute them.

---

## Interview Questions

### What does terraform apply do?

Executes infrastructure changes required to achieve the desired state.

### Does terraform apply update state?

Yes.

Terraform updates state after successful execution.

### What is the difference between plan and apply?

Plan previews changes.

Apply executes changes.

### Why use saved execution plans?

To ensure reviewed and approved changes are applied exactly as planned.

### What is auto-approve used for?

Automation and CI/CD pipelines.

---

## Practice Questions

### Question 1

Which command executes infrastructure changes?

A. terraform validate

B. terraform plan

C. terraform apply

D. terraform fmt

**Answer:** C

**Explanation:** terraform apply performs infrastructure operations.

---

### Question 2

What happens after a successful apply?

A. Providers are removed

B. State is updated

C. Configuration is deleted

D. Resources are destroyed

**Answer:** B

**Explanation:** Terraform updates state after applying changes.

---

### Question 3

Which command applies a previously saved execution plan?

A. terraform validate tfplan

B. terraform fmt tfplan

C. terraform apply tfplan

D. terraform state pull tfplan

**Answer:** C

**Explanation:** Terraform can apply saved plans directly.

---

### Question 4

Which flag skips manual approval?

A. -force

B. -approve

C. -auto-approve

D. -skip

**Answer:** C

**Explanation:** -auto-approve executes changes without confirmation.

---

### Question 5

Which statement is TRUE?

A. terraform plan creates resources.

B. terraform apply only validates configuration.

C. terraform apply executes infrastructure changes.

D. terraform validate updates state.

**Answer:** C

**Explanation:** apply is the command that performs infrastructure modifications.

---

## Related Objectives

* 2d Explain How Terraform Uses and Manages State
* 3d Generate and Review an Execution Plan
* 3f Destroy Terraform-Managed Infrastructure
* 6d Manage Resource Drift and Terraform State

---

## Key Takeaways

* terraform apply executes infrastructure changes.
* Apply creates, updates, and removes resources.
* State is updated after successful execution.
* Default apply requires approval.
* -auto-approve skips confirmation.
* Saved plans can be applied directly.
* Providers perform the actual API operations.
* Apply is the only workflow command that modifies infrastructure.
