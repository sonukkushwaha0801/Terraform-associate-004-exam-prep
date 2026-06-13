# Objective: 4g - Validate Configuration Using Custom Conditions

## Definition

Terraform supports custom validation rules that help ensure infrastructure configurations meet defined requirements before deployment.

Custom validation improves:

- Reliability
- Security
- Governance
- User Experience

Terraform supports:

- Variable Validation
- Preconditions
- Postconditions

These features allow Terraform to fail early when invalid inputs or unexpected infrastructure states are detected.

---

## Core Concepts

### Why Validation Matters

Without validation:

```hcl
instance_type = "invalid-instance"
```

Terraform may fail during deployment.

With validation:

Terraform detects the issue before resources are created.

Benefits:

- Prevent configuration errors
- Enforce standards
- Improve module usability
- Reduce deployment failures

---

# Variable Validation

## Definition

Variable validation checks user-provided values before Terraform proceeds.

Terraform evaluates validation rules during:

```bash
terraform plan
```

and

```bash
terraform apply
```

---

## Syntax

```hcl
variable "variable_name" {
  type = string

  validation {
    condition     = ...
    error_message = "..."
  }
}
```

---

## Example

```hcl
variable "environment" {
  type = string

  validation {
    condition = contains(
      ["dev", "test", "prod"],
      var.environment
    )

    error_message = "Environment must be dev, test, or prod."
  }
}
```

Valid:

```text
dev
test
prod
```

Invalid:

```text
production
```

Terraform fails.

---

## Numeric Validation

```hcl
variable "instance_count" {
  type = number

  validation {
    condition     = var.instance_count > 0
    error_message = "Instance count must be greater than zero."
  }
}
```

---

## String Length Validation

```hcl
variable "username" {
  type = string

  validation {
    condition     = length(var.username) >= 5
    error_message = "Username must be at least 5 characters."
  }
}
```

---

# Preconditions

## Definition

Preconditions verify assumptions before a resource is created or updated.

Terraform checks:

```text
Before Resource Operation
```

---

## Syntax

```hcl
precondition {
  condition     = ...
  error_message = "..."
}
```

---

## Example

```hcl
resource "aws_instance" "web" {

  lifecycle {

    precondition {
      condition     = var.instance_count > 0
      error_message = "Instance count must be positive."
    }

  }
}
```

Terraform validates before creating the resource.

---

## Purpose

Preconditions ensure:

- Input assumptions are correct
- Required conditions exist
- Resource creation is safe

---

# Postconditions

## Definition

Postconditions verify expectations after a resource has been created or read.

Terraform checks:

```text
After Resource Operation
```

---

## Syntax

```hcl
postcondition {
  condition     = ...
  error_message = "..."
}
```

---

## Example

```hcl
resource "aws_instance" "web" {

  lifecycle {

    postcondition {
      condition     = self.instance_state == "running"
      error_message = "Instance failed to start."
    }

  }
}
```

Terraform verifies the expected state after creation.

---

## Purpose

Postconditions ensure:

- Resource state is correct
- Provider behavior meets expectations
- Infrastructure is healthy

---

# Validation Comparison

| Feature             | When Checked           |
| ------------------- | ---------------------- |
| Variable Validation | Before Planning        |
| Precondition        | Before Resource Action |
| Postcondition       | After Resource Action  |

---

# How It Works

Validation Workflow:

```text
User Input
      │
      ▼
Variable Validation
      │
      ▼
Terraform Plan
      │
      ▼
Precondition Check
      │
      ▼
Resource Creation
      │
      ▼
Postcondition Check
      │
      ▼
Success
```

---

# Terraform Perspective

Example:

```hcl
variable "environment" {

  validation {
    condition = contains(
      ["dev","test","prod"],
      var.environment
    )

    error_message = "Invalid environment."
  }
}
```

Input:

```text
dev
```

Result:

```text
Pass
```

Input:

```text
production
```

Result:

```text
Fail
```

Terraform stops execution.

---

# Real-World Example

Organization Standard:

Allowed environments:

```text
dev
test
stage
prod
```

Validation:

```hcl
validation {
  condition = contains(
    ["dev","test","stage","prod"],
    var.environment
  )

  error_message = "Invalid environment."
}
```

This prevents accidental deployments.

---

# Production Use Case

Enterprise Terraform Modules often validate:

- Environment Names
- CIDR Blocks
- Region Names
- Instance Sizes
- Resource Counts
- Security Requirements

Benefits:

- Reduced Human Error
- Standardized Deployments
- Compliance Enforcement

---

# Common Validation Functions

## contains()

```hcl
contains(
  ["dev","prod"],
  var.environment
)
```

---

## length()

```hcl
length(var.username)
```

---

## can()

Checks whether an expression succeeds.

```hcl
can(regex("^prod", var.environment))
```

---

## regex()

Pattern matching.

```hcl
regex("^prod", var.environment)
```

---

# Important Exam Points

- Variable validation validates user input.
- Validation blocks use:
  - condition
  - error_message
- Preconditions run before resource actions.
- Postconditions run after resource actions.
- Custom validation improves reliability.
- Terraform stops execution when validation fails.
- contains() and length() are commonly used.

---

# Common Exam Traps

### Trap 1

Question:

Which block validates variable input?

Correct:

```hcl
validation
```

---

### Trap 2

Question:

Which argument defines validation logic?

Correct:

```hcl
condition
```

---

### Trap 3

Question:

Which argument defines validation failure text?

Correct:

```hcl
error_message
```

---

### Trap 4

Question:

When are preconditions evaluated?

Correct:

Before resource actions.

---

### Trap 5

Question:

When are postconditions evaluated?

Correct:

After resource actions.

---

### Trap 6

Question:

What happens when validation fails?

Correct:

Terraform stops execution.

---

# Interview Questions

### What is Terraform variable validation?

A mechanism that validates user-provided input before Terraform proceeds.

### What is a precondition?

A rule checked before a resource operation occurs.

### What is a postcondition?

A rule checked after a resource operation completes.

### Why use validation?

To prevent invalid configurations and improve reliability.

### What happens if validation fails?

Terraform returns an error and stops execution.

---

# Practice Questions

### Question 1

Which Terraform feature validates user input?

A. output

B. validation

C. provider

D. backend

**Answer:** B

---

### Question 2

Which argument contains validation logic?

A. value

B. default

C. condition

D. provider

**Answer:** C

---

### Question 3

When are preconditions evaluated?

A. After Apply

B. Before Resource Actions

C. During Init

D. During Destroy

**Answer:** B

---

### Question 4

When are postconditions evaluated?

A. Before Planning

B. During Init

C. After Resource Actions

D. Before Validation

**Answer:** C

---

### Question 5

What happens when a validation condition evaluates to false?

A. Terraform Ignores It

B. Terraform Retries

C. Terraform Stops Execution

D. Terraform Imports Resources

**Answer:** C

---

## Related Objectives

- 4c Variables and Outputs
- 4d Complex Types
- 4e Expressions and Functions
- 4h Sensitive Data Management

---

## Key Takeaways

- Variable validation checks input values.
- Validation blocks use condition and error_message.
- Preconditions run before resource operations.
- Postconditions run after resource operations.
- Validation prevents invalid configurations.
- Terraform stops when validation fails.
- contains(), length(), can(), and regex() are commonly used.
- Validation is important for production-grade Terraform modules.
