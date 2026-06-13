# Objective: 3g - Apply Formatting and Style Adjustments to a Configuration

## Definition

Terraform formatting is the process of automatically adjusting configuration files to follow Terraform's standard style conventions.

Formatting is performed using:

```bash
terraform fmt
```

This command improves readability, consistency, and maintainability of Terraform code.

Formatting does not change infrastructure behavior.

It only changes code presentation.

---

## Core Concepts

### Formatting

Terraform automatically applies:

* Consistent indentation
* Proper spacing
* Alignment of arguments
* Standardized formatting rules

Example:

Before:

```hcl
resource "aws_instance" "web" {
ami="ami-123456"
instance_type="t3.micro"
}
```

After:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

---

### Standardization

Terraform has a built-in formatting standard.

All Terraform users follow the same style.

Benefits:

* Readability
* Consistency
* Easier Code Reviews
* Reduced Formatting Disputes

---

### Team Collaboration

Consistent formatting helps teams:

* Review code faster
* Identify real changes
* Reduce unnecessary Git diffs

---

### Non-Destructive Operation

terraform fmt:

✅ Changes formatting

❌ Does not modify infrastructure

❌ Does not change resource behavior

❌ Does not update state

---

## How It Works

Formatting workflow:

```text
Read Configuration
        │
        ▼
Apply Terraform Style Rules
        │
        ▼
Rewrite Files
        │
        ▼
Formatting Complete
```

---

## Terraform Perspective

Poorly formatted configuration:

```hcl
resource "aws_s3_bucket" "app" {
bucket="company-app"
}
```

Execution:

```bash
terraform fmt
```

Result:

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "company-app"
}
```

Terraform rewrites the file using standard formatting.

---

## Real-World Example

Developer A writes:

```hcl
resource "aws_instance" "web" {
ami="ami-123456"
instance_type="t3.micro"
}
```

Developer B writes:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

Running:

```bash
terraform fmt
```

ensures both configurations follow identical formatting standards.

---

## Production Use Case

CI/CD pipeline:

```bash
terraform fmt -check
terraform validate
terraform plan
```

Benefits:

* Consistent codebase
* Easier reviews
* Standardized Terraform projects

Many organizations enforce formatting checks in pull requests.

---

## Formatting vs Validation

### terraform fmt

Purpose:

```text
Formatting
```

Checks:

* Indentation
* Spacing
* Style

Does NOT:

* Validate syntax
* Detect configuration errors

---

### terraform validate

Purpose:

```text
Configuration Correctness
```

Checks:

* Syntax
* References
* Internal consistency

Does NOT:

* Format code

---

## Formatting vs Planning

### terraform fmt

Formats code.

---

### terraform plan

Generates execution plans.

Determines infrastructure changes.

---

## Command Reference

### Format Configuration

```bash
terraform fmt
```

---

### Check Formatting Only

```bash
terraform fmt -check
```

Reports formatting issues without modifying files.

---

### Recursive Formatting

```bash
terraform fmt -recursive
```

Formats Terraform files in subdirectories.

---

## Important Exam Points

* terraform fmt formats Terraform code.
* terraform fmt does not modify infrastructure.
* terraform fmt does not validate configuration.
* terraform fmt does not update state.
* Formatting improves consistency and readability.
* Terraform has built-in formatting standards.
* terraform fmt is commonly used before commits and pull requests.

---

## Common Exam Traps

### Trap 1

Question:

Which command formats Terraform code?

Correct:

```bash
terraform fmt
```

---

### Trap 2

Question:

Does terraform fmt validate configuration?

Correct:

No.

Use:

```bash
terraform validate
```

---

### Trap 3

Question:

Does terraform fmt create infrastructure?

Correct:

No.

---

### Trap 4

Question:

Does terraform fmt modify state?

Correct:

No.

---

### Trap 5

Question:

Which command checks formatting without modifying files?

Correct:

```bash
terraform fmt -check
```

---

### Trap 6

Question:

Which command formats subdirectories?

Correct:

```bash
terraform fmt -recursive
```

---

## Interview Questions

### What does terraform fmt do?

Formats Terraform configuration files according to Terraform style conventions.

### Why is formatting important?

Improves readability, consistency, and maintainability.

### Does terraform fmt affect infrastructure?

No.

Only formatting changes are made.

### What is the difference between fmt and validate?

fmt checks formatting.

validate checks configuration correctness.

### Why is formatting commonly enforced in CI/CD pipelines?

To maintain consistent code quality across teams.

---

## Practice Questions

### Question 1

Which command formats Terraform configuration files?

A. terraform validate

B. terraform plan

C. terraform fmt

D. terraform apply

**Answer:** C

**Explanation:** terraform fmt automatically formats Terraform code.

---

### Question 2

What is the primary purpose of terraform fmt?

A. Validate Configuration

B. Create Resources

C. Apply Formatting Standards

D. Manage State

**Answer:** C

**Explanation:** fmt enforces Terraform's formatting conventions.

---

### Question 3

Does terraform fmt modify infrastructure?

A. Yes

B. No

**Answer:** B

**Explanation:** Formatting only affects source code appearance.

---

### Question 4

Which command checks formatting without modifying files?

A. terraform fmt -recursive

B. terraform fmt -check

C. terraform validate

D. terraform plan

**Answer:** B

**Explanation:** -check reports formatting issues without rewriting files.

---

### Question 5

Which statement is TRUE?

A. terraform fmt validates configuration.

B. terraform fmt updates state.

C. terraform fmt formats Terraform code.

D. terraform fmt creates resources.

**Answer:** C

**Explanation:** terraform fmt is used exclusively for formatting.

---

## Related Objectives

* 3a Describe the Terraform Workflow
* 3b Initialize a Terraform Working Directory
* 3c Validate a Terraform Configuration
* 3d Generate and Review an Execution Plan
* 3e Apply Changes to Infrastructure

---

## Key Takeaways

* terraform fmt formats Terraform code.
* Formatting improves consistency and readability.
* Formatting does not affect infrastructure.
* Formatting does not validate configuration.
* terraform fmt -check verifies formatting.
* terraform fmt -recursive formats subdirectories.
* fmt and validate serve different purposes.
* Formatting is commonly enforced in CI/CD pipelines.
