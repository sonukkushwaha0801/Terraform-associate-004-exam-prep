# Domain 2 Revision Sheet

## Terraform Fundamentals

### Objectives Covered

* 2a - Install and Version Terraform Providers
* 2b - Describe How Terraform Uses Providers
* 2c - Write Terraform Configuration Using Multiple Providers
* 2d - Explain How Terraform Uses and Manages State

---

# Terraform Providers

## Definition

Providers are plugins that allow Terraform to communicate with APIs and manage resources.

Examples:

* AWS
* AzureRM
* Google
* Kubernetes
* GitHub
* Cloudflare

---

## Provider Responsibilities

Providers:

✅ Communicate with APIs

✅ Create Resources

✅ Read Resources

✅ Update Resources

✅ Delete Resources

Providers perform CRUD operations.

---

## Terraform Core vs Provider

### Terraform Core

Responsible for:

* Reading Configuration
* Building Dependency Graph
* Comparing State
* Creating Execution Plans

---

### Providers

Responsible for:

* API Communication
* Resource Management

---

## Provider Architecture

```text
Terraform Configuration
            │
            ▼
      Terraform Core
            │
            ▼
         Provider
            │
            ▼
            API
            │
            ▼
     Infrastructure
```

---

# Provider Installation

Terraform installs providers using:

```bash
terraform init
```

This command:

* Downloads Providers
* Downloads Modules
* Initializes Backend
* Creates .terraform Directory

---

## Upgrade Providers

```bash
terraform init -upgrade
```

Used to upgrade installed providers.

---

## View Providers

```bash
terraform providers
```

Displays provider dependencies.

---

# Required Providers Block

Example:

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```

---

## Source Address

Format:

```text
<hostname>/<namespace>/<provider>
```

Example:

```text
hashicorp/aws
```

Purpose:

Identifies provider location.

---

## Version Constraint

Example:

```hcl
version = "~> 5.0"
```

Purpose:

Controls provider version selection.

Benefits:

* Consistency
* Predictability
* Stability

---

# Provider Configuration

Example:

```hcl
provider "aws" {
  region = "us-east-1"
}
```

Purpose:

Defines how Terraform connects to a platform.

---

# Multiple Providers

Terraform supports:

```text
AWS
Azure
Google
GitHub
```

within the same configuration.

Example:

```hcl
provider "aws" {}
provider "azurerm" {
  features {}
}
```

---

# Provider Aliases

Purpose:

Multiple configurations of the same provider.

Example:

```hcl
provider "aws" {
  region = "us-east-1"
}

provider "aws" {
  alias  = "west"
  region = "us-west-2"
}
```

---

## Resource Using Alias

```hcl
resource "aws_instance" "web" {
  provider = aws.west
}
```

---

# Common Alias Use Cases

* Multiple Regions
* Multiple Accounts
* Multi-Environment Deployments

---

# Terraform State

## Definition

Terraform state is a snapshot of managed infrastructure.

Default file:

```text
terraform.tfstate
```

---

## State Purpose

State tracks:

* Resources
* Resource Attributes
* Resource Relationships
* Infrastructure Metadata

---

## Why Terraform Uses State

State enables:

* Resource Tracking
* Change Detection
* Dependency Tracking
* Fast Planning

Without state Terraform cannot manage infrastructure effectively.

---

# Current State vs Desired State

Terraform compares:

```text
Current State
       vs
Desired State
```

Result:

```text
Execution Plan
```

Generated using:

```bash
terraform plan
```

---

# State Workflow

```text
Configuration
      │
      ▼
Desired State

      │

State File
      │

Current State

      ▼

Terraform Plan
      ▼

Apply Changes
      ▼

Update State
```

---

# State Commands

## List Resources

```bash
terraform state list
```

---

## Show Resource Details

```bash
terraform state show <resource>
```

Example:

```bash
terraform state show aws_instance.web
```

---

## Pull State

```bash
terraform state pull
```

---

# High-Probability Exam Facts

* Providers are plugins.
* Providers communicate with APIs.
* terraform init installs providers.
* terraform init -upgrade upgrades providers.
* required_providers defines source and version requirements.
* source identifies provider location.
* version controls provider selection.
* Provider aliases create multiple provider configurations.
* Terraform supports multiple providers.
* Terraform supports multi-cloud deployments.
* terraform.tfstate is the default state file.
* State tracks infrastructure.
* Terraform compares current state and desired state.
* State is updated after apply operations.

---

# Common Exam Traps

## Trap 1

Providers are:

✅ Plugins

❌ Modules

❌ Workspaces

❌ State Files

---

## Trap 2

terraform init:

✅ Downloads Providers

❌ Creates Resources

---

## Trap 3

Providers:

✅ Communicate With APIs

❌ Store State

---

## Trap 4

State:

✅ Tracks Infrastructure

❌ Stores Configuration Files

---

## Trap 5

Provider Alias:

✅ Multiple Configurations

❌ Multiple Resources

---

## Trap 6

terraform.tfstate:

✅ State File

❌ Terraform Configuration

---

## Trap 7

Terraform Compares:

✅ Current State vs Desired State

❌ Variables vs Outputs

---

## Trap 8

AWS + Azure:

✅ Multi-Cloud

Not related to provider aliases.

---

# 30-Second Final Revision

Remember:

* Providers = Plugins.
* terraform init installs providers.
* required_providers defines source and version.
* source = provider location.
* version = provider constraint.
* Aliases = multiple provider configurations.
* Terraform supports multiple providers.
* State = infrastructure snapshot.
* Default state file = terraform.tfstate.
* State tracks infrastructure.
* Terraform compares current state and desired state.
* terraform plan detects changes.
* terraform apply updates state.
* Providers and state are among the most tested Terraform Associate topics.
