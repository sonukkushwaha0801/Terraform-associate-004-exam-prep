# Objective: 7b - Use the CLI to Inspect State

## Definition

Terraform provides CLI commands that allow engineers to inspect Terraform state.

State inspection helps:

- Verify Managed Resources
- Troubleshoot Infrastructure
- Audit Terraform Deployments
- Validate Imports
- Investigate Drift

Terraform state inspection is commonly used in production environments and appears frequently in the Terraform Associate (004) exam.

---

## Core Concepts

Terraform state contains:

- Resource IDs
- Resource Attributes
- Dependencies
- Outputs
- Metadata

Terraform provides commands to inspect this information.

---

# State Inspection Commands

The most important commands are:

```bash
terraform state list
```

```bash
terraform state show
```

```bash
terraform show
```

---

# terraform state list

## Definition

Lists all resources currently tracked in Terraform state.

---

## Syntax

```bash
terraform state list
```

---

## Example

Output:

```text
aws_vpc.main
aws_subnet.public
aws_subnet.private
aws_instance.web
aws_security_group.web
```

---

## Purpose

Answers:

```text
What resources is Terraform managing?
```

---

## Common Use Cases

### Verify Imports

After:

```bash
terraform import
```

Run:

```bash
terraform state list
```

to confirm the resource exists in state.

---

### Audit Infrastructure

Quickly determine all managed resources.

---

### Troubleshooting

Confirm whether a resource exists in state.

---

# terraform state show

## Definition

Displays detailed information about a specific resource stored in state.

---

## Syntax

```bash
terraform state show RESOURCE
```

---

## Example

```bash
terraform state show aws_instance.web
```

---

## Sample Output

```text
id = i-123456789

instance_type = t3.micro

ami = ami-123456
```

---

## Purpose

Answers:

```text
What does Terraform know about this resource?
```

---

## Common Use Cases

### Investigate Imports

Verify imported attributes.

---

### Troubleshooting

Inspect:

- IDs
- Tags
- Attributes
- Relationships

---

### Drift Investigation

Compare state values with actual infrastructure.

---

# terraform show

## Definition

Displays the entire Terraform state in human-readable form.

---

## Syntax

```bash
terraform show
```

---

## Example

```bash
terraform show
```

---

## Purpose

Provides:

```text
Complete State Overview
```

including:

- Resources
- Outputs
- Attributes

---

## Example Use Case

Quickly review all infrastructure managed by Terraform.

---

# Comparison

| Command              | Purpose                      |
| -------------------- | ---------------------------- |
| terraform state list | List Resources               |
| terraform state show | Show Single Resource Details |
| terraform show       | Show Entire State            |

---

# State Inspection Workflow

## Step 1

List Resources

```bash
terraform state list
```

---

## Step 2

Choose Resource

Example:

```text
aws_instance.web
```

---

## Step 3

Inspect Resource

```bash
terraform state show aws_instance.web
```

---

## Workflow Diagram

```text
terraform state list
          │
          ▼
Choose Resource
          │
          ▼
terraform state show
          │
          ▼
Inspect Attributes
```

---

# Example Scenario

Infrastructure:

```text
VPC
Subnet
EC2
Security Group
```

Engineer wants:

```text
EC2 Instance ID
```

Workflow:

```bash
terraform state list
```

↓

```text
aws_instance.web
```

↓

```bash
terraform state show aws_instance.web
```

↓

```text
id = i-123456
```

---

# Inspecting Imported Resources

After:

```bash
terraform import aws_instance.web i-123456
```

Verify:

```bash
terraform state list
```

Then:

```bash
terraform state show aws_instance.web
```

---

# Terraform Perspective

Terraform State:

```text
Resources
Attributes
IDs
Metadata
```

Inspection Commands:

```text
Read State
```

without modifying infrastructure.

---

# Real-World Example

Production Incident:

Engineer receives:

```text
Instance Not Responding
```

Investigation:

```bash
terraform state list
```

↓

```bash
terraform state show aws_instance.web
```

↓

Review:

- IDs
- Tags
- Configuration

---

# Production Use Cases

## Auditing

```bash
terraform state list
```

---

## Troubleshooting

```bash
terraform state show
```

---

## Validation

```bash
terraform show
```

---

## Import Verification

```bash
terraform state show
```

---

# Important Exam Points

- terraform state list lists resources tracked by state.
- terraform state show displays details of a specific resource.
- terraform show displays the complete state.
- State inspection commands do not modify infrastructure.
- State inspection is commonly used after imports.
- State inspection is used during troubleshooting.

---

# Common Exam Traps

### Trap 1

Question:

Which command lists resources?

Correct:

```bash
terraform state list
```

---

### Trap 2

Question:

Which command displays one resource?

Correct:

```bash
terraform state show
```

---

### Trap 3

Question:

Which command displays entire state?

Correct:

```bash
terraform show
```

---

### Trap 4

Question:

Do inspection commands modify infrastructure?

Correct:

```text
No
```

---

### Trap 5

Question:

Which command is commonly used after import verification?

Correct:

```bash
terraform state show
```

---

# Interview Questions

### What does terraform state list do?

Lists resources tracked in state.

### What does terraform state show do?

Displays detailed information about a resource.

### What does terraform show do?

Displays the complete Terraform state.

### Do state inspection commands modify infrastructure?

No.

### Why use terraform state show?

To inspect resource attributes stored in state.

---

# Practice Questions

### Question 1

Which command lists all resources tracked by Terraform state?

A. terraform show

B. terraform state show

C. terraform state list

D. terraform inspect

**Answer:** C

---

### Question 2

Which command displays details about a specific resource?

A. terraform state show

B. terraform state list

C. terraform show

D. terraform output

**Answer:** A

---

### Question 3

Which command displays the complete Terraform state?

A. terraform inspect

B. terraform show

C. terraform state list

D. terraform graph

**Answer:** B

---

### Question 4

Do state inspection commands modify infrastructure?

A. Yes

B. No

**Answer:** B

---

### Question 5

Which command is commonly used to verify an imported resource?

A. terraform validate

B. terraform apply

C. terraform state show

D. terraform destroy

**Answer:** C

---

## Related Objectives

- 6d Manage Resource Drift and Terraform State
- 7a Import Existing Infrastructure
- 7c Verbose Logging

---

## Key Takeaways

- `terraform state list` lists resources tracked by state.
- `terraform state show` displays details for a specific resource.
- `terraform show` displays the complete state.
- State inspection commands are read-only.
- These commands are heavily used for troubleshooting and import verification.
- State inspection is a frequently tested Terraform Associate exam topic.
