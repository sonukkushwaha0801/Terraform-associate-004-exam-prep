# Objective: 3f - Destroy Terraform-Managed Infrastructure

## Definition

Terraform destroys managed infrastructure using:

```bash
terraform destroy
```

This command removes resources managed by Terraform and updates the state file to reflect the changes.

Destroy is essentially the reverse of apply.

Instead of creating infrastructure to match the desired state, Terraform removes managed infrastructure.

---

## Core Concepts

### Destroy Operation

Destroy removes resources that are currently managed by Terraform.

Terraform:

1. Reads configuration
2. Reads state
3. Determines managed resources
4. Generates destruction plan
5. Requests approval
6. Deletes resources
7. Updates state

---

### Managed Resources

Terraform can only destroy resources it manages.

Example:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

If the resource exists in state, Terraform can destroy it.

---

### State Dependency

Terraform uses state to determine:

* Which resources exist
* Resource relationships
* Destruction order

Without state, Terraform cannot reliably determine what should be destroyed.

---

### Dependency Awareness

Terraform destroys resources in the correct order.

Example:

```text
EC2 Instance
      │
      ▼
Security Group
      │
      ▼
VPC
```

Terraform typically removes:

```text
EC2 Instance
      ▼
Security Group
      ▼
VPC
```

to avoid dependency conflicts.

---

## How It Works

Destroy workflow:

```text
Read Configuration
        │
        ▼
Read State
        │
        ▼
Generate Destroy Plan
        │
        ▼
User Approval
        │
        ▼
Delete Resources
        │
        ▼
Update State
```

---

## Terraform Perspective

Current State:

```text
aws_instance.web
aws_security_group.web
```

Execution:

```bash
terraform destroy
```

Terraform generates a destruction plan and displays the resources that will be removed.

---

## Interactive Approval

Default behavior:

```bash
terraform destroy
```

Terraform prompts:

```text
Do you really want to destroy all resources?

Only 'yes' will be accepted to approve.
```

User must enter:

```text
yes
```

before destruction begins.

---

## Auto Approval

Terraform supports automated destruction:

```bash
terraform destroy -auto-approve
```

This skips interactive confirmation.

Commonly used in:

* Test environments
* CI/CD pipelines
* Temporary infrastructure

---

## Real-World Example

Developer creates:

```bash
terraform apply
```

Resources:

```text
EC2 Instance
S3 Bucket
Security Group
```

Later:

```bash
terraform destroy
```

Terraform removes all managed resources and updates state.

---

## Production Use Case

Temporary environments:

```text
Feature Branch Environment
          │
          ▼
terraform apply
          │
          ▼
Testing
          │
          ▼
terraform destroy
```

Benefits:

* Cost Savings
* Environment Cleanup
* Resource Lifecycle Management

---

## Destroy vs Apply

### terraform apply

Purpose:

```text
Create / Modify Infrastructure
```

---

### terraform destroy

Purpose:

```text
Remove Infrastructure
```

---

## Destroy Plan

Before destruction, Terraform generates a destroy plan.

Example:

```text
- aws_instance.web
- aws_security_group.web
```

The minus symbol indicates destruction.

---

## State Updates

After successful destruction:

Terraform updates:

```text
terraform.tfstate
```

Removed resources are no longer tracked.

---

## Command Reference

### Destroy Infrastructure

```bash
terraform destroy
```

---

### Destroy Without Approval

```bash
terraform destroy -auto-approve
```

---

### Generate Destroy Plan

```bash
terraform plan -destroy
```

Preview destruction without executing it.

---

## Important Exam Points

* terraform destroy removes managed infrastructure.
* Destroy updates Terraform state.
* Destroy requires approval by default.
* -auto-approve skips approval.
* Terraform destroys resources in dependency order.
* Terraform uses state during destruction.
* terraform plan -destroy previews destruction.

---

## Common Exam Traps

### Trap 1

Question:

Which command removes Terraform-managed resources?

Correct:

```bash
terraform destroy
```

---

### Trap 2

Question:

Does destroy update state?

Correct:

Yes.

---

### Trap 3

Question:

Can destroy be previewed?

Correct:

Yes.

```bash
terraform plan -destroy
```

---

### Trap 4

Question:

What symbol indicates destruction?

Correct:

```text
-
```

---

### Trap 5

Question:

Can Terraform destroy resources it does not manage?

Correct:

No.

---

### Trap 6

Question:

Which command skips destroy confirmation?

Correct:

```bash
terraform destroy -auto-approve
```

---

## Interview Questions

### What does terraform destroy do?

Removes infrastructure managed by Terraform.

### Does destroy update state?

Yes.

Terraform updates state after successful destruction.

### What is the difference between apply and destroy?

Apply creates or modifies infrastructure.

Destroy removes infrastructure.

### How can destruction be previewed?

Using:

```bash
terraform plan -destroy
```

### Why is state important during destroy?

Terraform uses state to determine what resources should be removed.

---

## Practice Questions

### Question 1

Which command removes Terraform-managed infrastructure?

A. terraform apply

B. terraform validate

C. terraform destroy

D. terraform fmt

**Answer:** C

**Explanation:** terraform destroy removes managed resources.

---

### Question 2

Which command previews resource destruction?

A. terraform apply

B. terraform plan -destroy

C. terraform validate

D. terraform state list

**Answer:** B

**Explanation:** plan -destroy generates a destroy plan without executing it.

---

### Question 3

What happens after successful destruction?

A. State is updated

B. Providers are removed

C. Configuration is deleted

D. Modules are removed

**Answer:** A

**Explanation:** Terraform updates state after resources are destroyed.

---

### Question 4

Which flag skips destroy confirmation?

A. -force

B. -approve

C. -auto-approve

D. -destroy

**Answer:** C

**Explanation:** -auto-approve bypasses manual confirmation.

---

### Question 5

Which statement is TRUE?

A. terraform destroy creates resources.

B. terraform destroy removes managed infrastructure.

C. terraform destroy formats code.

D. terraform destroy validates configuration.

**Answer:** B

**Explanation:** destroy removes resources tracked by Terraform.

---

## Related Objectives

* 2d Explain How Terraform Uses and Manages State
* 3d Generate and Review an Execution Plan
* 3e Apply Changes to Infrastructure
* 6d Manage Resource Drift and Terraform State

---

## Key Takeaways

* terraform destroy removes Terraform-managed resources.
* Terraform uses state during destruction.
* State is updated after destroy.
* Destroy requires approval by default.
* terraform destroy -auto-approve skips confirmation.
* terraform plan -destroy previews destruction.
* Destroy follows dependency-aware ordering.
* Destroy is the reverse operation of apply.
