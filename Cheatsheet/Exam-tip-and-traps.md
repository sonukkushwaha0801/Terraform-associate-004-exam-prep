# Terraform Associate (004) Exam Tips and Traps

## Purpose

This document focuses on:

* Common misconceptions
* Frequently tested concepts
* HashiCorp-style trick questions
* Exam elimination strategies

---

# Section 1 — Terraform Workflow Traps

### Trap

```text
terraform plan
```

changes infrastructure.

### Reality

```text
terraform plan
```

only previews changes.

---

### Trap

```text
terraform validate
```

checks cloud resources.

### Reality

It only validates configuration syntax and internal consistency.

---

# Section 2 — State Traps

### Trap

Terraform can operate without state.

### Reality

Terraform requires state.

---

### Trap

Remote state automatically provides locking.

### Reality

Locking depends on backend capabilities.

---

# Section 3 — Resource vs Data Traps

### Trap

Data sources create infrastructure.

### Reality

Data sources only read existing infrastructure.

---

### Trap

Resources only create infrastructure.

### Reality

Resources can create, update, and destroy.

---

# Section 4 — Import Traps

### Trap

Import creates Terraform configuration.

### Reality

Import updates state only.

Configuration must already exist.

---

# Section 5 — Sensitive Data Traps

### Trap

```hcl
sensitive = true
```

encrypts secrets.

### Reality

It only hides values from output.

Secrets may still exist in state.

---

# Section 6 — Module Traps

### Trap

Modules share variables automatically.

### Reality

Values must be passed explicitly.

---

### Trap

Updating module source automatically upgrades module.

### Reality

Run:

```bash
terraform init -upgrade
```

---

# Section 7 — HCP Terraform Traps

### Trap

Workspace = Environment

### Reality

Workspaces isolate state.

Environment strategy is an architectural choice.

---

### Trap

Sentinel scans Terraform code.

### Reality

Sentinel evaluates policies.

---

# Section 8 — Provider Traps

### Trap

Providers are built into Terraform.

### Reality

Providers are plugins.

---

### Trap

Multiple providers require multiple Terraform installations.

### Reality

Terraform downloads providers automatically.

---

# Section 9 — Dependency Traps

### Trap

Always use depends_on.

### Reality

Terraform prefers implicit dependencies.

---

# Section 10 — Top 25 Exam Traps

(rapid-fire section)

1. Plan ≠ Apply
2. Sensitive ≠ Encrypted
3. Data ≠ Resource
4. Import ≠ Configuration
5. Workspace ≠ Environment
6. Validate ≠ Deploy
7. Fmt ≠ Validate
8. Local Backend ≠ Remote Backend
   ...
9. Sentinel ≠ Secret Management

---

# Exam Strategy

## First Pass

Answer immediately known questions.

---

## Second Pass

Review scenario questions.

---

## Third Pass

Review marked questions.

---

## Elimination Technique

Eliminate answers that:

* contradict Terraform workflow
* confuse resources and data
* confuse sensitive and encrypted
* claim plan changes infrastructure

---

# Final Reminder

Most Terraform Associate failures come from:

* Reading too quickly
* Missing keywords
* Confusing similar concepts

Slow down and identify exactly what Terraform component the question is testing.
