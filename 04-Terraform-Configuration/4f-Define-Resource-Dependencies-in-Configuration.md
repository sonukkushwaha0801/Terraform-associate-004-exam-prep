# Objective: 4f - Define Resource Dependencies in Configuration

## Definition

Terraform uses dependencies to determine the order in which resources should be created, modified, or destroyed.

Terraform automatically builds a dependency graph and executes operations in the correct order.

Dependencies are critical because infrastructure resources often rely on other resources.

Examples:

- EC2 Instance depends on Subnet
- Subnet depends on VPC
- Route Table depends on VPC
- Load Balancer depends on Subnets

Terraform supports:

- Implicit Dependencies
- Explicit Dependencies

This objective is commonly tested in Terraform Associate (004).

---

## Core Concepts

### Dependency

A dependency exists when one resource requires another resource before it can be created.

Example:

```text
VPC
 │
 ▼
Subnet
 │
 ▼
EC2 Instance
```

Terraform must create:

```text
VPC
 ↓
Subnet
 ↓
EC2
```

in that order.

---

# Implicit Dependencies

## Definition

Terraform automatically creates dependencies when a resource references another resource.

No additional configuration is required.

Example:

```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "private" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"
}
```

Terraform automatically understands:

```text
aws_subnet.private
        │
        ▼
depends on
        │
        ▼
aws_vpc.main
```

---

## Why It Works

Terraform sees:

```hcl
aws_vpc.main.id
```

and creates a dependency relationship.

This is called:

```text
Implicit Dependency
```

---

## Recommended Approach

HashiCorp recommends:

```text
Use implicit dependencies whenever possible.
```

because they are:

- Clear
- Maintainable
- Automatically managed

---

# Explicit Dependencies

## Definition

Explicit dependencies are manually declared using:

```hcl
depends_on
```

Terraform creates a dependency even when no attribute reference exists.

---

## Syntax

```hcl
depends_on = [
  resource.reference
]
```

---

## Example

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t3.micro"

  depends_on = [
    aws_security_group.web
  ]
}
```

Terraform creates:

```text
Security Group
      ↓
EC2 Instance
```

even if no attribute is referenced.

---

# Why Explicit Dependencies Exist

Sometimes resources have hidden relationships.

Terraform cannot detect them automatically.

Example:

```text
Resource A must exist
before
Resource B
```

but no attributes are referenced.

Use:

```hcl
depends_on
```

to inform Terraform.

---

# Implicit vs Explicit Dependencies

| Feature             | Implicit | Explicit         |
| ------------------- | -------- | ---------------- |
| Automatic           | Yes      | No               |
| Uses References     | Yes      | No               |
| Requires depends_on | No       | Yes              |
| Preferred           | Yes      | Only When Needed |

---

# Dependency Graph

Terraform builds a dependency graph before execution.

Example:

```text
VPC
 │
 ├── Public Subnet
 │
 ├── Private Subnet
 │
 └── Route Table
         │
         ▼
      EC2 Instance
```

Terraform determines:

- Creation Order
- Update Order
- Destruction Order

automatically.

---

# Resource Creation Order

Terraform creates dependencies first.

Example:

```text
1. VPC
2. Subnet
3. Security Group
4. EC2 Instance
```

---

# Resource Destruction Order

Terraform destroys resources in reverse order.

Example:

```text
EC2 Instance
↓
Security Group
↓
Subnet
↓
VPC
```

This prevents dependency conflicts.

---

# Terraform Graph Command

Generate dependency graph:

```bash
terraform graph
```

Output:

```text
Dependency Graph
```

Useful for troubleshooting.

---

# How It Works

Terraform Workflow:

```text
Read Configuration
        │
        ▼
Build Dependency Graph
        │
        ▼
Determine Resource Order
        │
        ▼
Create Execution Plan
        │
        ▼
Apply Infrastructure
```

---

# Terraform Perspective

Example:

```hcl
resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "private" {
  vpc_id = aws_vpc.main.id
}
```

Terraform automatically builds:

```text
aws_vpc.main
      ↓
aws_subnet.private
```

No depends_on required.

---

# Real-World Example

Infrastructure:

```text
VPC
 │
 ├── Public Subnets
 │
 ├── Private Subnets
 │
 ├── Security Groups
 │
 └── EC2 Instances
```

Terraform automatically determines dependency order through references.

---

# Production Use Case

Enterprise Deployments:

Resources often depend on:

- Networks
- Security Policies
- Identity Resources
- Storage Resources

Terraform dependency management allows safe deployments at scale.

---

# Important Exam Points

- Terraform automatically builds dependency graphs.
- Resource references create implicit dependencies.
- depends_on creates explicit dependencies.
- Implicit dependencies are preferred.
- Terraform creates resources in dependency order.
- Terraform destroys resources in reverse dependency order.
- terraform graph visualizes dependencies.

---

# Common Exam Traps

### Trap 1

Question:

What creates an implicit dependency?

Correct:

```hcl
aws_vpc.main.id
```

resource reference.

---

### Trap 2

Question:

What creates an explicit dependency?

Correct:

```hcl
depends_on
```

---

### Trap 3

Question:

Should depends_on always be used?

Correct:

No.

Only when Terraform cannot infer dependencies.

---

### Trap 4

Question:

Which dependency type is preferred?

Correct:

Implicit Dependency.

---

### Trap 5

Question:

What command visualizes dependencies?

Correct:

```bash
terraform graph
```

---

### Trap 6

Question:

In what order are resources destroyed?

Correct:

Reverse dependency order.

---

# Interview Questions

### What is a Terraform dependency?

A relationship where one resource requires another resource to exist first.

### What is an implicit dependency?

A dependency automatically created through resource references.

### What is an explicit dependency?

A dependency manually declared using depends_on.

### When should depends_on be used?

Only when Terraform cannot infer the dependency automatically.

### Why are implicit dependencies preferred?

They are simpler, clearer, and automatically maintained.

---

# Practice Questions

### Question 1

What creates an implicit dependency?

A. depends_on

B. Resource Reference

C. Variable

D. Output

**Answer:** B

---

### Question 2

Which Terraform argument creates an explicit dependency?

A. count

B. provider

C. depends_on

D. lifecycle

**Answer:** C

---

### Question 3

Which dependency type is preferred?

A. Explicit

B. Manual

C. Implicit

D. Forced

**Answer:** C

---

### Question 4

Which command visualizes Terraform dependencies?

A. terraform validate

B. terraform graph

C. terraform output

D. terraform state list

**Answer:** B

---

### Question 5

Terraform destroys resources in:

A. Random Order

B. Alphabetical Order

C. Reverse Dependency Order

D. Creation Order

**Answer:** C

---

## Related Objectives

- 4a Resource and Data Blocks
- 4b Resource References
- 4e Expressions and Functions
- 6d Resource Drift and State

---

## Key Takeaways

- Terraform automatically manages dependencies.
- Resource references create implicit dependencies.
- depends_on creates explicit dependencies.
- Implicit dependencies are preferred.
- Terraform builds a dependency graph.
- Resources are created in dependency order.
- Resources are destroyed in reverse dependency order.
- terraform graph visualizes dependency relationships.
