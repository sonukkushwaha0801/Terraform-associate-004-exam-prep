# Last-Minute Prep Notes

> Terraform Associate (004)
>
> Read this 10–15 minutes before the exam.

---

# Terraform Workflow

```text
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
terraform destroy
```

Remember:

```text
Plan → Preview

Apply → Execute
```

---

# Resource vs Data

```text
resource
=
Create / Modify / Destroy

data
=
Read Existing Infrastructure
```

Exam Trap:

```text
Data Sources
DO NOT
Create Resources
```

---

# Variables

Most Common Types:

```text
string

number

bool

list

map

object
```

---

# Outputs

Used to expose values from Terraform.

Example:

```text
Public IP

Resource ID

ARN
```

---

# Dependencies

Implicit:

```text
resource.attribute
```

Explicit:

```text
depends_on
```

Use explicit dependencies only when necessary.

---

# Providers

Remember:

```text
Providers
=
Plugins
```

Terraform downloads providers during:

```text
terraform init
```

---

# Modules

Benefits:

```text
Reuse

Consistency

Standardization
```

Remember:

```text
Modules
Can Be Versioned
```

---

# State

State File:

```text
terraform.tfstate
```

Purpose:

```text
Configuration
↔
Real Infrastructure
```

---

# State Locking

Purpose:

```text
Prevent Concurrent State Modification
```

---

# Backends

Common Backends:

```text
local

s3

azurerm

gcs

remote
```

---

# Import

Command:

```text
terraform import
```

Remember:

```text
Import
Updates State

Import
Does NOT Generate Configuration
```

---

# Drift

Definition:

```text
Infrastructure Changed
Outside Terraform
```

Detect:

```text
terraform plan
```

Correct:

```text
terraform apply
```

---

# Sensitive Data

Example:

```hcl
sensitive = true
```

Exam Trap:

```text
Sensitive
≠
Encrypted
```

---

# Vault

Purpose:

```text
Secrets Management
```

Examples:

```text
Passwords

Tokens

API Keys
```

---

# HCP Terraform

Know:

```text
Organization

Project

Workspace
```

---

# HCP Terraform Features

```text
Remote State

Remote Execution

Private Registry

Run History

Sentinel

Run Tasks
```

---

# Sentinel

Purpose:

```text
Policy as Code
```

Example:

```text
Mandatory Tags

Encryption Required

Approved Regions
```

---

# Most Important Commands

```bash
terraform init

terraform fmt

terraform validate

terraform plan

terraform apply

terraform destroy

terraform show

terraform output

terraform import

terraform state list

terraform state show
```

---

# Top Exam Traps

```text
terraform plan
≠
terraform apply
```

```text
resource
≠
data
```

```text
sensitive
≠
encrypted
```

```text
import
≠
configuration
```

```text
workspace
≠
environment
```

```text
terraform validate
≠
deploy infrastructure
```

```text
terraform fmt
≠
validate configuration
```

```text
remote state
≠
automatic locking
```

---

# 30-Second Final Review

✅ Terraform Workflow

✅ Resource vs Data

✅ Variables

✅ Outputs

✅ Modules

✅ State

✅ Backends

✅ State Locking

✅ Import

✅ Drift

✅ Sensitive Data

✅ Vault

✅ HCP Terraform

✅ Sentinel

✅ Common Commands

---

# Final Reminder

Read every question carefully.

Most Terraform Associate questions test:

```text
Difference Between Similar Concepts
```

Especially:

```text
Plan vs Apply

Resource vs Data

Sensitive vs Encrypted

Import vs Configuration

Workspace vs Environment
```

If two answers look similar, focus on what Terraform actually does—not what sounds reasonable.
