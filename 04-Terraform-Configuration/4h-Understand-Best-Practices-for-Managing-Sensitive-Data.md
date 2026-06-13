# Objective: 4h - Understand Best Practices for Managing Sensitive Data, Including Secrets Management with Vault

## Definition

Sensitive data is information that must be protected from unauthorized access.

Examples:

- Passwords
- API Keys
- Access Tokens
- Database Credentials
- SSH Private Keys
- Encryption Keys
- Cloud Credentials

Terraform provides mechanisms to reduce accidental exposure of sensitive information, but secure secrets management remains the responsibility of the user.

This objective focuses heavily on:

- Sensitive Variables
- Sensitive Outputs
- State File Security
- Secret Management
- HashiCorp Vault Integration

---

## Core Concepts

### What Is Sensitive Data?

Sensitive data includes any value that could:

- Grant access to systems
- Expose confidential information
- Allow privilege escalation
- Compromise infrastructure

Examples:

```text
AWS Access Keys
GitHub Tokens
Database Passwords
Vault Tokens
Private Keys
```

---

## The Main Security Challenge

Terraform configurations often require secrets.

Example:

```hcl
resource "aws_db_instance" "prod" {
  username = "admin"
  password = "SuperSecretPassword"
}
```

This is dangerous because:

- Password is visible in source code
- Password may be committed to Git
- Password may appear in logs

---

# Sensitive Variables

## Definition

Terraform variables can be marked as sensitive.

Example:

```hcl
variable "db_password" {
  type      = string
  sensitive = true
}
```

---

## Benefits

Terraform hides values from:

- CLI Output
- Terraform Apply Output
- Terraform Plan Output

Example:

```text
db_password = (sensitive value)
```

instead of:

```text
db_password = MyPassword123
```

---

## Important Limitation

Sensitive variables do NOT encrypt data.

They only hide values from output.

Terraform still stores values in state.

---

# Sensitive Outputs

Outputs can also be marked as sensitive.

Example:

```hcl
output "database_password" {
  value     = var.db_password
  sensitive = true
}
```

Terraform displays:

```text
database_password = (sensitive value)
```

---

## Purpose

Prevents accidental exposure.

Useful when outputs contain:

- Passwords
- Tokens
- Secrets
- Credentials

---

# Terraform State Security

## Critical Exam Concept

Terraform state frequently contains sensitive data.

Example:

```text
terraform.tfstate
```

may contain:

- Passwords
- Tokens
- Resource Metadata
- Connection Information

---

## Example Risk

Configuration:

```hcl
resource "aws_db_instance" "prod" {
  password = var.db_password
}
```

State File:

```json
{
  "password": "SuperSecretPassword"
}
```

Secret still exists in state.

---

## Exam Rule

### Sensitive Variables

Hide values in output.

### State File

Still stores values.

Many candidates miss this distinction.

---

# State Security Best Practices

## Avoid Local State for Production

Risk:

```text
terraform.tfstate
```

stored on laptops.

Better:

Remote Backends.

Examples:

- S3 Backend
- HCP Terraform
- Azure Storage
- GCS Backend

---

## Enable Encryption

Examples:

### AWS S3

```text
SSE-S3
SSE-KMS
```

### Azure

Storage Encryption

### GCP

Cloud Storage Encryption

---

## Restrict Access

Apply:

- Least Privilege
- IAM Policies
- RBAC Controls

Only authorized users should access state files.

---

# Secrets Management Approaches

## Bad Practice

Hardcoding secrets:

```hcl
password = "SuperSecretPassword"
```

---

## Better Practice

Variable Input:

```hcl
variable "db_password" {
  sensitive = true
}
```

---

## Preferred Practice

External Secret Management System.

Examples:

- HashiCorp Vault
- AWS Secrets Manager
- Azure Key Vault
- Google Secret Manager

---

# HashiCorp Vault

## Definition

HashiCorp Vault is a secrets management platform.

Purpose:

- Store Secrets Securely
- Generate Dynamic Credentials
- Control Access
- Audit Secret Usage

Vault is HashiCorp's recommended solution for secret management.

---

## Benefits

Vault provides:

- Encryption
- Dynamic Secrets
- Secret Rotation
- Access Policies
- Audit Logging

---

## Example

Instead of:

```text
Store Password In Terraform Code
```

Use:

```text
Store Password In Vault
```

Terraform retrieves it when needed.

---

# Vault Workflow

```text
Vault
 │
 ▼
Stores Secret
 │
 ▼
Terraform Reads Secret
 │
 ▼
Provision Resource
```

Secret remains centralized.

---

# Dynamic Secrets

## Definition

Vault can generate credentials automatically.

Example:

```text
Temporary Database User
```

Generated:

```text
username = temp-user
password = random-password
```

Expires automatically.

---

## Benefits

- Reduced Secret Exposure
- Automatic Rotation
- Improved Security

---

# Environment Variables

Terraform commonly receives secrets through environment variables.

Example:

```bash
export TF_VAR_db_password=MyPassword123
```

Terraform automatically loads:

```text
TF_VAR_<variable_name>
```

---

## Benefits

Avoids storing secrets directly in configuration files.

---

# .gitignore Best Practices

Never commit:

```text
terraform.tfstate
terraform.tfstate.backup
*.tfvars
```

Example:

```gitignore
*.tfvars
*.tfstate
*.tfstate.backup
```

---

# How It Works

```text
Secret
   │
   ▼
Vault / Secret Manager
   │
   ▼
Terraform Variable
   │
   ▼
Resource Creation
   │
   ▼
State Storage
```

---

# Terraform Perspective

Example:

Variable:

```hcl
variable "db_password" {
  sensitive = true
}
```

Resource:

```hcl
resource "aws_db_instance" "prod" {
  password = var.db_password
}
```

Output:

```hcl
output "password" {
  value     = var.db_password
  sensitive = true
}
```

Terraform hides output but still stores values in state.

---

# Real-World Example

Production Environment:

Secrets stored in:

```text
HashiCorp Vault
```

Terraform retrieves:

```text
Database Credentials
API Tokens
Cloud Secrets
```

No secrets committed to Git.

---

# Production Use Case

Enterprise Terraform Platforms commonly use:

- Vault
- AWS Secrets Manager
- Azure Key Vault
- Google Secret Manager

Combined with:

- Remote State
- State Encryption
- Access Controls

---

# Important Exam Points

- Sensitive variables hide output values.
- Sensitive outputs hide output values.
- Sensitive does NOT encrypt secrets.
- Terraform state may contain secrets.
- State files must be protected.
- Vault is HashiCorp's recommended secret-management solution.
- Avoid hardcoded secrets.
- Use remote backends for production.
- Use encrypted state storage.
- Use least-privilege access.

---

# Common Exam Traps

### Trap 1

Question:

Does sensitive = true encrypt secrets?

Correct:

No.

---

### Trap 2

Question:

Can secrets still exist in state files?

Correct:

Yes.

---

### Trap 3

Question:

What is HashiCorp's secret-management solution?

Correct:

Vault.

---

### Trap 4

Question:

Should secrets be hardcoded?

Correct:

No.

---

### Trap 5

Question:

Should terraform.tfstate be committed to Git?

Correct:

No.

---

### Trap 6

Question:

What is the preferred secret-management approach?

Correct:

Vault or external secret-management systems.

---

# Interview Questions

### What does sensitive = true do?

Hides values from Terraform output.

### Does sensitive encrypt secrets?

No.

### Where are secrets commonly exposed in Terraform?

State files.

### What is HashiCorp Vault?

A centralized secrets management platform.

### Why is Vault preferred?

It provides secure storage, dynamic secrets, access control, and auditing.

---

# Practice Questions

### Question 1

What does sensitive = true do?

A. Encrypts Data

B. Hides Values From Output

C. Removes Secrets

D. Deletes State

**Answer:** B

---

### Question 2

Where are secrets commonly stored by Terraform?

A. Providers

B. Modules

C. State Files

D. Outputs Only

**Answer:** C

---

### Question 3

Which HashiCorp product is designed for secret management?

A. Consul

B. Nomad

C. Vault

D. Packer

**Answer:** C

---

### Question 4

Which practice is recommended?

A. Hardcode Passwords

B. Commit Secrets To Git

C. Use Vault

D. Store Secrets In README Files

**Answer:** C

---

### Question 5

Which statement is TRUE?

A. Sensitive variables encrypt values.

B. State files never contain secrets.

C. Vault is used for secret management.

D. Terraform automatically rotates passwords.

**Answer:** C

---

## Related Objectives

- 2d Terraform State Management
- 4c Variables and Outputs
- 4g Custom Validation
- 6c Remote Backends
- 8d HCP Terraform Integration

---

## Key Takeaways

- Sensitive variables hide values from output.
- Sensitive outputs hide values from output.
- Sensitive does not encrypt data.
- Terraform state often contains secrets.
- State security is critical.
- Never hardcode secrets.
- Never commit state files to Git.
- Use remote encrypted backends.
- HashiCorp Vault is the recommended secret-management solution.
- Vault integration is a high-probability Terraform Associate exam topic.
