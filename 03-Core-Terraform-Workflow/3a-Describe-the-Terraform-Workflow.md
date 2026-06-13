# Objective: 3a - Describe the Terraform Workflow

## Definition

The Terraform workflow is the sequence of steps used to define, validate, review, provision, modify, and destroy infrastructure.

Terraform follows a predictable workflow that enables infrastructure to be managed safely, consistently, and repeatably.

The standard workflow is:

```text
Write → Init → Validate → Plan → Apply
```

When infrastructure is no longer needed:

```text
Destroy
```

is used to remove resources.

---

## Core Concepts

### Configuration

Infrastructure is defined using Terraform configuration files.

Example:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

---

### Initialization

Terraform initializes the working directory.

Command:

```bash
terraform init
```

Purpose:

* Download providers
* Download modules
* Configure backend

---

### Validation

Terraform validates configuration syntax and internal consistency.

Command:

```bash
terraform validate
```

Purpose:

* Detect syntax errors
* Verify configuration structure

---

### Planning

Terraform compares:

```text
Current State
      vs
Desired State
```

Command:

```bash
terraform plan
```

Purpose:

* Preview changes
* Review impact
* Detect unintended modifications

---

### Apply

Terraform executes infrastructure changes.

Command:

```bash
terraform apply
```

Purpose:

* Create resources
* Update resources
* Delete resources when required

---

### Destroy

Terraform removes managed infrastructure.

Command:

```bash
terraform destroy
```

Purpose:

* Delete Terraform-managed resources

---

### Formatting

Terraform automatically formats configuration files.

Command:

```bash
terraform fmt
```

Purpose:

* Consistent style
* Readable code
* Team standardization

---

## How It Works

Complete Workflow:

```text
Write Configuration
        │
        ▼
terraform init
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
        │
        ▼
Infrastructure Running
        │
        ▼
terraform destroy
```

---

## Terraform Perspective

Terraform uses state throughout the workflow.

Example:

### Configuration

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "my-app-bucket"
}
```

### Plan

```bash
terraform plan
```

Terraform determines:

```text
+ create aws_s3_bucket.app
```

### Apply

```bash
terraform apply
```

Terraform creates the bucket and updates state.

---

## Real-World Example

A DevOps engineer provisions infrastructure:

### Step 1

Create:

```text
main.tf
```

### Step 2

Initialize:

```bash
terraform init
```

### Step 3

Validate:

```bash
terraform validate
```

### Step 4

Review:

```bash
terraform plan
```

### Step 5

Deploy:

```bash
terraform apply
```

Infrastructure is now running.

---

## Production Use Case

A platform engineering team manages production infrastructure.

Workflow:

1. Developers modify Terraform code
2. Pull Request created
3. CI pipeline executes:

   * terraform fmt
   * terraform validate
   * terraform plan
4. Team reviews plan
5. Approved changes are applied

Benefits:

* Safe deployments
* Change visibility
* Infrastructure consistency

---

## Workflow Command Summary

| Command            | Purpose                      |
| ------------------ | ---------------------------- |
| terraform init     | Initialize working directory |
| terraform validate | Validate configuration       |
| terraform plan     | Generate execution plan      |
| terraform apply    | Apply changes                |
| terraform destroy  | Remove infrastructure        |
| terraform fmt      | Format configuration         |

---

## Important Exam Points

* Terraform follows a predictable workflow.
* terraform init is usually the first command.
* terraform validate checks configuration correctness.
* terraform plan previews changes.
* terraform apply executes changes.
* terraform destroy removes resources.
* terraform fmt formats code.
* Reviewing plans before applying is a best practice.

---

## Common Exam Traps

### Trap 1

Question:

Which command should normally be executed first?

Correct:

```bash
terraform init
```

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

Which command actually creates resources?

Correct:

```bash
terraform apply
```

---

### Trap 4

Question:

Which command validates configuration?

Correct:

```bash
terraform validate
```

---

### Trap 5

Question:

Which command formats Terraform code?

Correct:

```bash
terraform fmt
```

---

### Trap 6

Question:

Which command removes infrastructure?

Correct:

```bash
terraform destroy
```

---

## Interview Questions

### What is the standard Terraform workflow?

Write → Init → Validate → Plan → Apply

---

### Why is terraform plan important?

It allows engineers to review infrastructure changes before execution.

---

### Why should plans be reviewed before apply?

To detect unintended changes and reduce deployment risk.

---

### What is the purpose of terraform validate?

To verify configuration syntax and internal consistency.

---

### What command removes infrastructure?

```bash
terraform destroy
```

---

## Practice Questions

### Question 1

Which command is typically executed first in a Terraform project?

A. terraform apply

B. terraform plan

C. terraform init

D. terraform destroy

**Answer:** C

**Explanation:** terraform init initializes the working directory and downloads required components.

---

### Question 2

Which command previews infrastructure changes?

A. terraform validate

B. terraform plan

C. terraform fmt

D. terraform providers

**Answer:** B

**Explanation:** terraform plan generates an execution plan without making changes.

---

### Question 3

Which command applies infrastructure changes?

A. terraform plan

B. terraform validate

C. terraform apply

D. terraform fmt

**Answer:** C

**Explanation:** terraform apply executes the actions shown in the execution plan.

---

### Question 4

What is the primary purpose of terraform validate?

A. Format Code

B. Create Resources

C. Validate Configuration

D. Remove Resources

**Answer:** C

**Explanation:** terraform validate checks syntax and configuration consistency.

---

### Question 5

Which command removes Terraform-managed resources?

A. terraform plan

B. terraform apply

C. terraform destroy

D. terraform init

**Answer:** C

**Explanation:** terraform destroy removes infrastructure managed by Terraform.

---

## Related Objectives

* 3b Initialize a Terraform Working Directory
* 3c Validate a Terraform Configuration
* 3d Generate and Review an Execution Plan
* 3e Apply Changes to Infrastructure
* 3f Destroy Terraform-Managed Infrastructure
* 3g Apply Formatting and Style Adjustments

---

## Key Takeaways

* Terraform follows a structured workflow.
* Standard workflow is Write → Init → Validate → Plan → Apply.
* terraform init prepares the environment.
* terraform validate checks correctness.
* terraform plan previews changes.
* terraform apply executes changes.
* terraform destroy removes infrastructure.
* terraform fmt standardizes code formatting.
* Understanding workflow order is a high-probability exam topic.
