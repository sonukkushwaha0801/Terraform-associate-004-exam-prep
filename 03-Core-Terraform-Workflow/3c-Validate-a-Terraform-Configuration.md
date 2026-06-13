# Objective: 3c - Validate a Terraform Configuration

## Definition

Terraform validation is the process of checking whether a Terraform configuration is syntactically correct and internally consistent.

Validation is performed using:

```bash
terraform validate
```

This command helps identify configuration errors before generating an execution plan or applying infrastructure changes.

Validation improves reliability by detecting issues early in the workflow.

---

## Core Concepts

### Validation

Validation verifies:

* Terraform syntax
* Block structure
* Attribute usage
* Resource references
* Variable references
* Configuration consistency

Terraform checks whether the configuration is logically valid.

---

### Validation Command

```bash
terraform validate
```

Purpose:

* Detect errors
* Verify configuration correctness
* Prevent failed deployments

---

### Syntax Validation

Example:

Valid:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

Invalid:

```hcl
resource "aws_instance" "web" {
  ami = "ami-123456"
  instance_type = "t3.micro"
```

Missing closing brace:

```text
}
```

Terraform validation detects this error.

---

### Configuration Validation

Terraform also validates references.

Example:

```hcl
resource "aws_instance" "web" {
  subnet_id = aws_subnet.private.id
}
```

If:

```text
aws_subnet.private
```

does not exist, validation fails.

---

## How It Works

Validation workflow:

```text
Read Configuration
        │
        ▼
Check Syntax
        │
        ▼
Check References
        │
        ▼
Check Configuration Consistency
        │
        ▼
Validation Success or Failure
```

---

## Terraform Perspective

Example:

Configuration:

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "company-app-bucket"
}
```

Validation:

```bash
terraform validate
```

Output:

```text
Success! The configuration is valid.
```

Terraform confirms that the configuration structure is correct.

---

## Real-World Example

A DevOps engineer modifies Terraform code.

Before opening a pull request:

```bash
terraform validate
```

is executed.

Validation detects configuration issues before code review or deployment.

---

## Production Use Case

CI/CD pipeline:

```bash
terraform fmt
terraform validate
terraform plan
```

Benefits:

* Early error detection
* Faster feedback
* Reduced deployment failures

Most production pipelines run validation automatically.

---

## Validation vs Planning

### terraform validate

Checks:

* Syntax
* References
* Internal consistency

Does NOT:

* Contact cloud APIs
* Generate infrastructure changes

---

### terraform plan

Checks:

* Current state
* Desired state
* Infrastructure changes

Generates execution plan.

---

## Validation vs Formatting

### terraform validate

Purpose:

```text
Correctness
```

---

### terraform fmt

Purpose:

```text
Formatting
```

Validation checks whether code is valid.

Formatting checks whether code follows style conventions.

---

## Command Reference

### Validate Configuration

```bash
terraform validate
```

---

### Format Configuration

```bash
terraform fmt
```

---

### Generate Plan

```bash
terraform plan
```

---

## Important Exam Points

* terraform validate checks configuration correctness.
* terraform validate detects syntax errors.
* terraform validate detects invalid references.
* terraform validate does not create resources.
* terraform validate does not generate plans.
* terraform validate is commonly executed after terraform init.
* Validation is often used in CI/CD pipelines.

---

## Common Exam Traps

### Trap 1

Question:

Which command validates Terraform configuration?

Correct:

```bash
terraform validate
```

---

### Trap 2

Question:

Which command formats Terraform code?

Correct:

```bash
terraform fmt
```

---

### Trap 3

Question:

Which command generates an execution plan?

Correct:

```bash
terraform plan
```

---

### Trap 4

Question:

Does terraform validate create infrastructure?

Correct:

No.

---

### Trap 5

Question:

Does terraform validate contact cloud APIs?

Correct:

No.

---

### Trap 6

Question:

Should terraform init typically run before validate?

Correct:

Yes.

Terraform must initialize the working directory first.

---

## Interview Questions

### What does terraform validate do?

Checks whether a Terraform configuration is syntactically and logically valid.

### Why is validation important?

It detects errors before planning or deployment.

### Does terraform validate create resources?

No.

### What is the difference between validate and plan?

Validate checks correctness.
Plan calculates infrastructure changes.

### What is the difference between validate and fmt?

Validate checks correctness.
fmt checks formatting.

---

## Practice Questions

### Question 1

Which command validates a Terraform configuration?

A. terraform fmt

B. terraform plan

C. terraform validate

D. terraform apply

**Answer:** C

**Explanation:** terraform validate checks syntax and configuration consistency.

---

### Question 2

What does terraform validate primarily check?

A. Infrastructure Changes

B. Code Formatting

C. Configuration Correctness

D. Provider Versions

**Answer:** C

**Explanation:** Validation focuses on correctness and consistency.

---

### Question 3

Which command is commonly executed before terraform validate?

A. terraform apply

B. terraform destroy

C. terraform init

D. terraform output

**Answer:** C

**Explanation:** Initialization should occur before validation.

---

### Question 4

Does terraform validate create infrastructure?

A. Yes

B. No

**Answer:** B

**Explanation:** Validation only checks configuration correctness.

---

### Question 5

Which statement is TRUE?

A. terraform validate generates execution plans.

B. terraform validate formats code.

C. terraform validate checks configuration correctness.

D. terraform validate creates resources.

**Answer:** C

**Explanation:** Validation verifies syntax and configuration consistency.

---

## Related Objectives

* 3a Describe the Terraform Workflow
* 3b Initialize a Terraform Working Directory
* 3d Generate and Review an Execution Plan
* 3g Apply Formatting and Style Adjustments

---

## Key Takeaways

* terraform validate checks configuration correctness.
* Validation detects syntax and reference errors.
* Validation does not create infrastructure.
* Validation does not generate plans.
* terraform init should generally run before validation.
* Validation is commonly integrated into CI/CD pipelines.
* Understand the distinction between validate, fmt, and plan.
