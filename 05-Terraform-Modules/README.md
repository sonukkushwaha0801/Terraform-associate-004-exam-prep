# Terraform Modules

Terraform modules are reusable containers for Terraform configuration.

Modules allow teams to:

- Reduce code duplication
- Standardize infrastructure deployments
- Improve maintainability
- Share infrastructure patterns
- Build reusable platforms

Terraform modules are heavily used in production environments and are a frequently tested topic in the Terraform Associate (004) certification exam.

---

# Objectives

## 5a - Explain How Terraform Sources Modules

Understand where modules come from and how Terraform downloads them.

Module Sources:

- Local Paths
- Terraform Registry
- Git Repositories
- HTTP URLs
- Private Registries

---

## 5b - Describe Variable Scope Within Modules

Understand how variables and outputs work between:

- Root Module
- Child Modules

Learn:

- Variable Passing
- Module Inputs
- Module Outputs
- Scope Boundaries

---

## 5c - Use Modules in Configuration

Learn how to:

- Call Modules
- Pass Variables
- Consume Outputs
- Build Reusable Infrastructure

---

## 5d - Manage Module Versions

Understand:

- Version Constraints
- Module Upgrades
- Module Stability
- Registry Versioning

---

# Why Modules Matter

Without Modules:

```text
VPC Code
Copied 20 Times
```

With Modules:

```text
Reusable VPC Module
Used Everywhere
```

Benefits:

- DRY (Don't Repeat Yourself)
- Standardization
- Faster Deployments
- Easier Maintenance

---

# Root Module

The directory where Terraform commands are executed.

Example:

```bash
terraform init
terraform plan
terraform apply
```

executed from:

```text
project/
```

This becomes the:

```text
Root Module
```

---

# Child Module

Any module called by another module.

Example:

```text
project/
│
├── main.tf
│
└── modules/
     └── vpc/
```

The VPC module is a:

```text
Child Module
```

---

# Learning Outcomes

After completing this domain you should be able to:

- Explain module architecture
- Differentiate root and child modules
- Use module blocks
- Pass inputs into modules
- Consume outputs from modules
- Understand module sources
- Manage module versions
- Use Terraform Registry modules

---

# Objectives Covered

| Objective            | Status |
| -------------------- | ------ |
| 5a Module Sources    | ⬜      |
| 5b Variable Scope    | ⬜      |
| 5c Module Usage      | ⬜      |
| 5d Module Versioning | ⬜      |

---

# High-Probability Exam Topics

HashiCorp frequently tests:

- Root Module
- Child Module
- Module Block Syntax
- Module Source Types
- Terraform Registry
- Module Inputs
- Module Outputs
- Version Constraints
- Module Upgrades

---

# Recommended Study Order

1. Module Basics
2. Module Sources
3. Root vs Child Modules
4. Variable Scope
5. Module Inputs
6. Module Outputs
7. Module Versioning

---

# Domain Completion Checklist

- [ ] Completed 5a
- [ ] Completed 5b
- [ ] Completed 5c
- [ ] Completed 5d
- [ ] Completed Practice Questions
- [ ] Completed Revision Sheet
- [ ] Ready for Domain 6
