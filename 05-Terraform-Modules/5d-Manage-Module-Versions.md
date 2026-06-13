# Objective: 5d - Manage Module Versions

## Definition

Terraform allows module versions to be controlled and constrained.

Version management ensures:

- Predictable Deployments
- Stable Infrastructure
- Controlled Upgrades
- Reduced Risk

Without version control, Terraform could download newer module versions that introduce breaking changes.

This objective focuses on:

- Module Versioning
- Semantic Versioning
- Version Constraints
- Module Upgrades

and is a frequently tested Terraform Associate (004) topic.

---

## Core Concepts

### Why Version Modules?

Example:

A module currently uses:

```text
v1.0.0
```

A new release:

```text
v2.0.0
```

introduces breaking changes.

Without version constraints:

Terraform may download the newer version unexpectedly.

Result:

```text
Deployment Failure
```

Version constraints prevent this.

---

# Semantic Versioning

Terraform modules typically follow:

```text
MAJOR.MINOR.PATCH
```

Format:

```text
1.2.3
```

---

## Major Version

Example:

```text
2.0.0
```

Meaning:

```text
Breaking Changes
```

Examples:

- Resource Renaming
- Variable Changes
- Output Changes

---

## Minor Version

Example:

```text
1.4.0
```

Meaning:

```text
New Features
```

without breaking existing functionality.

---

## Patch Version

Example:

```text
1.4.3
```

Meaning:

```text
Bug Fixes
```

No new features.

No breaking changes.

---

## Semantic Version Summary

| Version Part | Meaning          |
| ------------ | ---------------- |
| MAJOR        | Breaking Changes |
| MINOR        | New Features     |
| PATCH        | Bug Fixes        |

---

# Module Version Argument

Terraform Registry modules support:

```hcl
version
```

argument.

Example:

```hcl
module "vpc" {

  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0.0"

}
```

Terraform downloads:

```text
Version 5.0.0
```

specifically.

---

# Exact Version Constraint

Example:

```hcl
version = "5.0.0"
```

Meaning:

```text
Only Version 5.0.0
```

No upgrades allowed.

---

# Greater Than Constraint

Example:

```hcl
version = ">= 5.0.0"
```

Meaning:

```text
Version 5.0.0 or newer
```

---

# Less Than Constraint

Example:

```hcl
version = "< 6.0.0"
```

Meaning:

```text
Any Version Below 6.0.0
```

---

# Range Constraint

Example:

```hcl
version = ">= 5.0.0, < 6.0.0"
```

Meaning:

```text
Any 5.x Version
```

but not:

```text
6.0.0
```

---

# Pessimistic Constraint (~>)

## Most Important Exam Topic

Example:

```hcl
version = "~> 5.0"
```

Meaning:

```text
>= 5.0.0
< 6.0.0
```

Terraform may install:

```text
5.1.0
5.4.0
5.9.1
```

but NOT:

```text
6.0.0
```

---

## Another Example

```hcl
version = "~> 5.2.0"
```

Meaning:

```text
>= 5.2.0
< 5.3.0
```

Allowed:

```text
5.2.1
5.2.4
5.2.9
```

Not Allowed:

```text
5.3.0
```

---

## Exam Memory Trick

```text
~> Locks Left
Allows Right
```

Examples:

```text
~> 5.0
```

Locks:

```text
Major Version
```

---

```text
~> 5.2.0
```

Locks:

```text
Minor Version
```

---

# Version Constraint Examples

## Exact

```hcl
version = "1.2.0"
```

---

## Minimum Version

```hcl
version = ">= 1.2.0"
```

---

## Maximum Version

```hcl
version = "< 2.0.0"
```

---

## Range

```hcl
version = ">= 1.2.0, < 2.0.0"
```

---

## Pessimistic

```hcl
version = "~> 1.2"
```

---

# Module Upgrade Process

Terraform does not automatically upgrade modules.

Example:

Current:

```text
v1.0.0
```

Registry:

```text
v1.5.0
```

Terraform continues using installed version.

---

## Upgrade Command

```bash
terraform init -upgrade
```

Purpose:

```text
Upgrade Providers
Upgrade Modules
```

---

## Workflow

```text
Update Version Constraint
        │
        ▼
terraform init -upgrade
        │
        ▼
Download New Module Version
```

---

# Registry Module Example

```hcl
module "vpc" {

  source  = "terraform-aws-modules/vpc/aws"

  version = "~> 5.0"

}
```

Terraform selects:

```text
Latest Compatible 5.x Version
```

---

# Git Modules and Versioning

Git modules commonly use:

```text
Tags
Branches
Commits
```

---

## Tag Example

```hcl
module "vpc" {

  source =
  "git::https://github.com/company/vpc-module.git?ref=v1.0.0"

}
```

---

## Branch Example

```hcl
?ref=main
```

---

## Commit Example

```hcl
?ref=a1b2c3d
```

---

# How It Works

```text
Module Block
      │
      ▼
Version Constraint
      │
      ▼
terraform init
      │
      ▼
Terraform Resolves Version
      │
      ▼
Downloads Compatible Module
```

---

# Terraform Perspective

Example:

```hcl
module "network" {

  source  = "terraform-aws-modules/vpc/aws"

  version = "~> 5.0"

}
```

Terraform:

```text
Search Registry
      │
      ▼
Find Compatible Version
      │
      ▼
Download Module
```

---

# Real-World Example

Enterprise Policy:

```text
Allowed:
5.x
```

Not Allowed:

```text
6.x
```

Constraint:

```hcl
version = "~> 5.0"
```

Prevents unexpected major upgrades.

---

# Production Use Case

Best Practice:

Always pin module versions.

Example:

```hcl
version = "~> 5.0"
```

Benefits:

- Predictable Deployments
- Stable Infrastructure
- Controlled Upgrades
- Easier Troubleshooting

---

# Important Exam Points

- Registry modules support version argument.
- Semantic Versioning:

```text
MAJOR.MINOR.PATCH
```

- Major versions introduce breaking changes.
- Minor versions add features.
- Patch versions fix bugs.
- ~> is the pessimistic constraint.
- terraform init -upgrade upgrades modules.
- Version pinning is recommended.
- Git modules commonly use ?ref=.

---

# Common Exam Traps

### Trap 1

Question:

Which command upgrades modules?

Correct:

```bash
terraform init -upgrade
```

---

### Trap 2

Question:

What does ~> represent?

Correct:

Pessimistic Version Constraint.

---

### Trap 3

Question:

What part of SemVer represents breaking changes?

Correct:

MAJOR

---

### Trap 4

Question:

Should production modules be version-pinned?

Correct:

Yes.

---

### Trap 5

Question:

Does terraform init automatically upgrade modules?

Correct:

No.

Use:

```bash
terraform init -upgrade
```

---

# Interview Questions

### Why should Terraform modules be version-pinned?

To prevent unexpected changes and ensure predictable deployments.

### What is semantic versioning?

A versioning scheme using:

```text
MAJOR.MINOR.PATCH
```

### What does ~> mean?

Pessimistic version constraint.

### How do you upgrade modules?

```bash
terraform init -upgrade
```

### How are Git module versions commonly specified?

Using:

```text
?ref=
```

with tags, branches, or commits.

---

# Practice Questions

### Question 1

Which argument specifies a Terraform Registry module version?

A. source

B. provider

C. version

D. backend

**Answer:** C

---

### Question 2

What does the MAJOR version represent?

A. Bug Fixes

B. Breaking Changes

C. Documentation

D. Outputs

**Answer:** B

---

### Question 3

Which command upgrades modules?

A.

```bash
terraform apply
```

B.

```bash
terraform plan
```

C.

```bash
terraform init -upgrade
```

D.

```bash
terraform validate
```

**Answer:** C

---

### Question 4

What does:

```hcl
version = "~> 5.0"
```

allow?

A. Only 5.0.0

B. Any Version Below 5.0

C. Compatible 5.x Versions

D. Any Version

**Answer:** C

---

### Question 5

How are Git module versions commonly specified?

A. version

B. output

C. ?ref=

D. provider

**Answer:** C

---

## Related Objectives

- 5a Module Sources
- 5b Variable Scope
- 5c Use Modules in Configuration
- 2a Provider Versioning

---

## Key Takeaways

- Module versions should be pinned.
- Registry modules support the version argument.
- Semantic versioning uses MAJOR.MINOR.PATCH.
- MAJOR = Breaking Changes.
- MINOR = New Features.
- PATCH = Bug Fixes.
- ~> is the pessimistic version constraint.
- Use terraform init -upgrade to upgrade modules.
- Git modules commonly use ?ref= for version selection.
- Module versioning is a high-frequency Terraform Associate exam topic.
