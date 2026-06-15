# Terraform Architecture Solutions

> Companion Guide for:
>
> `Interview-Preparation/Terraform-Architecture-Questions.md`
>
> Coverage:
>
> * Environment Architecture
> * Environment Isolation
> * Change Promotion
> * Secrets Management
> * Drift Prevention

---

# Question 1

## Scenario

How would you design Terraform architecture for:

* Development
* Staging
* Production

while maintaining strict isolation?

---

## What Is Being Tested?

* Environment Architecture
* State Management
* Terraform Best Practices

---

## Solution

Each environment should have:

* Separate Terraform state
* Separate backend configuration
* Separate variables
* Separate deployment pipeline

Infrastructure logic should be shared through modules.

---

## Architecture

```text
terraform-live/
│
├── dev/
├── stage/
└── prod/

terraform-modules/
│
├── networking/
├── compute/
└── security/
```

---

## Example Configuration

```hcl
module "networking" {
  source = "../../terraform-modules/networking"

  environment = "dev"
}
```

---

## Commands

```bash
terraform init

terraform plan

terraform apply
```

---

## Important Exam Points

* Separate environments reduce blast radius.
* Modules reduce duplication.
* Production should never share state with development.

---

## Common Mistakes

* Single state file for all environments.
* Copy-paste infrastructure.
* Shared backend for everything.

---

## Key Takeaway

Environment isolation starts with separate state and shared reusable modules.

---

# Question 2

## Scenario

Would you use:

* Separate repositories
* Separate directories
* Separate workspaces

for environment management?

Why?

---

## What Is Being Tested?

* Environment Design
* Terraform Organization

---

## Solution

For Terraform Associate level:

Recommended:

```text
Single Repository
+
Separate Environment Directories
```

Example:

```text
environments/
├── dev
├── stage
└── prod
```

---

## Architecture

```text
Git Repository
│
├── dev
├── stage
└── prod
```

---

## Example

```text
terraform-live/
├── dev
├── stage
└── prod
```

---

## Important Exam Points

* Directories provide isolation.
* Easier to manage than multiple repositories.
* Common enterprise approach.

---

## Common Mistakes

* Everything inside one directory.
* Single state for all environments.

---

## Key Takeaway

Separate directories are usually the simplest and safest environment strategy.

---

# Question 3

## Scenario

How would you promote infrastructure changes from Development to Production?

---

## What Is Being Tested?

* Terraform Workflow
* Change Management

---

## Solution

Use a controlled promotion process.

---

## Workflow

```text
Development
     ↓
Testing
     ↓
Staging
     ↓
Approval
     ↓
Production
```

---

## Commands

Development:

```bash
terraform plan
terraform apply
```

Production:

```bash
terraform plan
```

Review before:

```bash
terraform apply
```

---

## Important Exam Points

* Never deploy directly to production.
* Review plans before production applies.
* Use approval processes.

---

## Common Mistakes

* Skipping staging.
* Direct production deployment.

---

## Key Takeaway

Promote infrastructure through environments instead of deploying directly to production.

---

# Question 4

## Scenario

How would you prevent Development engineers from affecting Production infrastructure?

---

## What Is Being Tested?

* Access Control
* Governance

---

## Solution

Use:

* Separate AWS Accounts
* Separate State Files
* IAM Permissions
* Approval Workflows

---

## Architecture

```text
Developers
     ↓
Dev Account

Production Team
     ↓
Prod Account
```

---

## Example IAM Concept

```text
Developer Role
=
Dev Only

Production Role
=
Restricted
```

---

## Important Exam Points

* Access control is critical.
* Production should have additional protections.

---

## Common Mistakes

* Shared credentials.
* Shared accounts.

---

## Key Takeaway

Access control is the first line of defense against accidental production changes.

---

# Question 5

## Scenario

How would you structure state files across environments?

---

## What Is Being Tested?

* State Management
* Backend Design

---

## Solution

Each environment should maintain independent state.

---

## Architecture

```text
Dev State
Stage State
Prod State
```

---

## Example Backend Layout

```text
terraform-state/
├── dev.tfstate
├── stage.tfstate
└── prod.tfstate
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket = "terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}
```

---

## Commands

```bash
terraform state list

terraform state show
```

---

## Important Exam Points

* Separate environments require separate state.
* Remote state is preferred.

---

## Common Mistakes

* One state file for everything.

---

## Key Takeaway

State isolation is environment isolation.

---

# Question 6

## Scenario

How would you design Terraform architecture for a regulated environment requiring change approvals?

---

## What Is Being Tested?

* Governance
* Compliance

---

## Solution

Implement approval gates before production deployment.

---

## Workflow

```text
Code Change
      ↓
Pull Request
      ↓
Review
      ↓
Terraform Plan
      ↓
Approval
      ↓
Terraform Apply
```

---

## Commands

```bash
terraform validate

terraform plan
```

---

## Important Exam Points

* Compliance requires traceability.
* Reviews reduce deployment risk.

---

## Common Mistakes

* Direct production applies.
* No audit trail.

---

## Key Takeaway

Regulated environments require controlled and auditable deployments.

---

# Question 7

## Scenario

What governance controls would you implement around production deployments?

---

## What Is Being Tested?

* Governance
* Operational Controls

---

## Solution

Implement:

* Pull Requests
* Code Reviews
* Protected Branches
* Approval Gates
* Remote State

---

## Architecture

```text
Developer
     ↓
Pull Request
     ↓
Review
     ↓
Apply
```

---

## Important Exam Points

* Governance reduces operational risk.
* Production changes should be reviewed.

---

## Common Mistakes

* Allowing direct commits to production branches.

---

## Key Takeaway

Production infrastructure should always be controlled by governance processes.

---

# Question 8

## Scenario

How would you manage environment-specific configuration without duplicating Terraform code?

---

## What Is Being Tested?

* Variables
* Modules

---

## Solution

Reuse modules and pass environment-specific variables.

---

## Example Variable

```hcl
variable "instance_type" {
  type = string
}
```

---

## Dev

```hcl
instance_type = "t3.micro"
```

---

## Prod

```hcl
instance_type = "t3.large"
```

---

## Architecture

```text
Shared Module
      ↓
Environment Variables
      ↓
Environment Deployment
```

---

## Important Exam Points

* Modules reduce duplication.
* Variables customize deployments.

---

## Common Mistakes

* Separate codebases per environment.

---

## Key Takeaway

Use modules for reuse and variables for customization.

---

# Question 9

## Scenario

How would you handle secrets differently across environments?

---

## What Is Being Tested?

* Security
* Secrets Management

---

## Solution

Store secrets outside Terraform code.

Use:

* Vault
* AWS Secrets Manager
* Azure Key Vault

---

## Architecture

```text
Terraform
     ↓
Vault
     ↓
Secret Retrieval
```

---

## Example

```hcl
variable "db_password" {
  sensitive = true
}
```

---

## Important Exam Points

* Never hardcode secrets.
* Sensitive variables do not encrypt data.

---

## Common Mistakes

* Secrets in Git.
* Passwords in variables.tf.

---

## Key Takeaway

Secrets should be centrally managed and retrieved securely.

---

# Question 10

## Scenario

What architecture patterns reduce environment drift?

---

## What Is Being Tested?

* Drift Management
* Governance

---

## Solution

Terraform should be the single source of truth.

---

## Architecture

```text
Git
 ↓
Terraform
 ↓
Infrastructure
```

---

## Controls

* Pull Requests
* Code Reviews
* CI/CD
* Restricted Console Access

---

## Commands

```bash
terraform plan
```

Detect drift:

```bash
terraform plan
```

Correct drift:

```bash
terraform apply
```

---

## Important Exam Points

* Drift occurs when infrastructure changes outside Terraform.
* Terraform detects drift during planning.

---

## Common Mistakes

* Manual cloud changes.
* Ignoring plan output.

---

## Key Takeaway

Prevent drift by ensuring all infrastructure changes flow through Terraform.

---

# Question 11

## Scenario

Design a remote-state architecture for:

* Multiple Teams
* Multiple AWS Accounts
* Multiple Environments

---

## What Is Being Tested?

* Remote State
* Backend Architecture
* State Isolation

---

## Solution

Separate state files by:

* Account
* Environment
* Application

Never use one shared state file.

---

## Architecture

```text
AWS Account A
├── Dev State
├── Stage State
└── Prod State

AWS Account B
├── Dev State
├── Stage State
└── Prod State
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-state"
    key            = "prod/app1/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
  }
}
```

---

## Commands

```bash
terraform init

terraform state list
```

---

## Important Exam Points

* State should be isolated.
* Remote state supports collaboration.
* State locking prevents corruption.

---

## Common Mistakes

* Shared state across teams.
* Local state in production.

---

## Key Takeaway

State boundaries should align with environment and ownership boundaries.

---

# Question 12

## Scenario

What risks exist if multiple applications share the same state file?

---

## What Is Being Tested?

* State Isolation
* Operational Risk

---

## Solution

Sharing state increases blast radius.

A single issue can affect multiple applications.

---

## Architecture

```text
Bad Design

App1
App2
App3
 ↓
Shared State
```

---

## Risks

* Accidental deletions
* Large plans
* Complex troubleshooting
* Team conflicts

---

## Commands

```bash
terraform plan
```

Large shared state often produces noisy plans.

---

## Important Exam Points

* Smaller state files are easier to manage.
* Isolation improves safety.

---

## Common Mistakes

* One state file for an entire department.

---

## Key Takeaway

One application should not be able to impact another application's state.

---

# Question 13

## Scenario

How would you structure Terraform state for hundreds of applications?

---

## What Is Being Tested?

* Scalability
* State Organization

---

## Solution

Separate state by:

* Environment
* Application

---

## Architecture

```text
prod/
├── app1.tfstate
├── app2.tfstate
├── app3.tfstate

stage/
├── app1.tfstate
├── app2.tfstate
├── app3.tfstate
```

---

## Example Backend Keys

```text
prod/app1/terraform.tfstate

prod/app2/terraform.tfstate

prod/app3/terraform.tfstate
```

---

## Important Exam Points

* Smaller state files scale better.
* Easier recovery and troubleshooting.

---

## Common Mistakes

* Monolithic state files.

---

## Key Takeaway

Scale Terraform by splitting state logically.

---

# Question 14

## Scenario

How would you design state isolation boundaries?

---

## What Is Being Tested?

* State Design
* Infrastructure Organization

---

## Solution

Use isolation based on:

* Team
* Environment
* Application

---

## Architecture

```text
Team A
 ├── Dev
 ├── Stage
 └── Prod

Team B
 ├── Dev
 ├── Stage
 └── Prod
```

Each owns separate state.

---

## Commands

```bash
terraform state list
```

Used to verify ownership boundaries.

---

## Important Exam Points

* State isolation reduces blast radius.
* Recovery becomes easier.

---

## Common Mistakes

* Cross-team shared state.

---

## Key Takeaway

State ownership should match resource ownership.

---

# Question 15

## Scenario

How would you recover from state corruption?

---

## What Is Being Tested?

* Disaster Recovery
* State Management

---

## Solution

Restore a known-good state version.

Validate infrastructure before continuing.

---

## Recovery Workflow

```text
State Corruption
      ↓
Restore Backup
      ↓
terraform plan
      ↓
Validate
      ↓
terraform apply
```

---

## Commands

```bash
terraform state list

terraform plan
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-state"
    key            = "prod/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
  }
}
```

---

## Important Exam Points

* Versioned remote state is preferred.
* Backups are critical.

---

## Common Mistakes

* No state backup strategy.
* Manual state editing.

---

## Key Takeaway

Recovery starts with backups and validated state restoration.

---

# Question 16

## Scenario

What backup strategy would you implement for Terraform state?

---

## What Is Being Tested?

* State Protection
* Business Continuity

---

## Solution

Use:

* Remote backend
* Versioning
* Automated backups

---

## Architecture

```text
Terraform
     ↓
S3 Backend
     ↓
Versioning
     ↓
Backup
```

---

## Example AWS Setup

```text
S3 Bucket
+
Versioning Enabled
+
DynamoDB Locking
```

---

## Important Exam Points

* Versioning improves recovery.
* State is critical data.

---

## Common Mistakes

* Single copy of state.

---

## Key Takeaway

Treat Terraform state like a production database.

---

# Question 17

## Scenario

How would you test Terraform state recovery?

---

## What Is Being Tested?

* Disaster Recovery Validation

---

## Solution

Perform recovery drills.

Simulate state loss and restore from backup.

---

## Workflow

```text
Backup
 ↓
Delete Test State
 ↓
Restore
 ↓
terraform plan
 ↓
Verify
```

---

## Commands

```bash
terraform plan

terraform state list
```

---

## Important Exam Points

* Backups must be tested.
* Untested recovery plans are unreliable.

---

## Common Mistakes

* Assuming backups work.

---

## Key Takeaway

Recovery testing is as important as backup creation.

---

# Question 18

## Scenario

How would you reduce state blast radius?

---

## What Is Being Tested?

* State Architecture
* Risk Reduction

---

## Solution

Break infrastructure into smaller states.

---

## Architecture

```text
Networking State

Compute State

Database State
```

instead of:

```text
Everything
↓
One State File
```

---

## Benefits

* Faster plans
* Easier recovery
* Reduced impact

---

## Important Exam Points

* Smaller state files reduce operational risk.

---

## Common Mistakes

* Giant monolithic state.

---

## Key Takeaway

Reduce blast radius through state separation.

---

# Question 19

## Scenario

How would you design state management for a Platform Engineering team?

---

## What Is Being Tested?

* Platform Thinking
* Terraform Governance

---

## Solution

Provide centrally managed state.

Teams consume infrastructure safely.

---

## Architecture

```text
Platform Team
      ↓
Remote State Platform
      ↓
Application Teams
```

---

## Features

* Remote state
* State locking
* Versioning
* Backups

---

## Commands

```bash
terraform init

terraform state list
```

---

## Important Exam Points

* Platform teams provide standards.
* Teams should not manage state manually.

---

## Common Mistakes

* Decentralized unmanaged state.

---

## Key Takeaway

State management should be standardized across teams.

---

# Question 20

## Scenario

Would you prefer HCP Terraform or S3 + DynamoDB?

Explain trade-offs.

---

## What Is Being Tested?

* Backend Knowledge
* Terraform Ecosystem

---

## Solution

### HCP Terraform

Provides:

* Remote state
* Locking
* Runs
* Governance
* Collaboration

### S3 + DynamoDB

Provides:

* Remote state
* Locking
* Lower cost
* Greater operational responsibility

---

## Comparison

| Feature             | HCP Terraform | S3 + DynamoDB |
| ------------------- | ------------- | ------------- |
| Remote State        | Yes           | Yes           |
| Locking             | Yes           | Yes           |
| Governance          | Yes           | Limited       |
| Run History         | Yes           | No            |
| Collaboration       | Yes           | Limited       |
| Management Overhead | Low           | Higher        |

---

## Example S3 Backend

```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-state"
    key            = "prod/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
  }
}
```

---

## Important Exam Points

* HCP Terraform provides additional platform capabilities.
* S3 + DynamoDB is a common AWS backend solution.

---

## Common Mistakes

* Assuming all remote backends provide the same features.

---

## Key Takeaway

Choose HCP Terraform for collaboration and governance. Choose S3 + DynamoDB when you want greater control and already operate AWS infrastructure.

---

# Question 21

## Scenario

How would you design reusable Terraform modules for hundreds of teams?

---

## What Is Being Tested?

* Module Design
* Reusability
* Standardization

---

## Solution

Create small, focused modules.

Examples:

```text
networking
compute
database
security
monitoring
```

Each module should solve one problem well.

---

## Architecture

```text
Application Team
      ↓
Shared Module
      ↓
AWS Resources
```

---

## Example

```hcl
module "vpc" {
  source = "company/network/aws"
}
```

---

## Important Exam Points

* Modules promote reuse.
* Modules reduce duplication.
* Modules improve consistency.

---

## Common Mistakes

* Giant modules.
* Copy-paste infrastructure.

---

## Key Takeaway

Build small reusable modules instead of large generic modules.

---

# Question 22

## Scenario

How would you organize a module repository?

---

## What Is Being Tested?

* Module Organization
* Repository Structure

---

## Solution

Separate modules logically.

---

## Repository Structure

```text
terraform-modules/

├── networking/
├── compute/
├── security/
├── database/
└── monitoring/
```

---

## Example

```text
networking/
├── main.tf
├── variables.tf
├── outputs.tf
└── README.md
```

---

## Important Exam Points

* Modules should be self-contained.
* Documentation is important.

---

## Common Mistakes

* Mixing unrelated resources.

---

## Key Takeaway

Organize modules by functionality.

---

# Question 23

## Scenario

How would you version modules?

---

## What Is Being Tested?

* Module Lifecycle
* Version Management

---

## Solution

Use Semantic Versioning.

---

## Example

```text
v1.0.0
v1.1.0
v1.2.0
v2.0.0
```

---

## Module Usage

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "~> 5.0"
}
```

---

## Important Exam Points

* Version pinning improves stability.
* Major versions may introduce breaking changes.

---

## Common Mistakes

* Using latest version in production.

---

## Key Takeaway

Always version modules and pin versions in production.

---

# Question 24

## Scenario

How would you prevent breaking changes from impacting production environments?

---

## What Is Being Tested?

* Change Management
* Module Governance

---

## Solution

Test module changes before production rollout.

---

## Workflow

```text
Module Change
      ↓
Development
      ↓
Testing
      ↓
Staging
      ↓
Production
```

---

## Commands

```bash
terraform validate

terraform plan
```

---

## Version Example

```hcl
module "network" {
  source  = "./modules/network"
  version = "1.2.0"
}
```

---

## Important Exam Points

* Pin versions.
* Test before upgrades.

---

## Common Mistakes

* Immediate production upgrades.

---

## Key Takeaway

Version control and testing reduce deployment risk.

---

# Question 25

## Scenario

How many input variables are too many?

Why?

---

## What Is Being Tested?

* Module Design
* Maintainability

---

## Solution

There is no fixed number.

However:

```text
5–20 Variables
```

is usually manageable.

If a module contains:

```text
50+
Variables
```

review the design.

---

## Indicators

The module may be:

* Too generic
* Doing too much
* Difficult to use

---

## Example

Bad:

```text
Mega Module
├── VPC
├── EC2
├── RDS
├── IAM
├── Monitoring
└── Security
```

---

## Better

```text
VPC Module

EC2 Module

RDS Module
```

---

## Key Takeaway

Large numbers of variables often indicate poor module boundaries.

---

# Question 26

## Scenario

How would you balance flexibility versus standardization in module design?

---

## What Is Being Tested?

* Module Design Principles

---

## Solution

Provide sensible defaults while allowing customization.

---

## Example

```hcl
variable "instance_type" {
  default = "t3.micro"
}
```

Users can override when needed.

---

## Architecture

```text
Standard Defaults
       +
Optional Overrides
```

---

## Important Exam Points

* Modules should be easy to consume.
* Avoid excessive configuration.

---

## Common Mistakes

* Making every setting configurable.

---

## Key Takeaway

Optimize for usability, not maximum flexibility.

---

# Question 27

## Scenario

What module anti-patterns have you encountered?

---

## What Is Being Tested?

* Module Best Practices

---

## Common Anti-Patterns

### Mega Modules

```text
Everything
In
One Module
```

---

### Hardcoded Values

```hcl
region = "us-east-1"
```

---

### No Versioning

---

### Poor Documentation

---

### Copy-Paste Modules

---

## Important Exam Points

* Modules should be reusable.
* Documentation matters.

---

## Key Takeaway

Simple, documented, versioned modules scale best.

---

# Question 28

## Scenario

How would you design a module approval process?

---

## What Is Being Tested?

* Governance
* Module Lifecycle

---

## Solution

Use code review before publishing modules.

---

## Workflow

```text
Developer
    ↓
Pull Request
    ↓
Review
    ↓
Testing
    ↓
Release
```

---

## Commands

```bash
terraform fmt

terraform validate
```

---

## Governance Controls

* Code Reviews
* CI Validation
* Version Tags

---

## Key Takeaway

Approved modules improve consistency and security.

---

# Question 29

## Scenario

How would you secure shared modules?

---

## What Is Being Tested?

* Module Security

---

## Solution

Implement:

* Access controls
* Version control
* Security reviews

---

## Workflow

```text
Module Code
     ↓
Review
     ↓
Security Validation
     ↓
Release
```

---

## Example Controls

* Protected branches
* Pull requests
* Signed releases

---

## Important Exam Points

* Shared modules affect many environments.
* Module security is critical.

---

## Common Mistakes

* Direct commits to module repositories.

---

## Key Takeaway

Secure modules before they reach production environments.

---

# Question 30

## Scenario

How would you distribute modules across an enterprise?

---

## What Is Being Tested?

* Module Distribution
* Enterprise Terraform

---

## Solution

Use:

* Terraform Registry
* Private Module Registry
* Git Repositories

---

## Architecture

```text
Module Registry
        ↓
Teams
        ↓
Terraform Deployments
```

---

## Example

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "~> 5.0"
}
```

---

## Commands

```bash
terraform init
```

Downloads module dependencies.

---

## Important Exam Points

* Registries simplify reuse.
* Versioning improves reliability.

---

## Common Mistakes

* Sharing modules manually.

---

## Key Takeaway

A centralized module distribution strategy improves consistency and scalability.

---

# Question 31

## Scenario

Design Terraform architecture for:

* 50 AWS Accounts
* Multiple Regions
* Hundreds of Applications

---

## What Is Being Tested?

* Multi-Account Architecture
* Scalability
* Environment Design

---

## Solution

Separate infrastructure by:

* AWS Account
* Environment
* Application

Use reusable modules.

---

## Architecture

```text
Organization
│
├── Account-A
│   ├── Dev
│   ├── Stage
│   └── Prod
│
├── Account-B
│   ├── Dev
│   ├── Stage
│   └── Prod
│
└── Account-C
```

---

## Example Structure

```text
terraform-live/

├── account-a/
├── account-b/
└── account-c/

terraform-modules/
```

---

## Important Exam Points

* Separate state per account.
* Use reusable modules.
* Avoid monolithic deployments.

---

## Common Mistakes

* Single account for everything.
* Shared state across accounts.

---

## Key Takeaway

Separate accounts improve security, scalability, and governance.

---

# Question 32

## Scenario

How would you organize repositories?

---

## What Is Being Tested?

* Repository Design
* Terraform Organization

---

## Solution

Separate modules from environment deployments.

---

## Example Structure

```text
terraform-modules/

terraform-live/

terraform-platform/
```

---

## Architecture

```text
Modules Repo
      ↓
Environment Repo
      ↓
Deployments
```

---

## Important Exam Points

* Reuse modules.
* Keep deployment code separate.

---

## Common Mistakes

* Mixing modules and environments together.

---

## Key Takeaway

Separate reusable code from environment-specific code.

---

# Question 33

## Scenario

How would you structure provider configurations?

---

## What Is Being Tested?

* Providers
* Multi-Account Deployments

---

## Solution

Use provider aliases.

---

## Example

```hcl
provider "aws" {
  region = "us-east-1"
}

provider "aws" {
  alias  = "prod"
  region = "us-west-2"
}
```

---

## Module Usage

```hcl
module "prod_vpc" {
  source = "./modules/vpc"

  providers = {
    aws = aws.prod
  }
}
```

---

## Important Exam Points

* Aliases support multiple provider instances.
* Useful for multi-region deployments.

---

## Common Mistakes

* One provider configuration for everything.

---

## Key Takeaway

Provider aliases enable flexible multi-account and multi-region architectures.

---

# Question 34

## Scenario

How would you manage IAM roles for Terraform?

---

## What Is Being Tested?

* Security
* Access Control

---

## Solution

Use dedicated IAM roles.

Avoid personal user credentials.

---

## Architecture

```text
Terraform
     ↓
IAM Role
     ↓
AWS Resources
```

---

## Example

```hcl
provider "aws" {
  assume_role {
    role_arn = "arn:aws:iam::123456789012:role/TerraformRole"
  }
}
```

---

## Important Exam Points

* Least privilege principle.
* Role assumption is preferred.

---

## Common Mistakes

* Long-lived access keys.

---

## Key Takeaway

Terraform should operate through dedicated IAM roles.

---

# Question 35

## Scenario

How would you implement account-level isolation?

---

## What Is Being Tested?

* AWS Architecture
* Security Boundaries

---

## Solution

Use separate AWS accounts.

---

## Example

```text
AWS Organization

├── Dev Account
├── Stage Account
└── Prod Account
```

---

## Benefits

* Security isolation
* Billing separation
* Reduced blast radius

---

## Important Exam Points

* Account boundaries are strong security boundaries.

---

## Common Mistakes

* Mixing all environments in one account.

---

## Key Takeaway

Separate accounts provide stronger isolation than tags or naming conventions.

---

# Question 36

## Scenario

How would you manage shared networking across accounts?

---

## What Is Being Tested?

* Networking Architecture
* Shared Infrastructure

---

## Solution

Centralize networking resources.

---

## Architecture

```text
Networking Account
        ↓
Shared Services
        ↓
Application Accounts
```

---

## Example Components

* Transit Gateway
* Shared VPC
* DNS Services

---

## Important Exam Points

* Shared services reduce duplication.
* Centralized networking simplifies management.

---

## Common Mistakes

* Duplicating networking everywhere.

---

## Key Takeaway

Shared infrastructure should be centrally managed.

---

# Question 37

## Scenario

How would you implement governance consistently across all accounts?

---

## What Is Being Tested?

* Governance
* Standardization

---

## Solution

Implement:

* Shared Modules
* CI/CD
* Sentinel Policies
* Access Controls

---

## Architecture

```text
Policy
     ↓
Terraform
     ↓
All Accounts
```

---

## Example Controls

```text
Encryption Required

Mandatory Tags

Approved Regions
```

---

## Important Exam Points

* Governance should be automated.
* Policies improve consistency.

---

## Common Mistakes

* Manual governance reviews.

---

## Key Takeaway

Automated governance scales better than manual reviews.

---

# Question 38

## Scenario

How would you manage Terraform deployments across multiple regions?

---

## What Is Being Tested?

* Multi-Region Deployments
* Providers

---

## Solution

Use provider aliases.

Deploy resources region-by-region.

---

## Example

```hcl
provider "aws" {
  alias  = "east"
  region = "us-east-1"
}

provider "aws" {
  alias  = "west"
  region = "us-west-2"
}
```

---

## Architecture

```text
Terraform
   ↓
us-east-1

Terraform
   ↓
us-west-2
```

---

## Commands

```bash
terraform plan

terraform apply
```

---

## Important Exam Points

* Provider aliases support multi-region deployments.

---

## Common Mistakes

* Hardcoding regions.

---

## Key Takeaway

Provider aliases are the standard Terraform approach for multi-region deployments.

---

# Question 39

## Scenario

How would you structure CI/CD pipelines for multi-account deployments?

---

## What Is Being Tested?

* Automation
* Deployment Architecture

---

## Solution

Separate pipelines by environment.

---

## Architecture

```text
GitHub
    ↓
Terraform Validate
    ↓
Terraform Plan
    ↓
Approval
    ↓
Terraform Apply
```

---

## Example Commands

```bash
terraform fmt

terraform validate

terraform plan

terraform apply
```

---

## Environment Promotion

```text
Dev
 ↓
Stage
 ↓
Prod
```

---

## Important Exam Points

* Validate before apply.
* Review plans before production changes.

---

## Common Mistakes

* Direct production deployments.

---

## Key Takeaway

CI/CD improves consistency and reduces deployment risk.

---

# Question 40

## Scenario

How would you audit infrastructure changes across all accounts?

---

## What Is Being Tested?

* Governance
* Auditability

---

## Solution

Use:

* Git History
* Pull Requests
* CI/CD Logs
* HCP Terraform Run History

---

## Architecture

```text
Developer
     ↓
Git Commit
     ↓
Pull Request
     ↓
Terraform Run
     ↓
Audit Trail
```

---

## Example Evidence Sources

```text
GitHub

HCP Terraform

CloudTrail

CI/CD Logs
```

---

## Important Exam Points

* Infrastructure should be version controlled.
* Audit trails support compliance.

---

## Common Mistakes

* Manual undocumented changes.

---

## Key Takeaway

Every infrastructure change should be traceable and auditable.

---

# Question 41

## Scenario

How would you implement Policy-as-Code?

---

## What Is Being Tested?

* Governance
* Policy Enforcement

---

## Solution

Use policy engines to automatically validate Terraform deployments.

For HCP Terraform:

```text id="g41a"
Sentinel
```

For Open Source environments:

```text id="g41b"
OPA (Open Policy Agent)
```

---

## Architecture

```text id="g41c"
Terraform Plan
      ↓
Policy Check
      ↓
Pass / Fail
      ↓
Apply
```

---

## Important Exam Points

* Policy-as-Code automates governance.
* Policies are evaluated before deployment.

---

## Common Mistakes

* Manual policy reviews.
* No automated enforcement.

---

## Key Takeaway

Policy-as-Code ensures consistent governance across deployments.

---

# Question 42

## Scenario

What Sentinel policies would you enforce organization-wide?

---

## What Is Being Tested?

* Sentinel
* Governance

---

## Solution

Common policies:

* Mandatory tags
* Approved AWS regions
* Encryption enabled
* Approved instance types
* No public S3 buckets

---

## Example Policy Goals

```text id="g42a"
Encryption Required

Tagging Required

Approved Regions Only
```

---

## Architecture

```text id="g42b"
Terraform Plan
      ↓
Sentinel
      ↓
Pass / Fail
```

---

## Important Exam Points

* Sentinel enforces organizational standards.
* Policies execute before apply.

---

## Common Mistakes

* Relying only on human reviews.

---

## Key Takeaway

Sentinel converts governance requirements into enforceable rules.

---

# Question 43

## Scenario

How would you enforce mandatory tagging?

---

## What Is Being Tested?

* Governance
* Resource Standards

---

## Solution

Use Sentinel policies and reusable modules.

---

## Example Tags

```text id="g43a"
Environment

Application

Owner

CostCenter
```

---

## Example Terraform

```hcl id="g43b"
tags = {
  Environment = "prod"
  Owner       = "platform-team"
}
```

---

## Architecture

```text id="g43c"
Terraform
      ↓
Tag Validation
      ↓
Deploy
```

---

## Important Exam Points

* Tags improve governance.
* Tags improve cost tracking.

---

## Common Mistakes

* Optional tagging.

---

## Key Takeaway

Mandatory tags improve visibility and governance.

---

# Question 44

## Scenario

How would you prevent insecure infrastructure from being deployed?

---

## What Is Being Tested?

* Security Controls
* Governance

---

## Solution

Implement:

* Sentinel
* Run Tasks
* CI/CD Validation

---

## Workflow

```text id="g44a"
Terraform Plan
      ↓
Security Checks
      ↓
Pass
      ↓
Apply
```

---

## Example Rules

```text id="g44b"
No Public Buckets

Encryption Required

Approved Regions Only
```

---

## Important Exam Points

* Shift security left.
* Validate before deployment.

---

## Common Mistakes

* Security reviews after deployment.

---

## Key Takeaway

Security controls should block unsafe infrastructure before deployment.

---

# Question 45

## Scenario

How would you enforce encryption requirements?

---

## What Is Being Tested?

* Security
* Compliance

---

## Solution

Implement encryption by default.

Enforce through:

* Modules
* Sentinel Policies

---

## Example

```hcl id="g45a"
server_side_encryption_configuration {
  rule {
    apply_server_side_encryption_by_default {
      sse_algorithm = "AES256"
    }
  }
}
```

---

## Architecture

```text id="g45b"
Terraform
      ↓
Encryption Validation
      ↓
Deploy
```

---

## Important Exam Points

* Encryption should be automatic.
* Policies enforce compliance.

---

## Common Mistakes

* Optional encryption.

---

## Key Takeaway

Security defaults should favor encryption.

---

# Question 46

## Scenario

How would you integrate security scanning into Terraform workflows?

---

## What Is Being Tested?

* Security Automation
* CI/CD

---

## Solution

Integrate scanning before apply.

---

## Example Tools

```text id="g46a"
Checkov

tfsec

Snyk

Prisma Cloud
```

---

## Workflow

```text id="g46b"
Terraform Code
      ↓
Security Scan
      ↓
Pass
      ↓
Deploy
```

---

## Example Command

```bash id="g46c"
checkov -d .
```

---

## Important Exam Points

* Security scanning should be automated.

---

## Common Mistakes

* Manual scanning.

---

## Key Takeaway

Automated scanning identifies security issues early.

---

# Question 47

## Scenario

How would you design Terraform approval workflows?

---

## What Is Being Tested?

* Governance
* Deployment Controls

---

## Solution

Require approvals before production deployments.

---

## Workflow

```text id="g47a"
Code Change
      ↓
Pull Request
      ↓
Terraform Plan
      ↓
Approval
      ↓
Apply
```

---

## Example Commands

```bash id="g47b"
terraform validate

terraform plan
```

---

## Important Exam Points

* Production changes require reviews.
* Plans should be reviewed before apply.

---

## Common Mistakes

* Direct production deployments.

---

## Key Takeaway

Approvals reduce deployment risk.

---

# Question 48

## Scenario

How would you balance deployment velocity with governance?

---

## What Is Being Tested?

* Governance Design
* Operational Efficiency

---

## Solution

Automate everything possible.

Require approvals only where risk justifies them.

---

## Example

Development:

```text id="g48a"
Automatic
```

Production:

```text id="g48b"
Controlled Approval
```

---

## Workflow

```text id="g48c"
Dev
 ↓
Stage
 ↓
Approval
 ↓
Prod
```

---

## Important Exam Points

* Automation improves speed.
* Governance reduces risk.

---

## Common Mistakes

* Excessive manual processes.

---

## Key Takeaway

Automate low-risk activities and govern high-risk activities.

---

# Question 49

## Scenario

How would you implement least privilege for Terraform users?

---

## What Is Being Tested?

* Security
* IAM

---

## Solution

Grant only required permissions.

Use dedicated IAM roles.

---

## Architecture

```text id="g49a"
Terraform
      ↓
IAM Role
      ↓
AWS Resources
```

---

## Example

```hcl id="g49b"
provider "aws" {
  assume_role {
    role_arn = "arn:aws:iam::123456789012:role/TerraformRole"
  }
}
```

---

## Important Exam Points

* Avoid administrator access.
* Use role-based permissions.

---

## Common Mistakes

* Excessive permissions.

---

## Key Takeaway

Least privilege minimizes security risk.

---

# Question 50

## Scenario

How would you design Terraform governance for regulated industries?

---

## What Is Being Tested?

* Compliance
* Governance

---

## Solution

Implement:

* Pull Requests
* Code Reviews
* Audit Trails
* Sentinel Policies
* Access Controls
* State Protection

---

## Architecture

```text id="g50a"
Developer
     ↓
Pull Request
     ↓
Review
     ↓
Policy Validation
     ↓
Approval
     ↓
Apply
```

---

## Example Controls

```text id="g50b"
Audit Logging

Encryption

Access Control

Policy Enforcement
```

---

## Commands

```bash id="g50c"
terraform validate

terraform plan
```

---

## Important Exam Points

* Compliance requires traceability.
* Governance should be automated where possible.

---

## Common Mistakes

* No audit trail.
* Manual approval records.

---

## Key Takeaway

Regulated environments require secure, auditable, and controlled Terraform workflows.

---

# Question 51

## Scenario

How would you build an Internal Developer Platform using Terraform?

---

## What Is Being Tested?

* Platform Engineering
* Infrastructure Standardization

---

## Solution

Create reusable Terraform modules that developers can consume through automated workflows.

---

## Architecture

```text
Developers
     ↓
Platform Portal
     ↓
Terraform Modules
     ↓
Cloud Infrastructure
```

---

## Example Components

```text
Networking Module

Application Module

Database Module

Monitoring Module
```

---

## Important Exam Points

* Platform teams create reusable infrastructure.
* Developers consume approved patterns.

---

## Common Mistakes

* Allowing every team to build infrastructure differently.

---

## Key Takeaway

An Internal Developer Platform standardizes infrastructure delivery.

---

# Question 52

## Scenario

What Terraform abstractions should developers see?

---

## What Is Being Tested?

* Platform Design
* Developer Experience

---

## Solution

Expose business-focused infrastructure.

Hide implementation complexity.

---

## Example

Instead of:

```text
VPC
Subnets
Route Tables
Security Groups
```

Expose:

```text
Web Application Environment
```

---

## Architecture

```text
Developer
     ↓
Application Environment
     ↓
Terraform Modules
     ↓
Cloud Resources
```

---

## Important Exam Points

* Simplicity improves adoption.
* Infrastructure complexity should be abstracted.

---

## Common Mistakes

* Exposing every infrastructure detail.

---

## Key Takeaway

Developers should consume services, not infrastructure complexity.

---

# Question 53

## Scenario

What Terraform complexity should be hidden from developers?

---

## What Is Being Tested?

* Platform Engineering
* User Experience

---

## Solution

Hide:

* Networking configuration
* IAM complexity
* State management
* Backend configuration
* Security policies

---

## Architecture

```text
Developer
     ↓
Platform Interface
     ↓
Terraform
     ↓
Infrastructure
```

---

## Important Exam Points

* Platform teams own complexity.
* Developers focus on applications.

---

## Common Mistakes

* Requiring developers to manage state.

---

## Key Takeaway

Hide operational complexity whenever possible.

---

# Question 54

## Scenario

How would developers request infrastructure?

---

## What Is Being Tested?

* Self-Service Infrastructure

---

## Solution

Provide approved workflows.

Examples:

* Git Pull Requests
* Service Catalog
* Platform Portal

---

## Workflow

```text
Developer Request
        ↓
Approval
        ↓
Terraform Deployment
```

---

## Example

```text
Request:
Application Environment

Result:
Network
Compute
Monitoring
Security
```

---

## Important Exam Points

* Requests should be standardized.
* Automation reduces manual work.

---

## Common Mistakes

* Manual ticket-based provisioning.

---

## Key Takeaway

Infrastructure requests should be automated and repeatable.

---

# Question 55

## Scenario

How would you implement self-service infrastructure?

---

## What Is Being Tested?

* Automation
* Platform Design

---

## Solution

Allow developers to deploy approved infrastructure without direct cloud access.

---

## Architecture

```text
Developer
     ↓
Git Repository
     ↓
Terraform Pipeline
     ↓
Cloud Resources
```

---

## Example Commands

```bash
terraform fmt

terraform validate

terraform plan

terraform apply
```

---

## Important Exam Points

* Self-service does not mean unrestricted access.
* Governance still applies.

---

## Common Mistakes

* Giving developers administrator access.

---

## Key Takeaway

Self-service should be controlled and automated.

---

# Question 56

## Scenario

How would you maintain governance while enabling self-service?

---

## What Is Being Tested?

* Governance
* Platform Engineering

---

## Solution

Combine automation with policy enforcement.

---

## Architecture

```text
Developer
     ↓
Terraform
     ↓
Sentinel Policies
     ↓
Approval
     ↓
Deploy
```

---

## Governance Controls

* Pull Requests
* Sentinel Policies
* Run Tasks
* Approval Gates

---

## Important Exam Points

* Governance and self-service can coexist.
* Policies automate compliance.

---

## Common Mistakes

* Disabling governance for speed.

---

## Key Takeaway

Automation should increase governance, not reduce it.

---

# Question 57

## Scenario

How would you design Terraform products instead of Terraform projects?

---

## What Is Being Tested?

* Platform Thinking
* Product-Based Infrastructure

---

## Solution

Provide reusable infrastructure offerings.

---

## Examples

```text
Web Application Platform

Database Platform

Container Platform

Monitoring Platform
```

---

## Architecture

```text
Platform Product
        ↓
Terraform Modules
        ↓
Cloud Resources
```

---

## Important Exam Points

* Infrastructure becomes a consumable product.
* Standardization improves scalability.

---

## Common Mistakes

* Treating every deployment as unique.

---

## Key Takeaway

Infrastructure products improve consistency and operational efficiency.

---

# Question 58

## Scenario

How would you onboard hundreds of teams onto a Terraform platform?

---

## What Is Being Tested?

* Platform Adoption
* Scalability

---

## Solution

Provide:

* Documentation
* Reusable Modules
* Training
* Standard Templates

---

## Workflow

```text
Team Onboarding
       ↓
Training
       ↓
Templates
       ↓
Terraform Adoption
```

---

## Example Resources

```text
Module Catalog

Quick Start Guides

Reference Architectures
```

---

## Important Exam Points

* Documentation accelerates adoption.
* Standardization reduces support effort.

---

## Common Mistakes

* No onboarding strategy.

---

## Key Takeaway

Successful platforms prioritize usability and documentation.

---

# Question 59

## Scenario

What platform metrics would you track?

---

## What Is Being Tested?

* Platform Operations
* Observability

---

## Solution

Track:

* Deployment Success Rate
* Failed Deployments
* Deployment Frequency
* Recovery Time
* Infrastructure Drift

---

## Example Metrics

```text
Successful Applies

Failed Applies

Policy Violations

Drift Events
```

---

## Architecture

```text
Terraform
     ↓
Metrics
     ↓
Dashboards
```

---

## Important Exam Points

* Metrics help measure platform effectiveness.
* Monitoring improves operational visibility.

---

## Common Mistakes

* Tracking only infrastructure uptime.

---

## Key Takeaway

Measure platform performance using operational metrics.

---

# Question 60

## Scenario

How would you evolve the platform over time?

---

## What Is Being Tested?

* Continuous Improvement
* Platform Strategy

---

## Solution

Continuously improve:

* Modules
* Governance
* Security
* Automation

---

## Workflow

```text
Feedback
    ↓
Improvements
    ↓
Testing
    ↓
Release
```

---

## Example Improvements

```text
New Modules

Improved Security Controls

Additional Automation

Enhanced Documentation
```

---

## Important Exam Points

* Platforms should evolve incrementally.
* Feedback drives improvements.

---

## Common Mistakes

* Large disruptive platform redesigns.

---

## Key Takeaway

Successful platforms evolve continuously through small improvements.

---

# Question 61

## Scenario

How would you manage secrets in Terraform at enterprise scale?

---

## What Is Being Tested?

* Secrets Management
* Terraform Security

---

## Solution

Store secrets outside Terraform code.

Use centralized secret management systems.

Examples:

* HashiCorp Vault
* AWS Secrets Manager
* Azure Key Vault
* Google Secret Manager

---

## Architecture

```text
Terraform
     ↓
Secret Manager
     ↓
Secret Retrieval
     ↓
Infrastructure
```

---

## Example

```hcl
variable "db_password" {
  sensitive = true
}
```

---

## Important Exam Points

* Never hardcode secrets.
* Sensitive variables do not encrypt secrets.

---

## Common Mistakes

* Secrets in Git repositories.
* Passwords inside Terraform files.

---

## Key Takeaway

Terraform should consume secrets, not store secrets.

---

# Question 62

## Scenario

Would you use Vault?

Why or why not?

---

## What Is Being Tested?

* Vault Fundamentals
* Secret Management

---

## Solution

Yes, for enterprise environments.

Vault provides:

* Centralized secret storage
* Dynamic credentials
* Secret rotation
* Audit logging

---

## Architecture

```text
Terraform
     ↓
Vault
     ↓
Temporary Credentials
     ↓
Cloud Provider
```

---

## Example Benefits

```text
Dynamic AWS Credentials

Credential Rotation

Auditing
```

---

## Important Exam Points

* Vault reduces secret exposure.
* Vault supports dynamic secrets.

---

## Common Mistakes

* Using Vault but still hardcoding credentials.

---

## Key Takeaway

Vault improves secret security and lifecycle management.

---

# Question 63

## Scenario

How would you implement secret rotation?

---

## What Is Being Tested?

* Credential Lifecycle
* Security Operations

---

## Solution

Automate rotation using:

* Vault
* AWS Secrets Manager
* Cloud-native secret solutions

---

## Workflow

```text
Secret Created
      ↓
Expiration
      ↓
Automatic Rotation
      ↓
New Secret Issued
```

---

## Example

```text
Database Password

AWS Access Keys

API Tokens
```

---

## Important Exam Points

* Rotating credentials reduces exposure risk.
* Automation is preferred.

---

## Common Mistakes

* Permanent credentials.

---

## Key Takeaway

Secrets should have a lifecycle and rotation strategy.

---

# Question 64

## Scenario

How would you prevent secrets from entering Git repositories?

---

## What Is Being Tested?

* Secure Development Practices

---

## Solution

Implement:

* Secret scanning
* Code reviews
* Git hooks
* Secret management systems

---

## Architecture

```text
Developer
     ↓
Secret Scan
     ↓
Git Repository
```

---

## Example Tools

```text
GitHub Secret Scanning

Gitleaks

TruffleHog
```

---

## Important Exam Points

* Prevention is better than cleanup.
* Scanning should be automated.

---

## Common Mistakes

* Discovering secrets after deployment.

---

## Key Takeaway

Secrets should be blocked before reaching source control.

---

# Question 65

## Scenario

How would you secure Terraform state?

---

## What Is Being Tested?

* State Security
* Backend Security

---

## Solution

Use:

* Remote State
* Encryption
* Access Controls
* State Locking

---

## Architecture

```text
Terraform
     ↓
Encrypted Backend
     ↓
State Storage
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket = "terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}
```

---

## Important Exam Points

* State may contain sensitive information.
* Protect state like production data.

---

## Common Mistakes

* Committing state files to Git.

---

## Key Takeaway

State security is infrastructure security.

---

# Question 66

## Scenario

How would you audit access to Terraform infrastructure?

---

## What Is Being Tested?

* Auditing
* Compliance

---

## Solution

Use:

* IAM Logs
* CloudTrail
* HCP Terraform Audit Logs
* Git History

---

## Architecture

```text
User
 ↓
Terraform
 ↓
Cloud Resources
 ↓
Audit Logs
```

---

## Example Sources

```text
CloudTrail

GitHub

HCP Terraform
```

---

## Important Exam Points

* Infrastructure actions should be traceable.
* Auditing supports compliance.

---

## Common Mistakes

* No centralized logging.

---

## Key Takeaway

Every infrastructure action should leave an audit trail.

---

# Question 67

## Scenario

How would you secure Terraform pipelines?

---

## What Is Being Tested?

* CI/CD Security

---

## Solution

Implement:

* Least privilege IAM
* Secret management
* Branch protection
* Approval workflows

---

## Workflow

```text
Code
 ↓
Pipeline
 ↓
Terraform
 ↓
Infrastructure
```

---

## Example Controls

```text
Protected Branches

Secret Storage

Role-Based Access
```

---

## Important Exam Points

* Pipelines should not use personal credentials.
* Access should be restricted.

---

## Common Mistakes

* Hardcoded credentials in CI/CD.

---

## Key Takeaway

Secure pipelines are critical to secure infrastructure.

---

# Question 68

## Scenario

How would you implement break-glass access procedures?

---

## What Is Being Tested?

* Emergency Operations
* Security Controls

---

## Solution

Create temporary emergency access procedures.

---

## Workflow

```text
Incident
   ↓
Emergency Access
   ↓
Resolution
   ↓
Access Revoked
```

---

## Requirements

* Approval process
* Audit logging
* Time-limited access

---

## Important Exam Points

* Break-glass access should be exceptional.
* All actions must be audited.

---

## Common Mistakes

* Permanent emergency accounts.

---

## Key Takeaway

Emergency access should be controlled, temporary, and auditable.

---

# Question 69

## Scenario

How would you respond to a secret exposure incident?

---

## What Is Being Tested?

* Security Incident Response

---

## Solution

Assume compromise immediately.

---

## Response Workflow

```text
Secret Exposed
      ↓
Revoke Secret
      ↓
Rotate Secret
      ↓
Investigate
      ↓
Restore Operations
```

---

## Immediate Actions

```text
Disable Access

Generate New Secret

Review Logs
```

---

## Important Exam Points

* Secret rotation should be immediate.
* Investigation follows containment.

---

## Common Mistakes

* Delaying rotation.

---

## Key Takeaway

Treat exposed secrets as compromised secrets.

---

# Question 70

## Scenario

How would you design Terraform security controls for a large enterprise?

---

## What Is Being Tested?

* Enterprise Security
* Governance

---

## Solution

Implement multiple security layers.

---

## Architecture

```text
Developers
     ↓
GitHub Reviews
     ↓
Terraform Validation
     ↓
Security Scanning
     ↓
Sentinel Policies
     ↓
Approval
     ↓
Deployment
```

---

## Security Controls

```text
Least Privilege IAM

Encrypted State

Secret Management

Policy Enforcement

Audit Logging
```

---

## Example Commands

```bash
terraform fmt

terraform validate

terraform plan
```

---

## Important Exam Points

* Security should be layered.
* Automation improves consistency.

---

## Common Mistakes

* Single security control.
* Manual-only security processes.

---

## Key Takeaway

Enterprise Terraform security requires governance, automation, and multiple layers of protection.

---

# Question 71

## Scenario

How would you design disaster recovery for Terraform state?

---

## What Is Being Tested?

* State Management
* Disaster Recovery

---

## Solution

Store state remotely with versioning and backups.

---

## Architecture

```text
Terraform
     ↓
Remote Backend
     ↓
Versioning
     ↓
Backups
```

---

## Example AWS Architecture

```text
Terraform
     ↓
S3 Backend
     ↓
Versioning Enabled
     ↓
DynamoDB Locking
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-state"
    key            = "prod/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
  }
}
```

---

## Important Exam Points

* State is critical infrastructure metadata.
* Remote state improves recovery.
* Versioning protects against accidental deletion.

---

## Common Mistakes

* Local-only state.
* No backups.

---

## Key Takeaway

Treat Terraform state like production data.

---

# Question 72

## Scenario

What is your recovery procedure if Terraform state is lost?

---

## What Is Being Tested?

* Recovery Process
* State Management

---

## Solution

Restore the latest known-good backup.

---

## Recovery Workflow

```text
State Loss
    ↓
Restore Backup
    ↓
terraform plan
    ↓
Validate
    ↓
Continue Operations
```

---

## Commands

```bash
terraform state list

terraform plan
```

---

## Alternative Recovery

If no backup exists:

```bash
terraform import
```

may be required.

---

## Important Exam Points

* Backups simplify recovery.
* Imports may rebuild state.

---

## Common Mistakes

* Continuing deployments without validation.

---

## Key Takeaway

Always validate restored state before applying changes.

---

# Question 73

## Scenario

How would you recover from accidental resource deletion?

---

## What Is Being Tested?

* Terraform Recovery
* State Consistency

---

## Solution

Terraform can recreate missing resources if they still exist in configuration.

---

## Workflow

```text
Resource Deleted
       ↓
terraform plan
       ↓
Terraform Detects Drift
       ↓
terraform apply
       ↓
Resource Recreated
```

---

## Commands

```bash
terraform plan

terraform apply
```

---

## Important Exam Points

* Terraform compares desired and actual state.
* Missing resources are recreated.

---

## Common Mistakes

* Manually recreating resources before investigating.

---

## Key Takeaway

Terraform helps restore infrastructure from configuration.

---

# Question 74

## Scenario

How would you recover from a failed production deployment?

---

## What Is Being Tested?

* Operational Recovery
* Terraform Workflow

---

## Solution

Stop further deployments.

Identify the failure.

Review Terraform plan and logs.

---

## Workflow

```text
Deployment Failure
       ↓
Investigation
       ↓
Fix Issue
       ↓
terraform plan
       ↓
terraform apply
```

---

## Commands

```bash
terraform plan

terraform show
```

---

## Debugging

```bash
TF_LOG=DEBUG terraform apply
```

---

## Important Exam Points

* Understand the root cause before retrying.
* Review plan output carefully.

---

## Common Mistakes

* Re-running apply repeatedly.

---

## Key Takeaway

Investigate first, deploy second.

---

# Question 75

## Scenario

How would you handle large-scale drift across environments?

---

## What Is Being Tested?

* Drift Detection
* Governance

---

## Solution

Identify all drift and restore Terraform as the source of truth.

---

## Workflow

```text
Drift
 ↓
terraform plan
 ↓
Review
 ↓
Correct Configuration
 ↓
Apply
```

---

## Commands

```bash
terraform plan
```

---

## Prevention Controls

* Restricted Console Access
* CI/CD Deployments
* Pull Requests

---

## Important Exam Points

* Drift occurs when resources change outside Terraform.

---

## Common Mistakes

* Ignoring plan output.

---

## Key Takeaway

Terraform should remain the authoritative source of infrastructure configuration.

---

# Question 76

## Scenario

How would you design rollback strategies for Terraform?

---

## What Is Being Tested?

* Change Management
* Recovery Planning

---

## Solution

Terraform does not provide native rollback.

Use:

* Version Control
* Previous Configurations
* State Recovery

---

## Workflow

```text
Deployment Issue
       ↓
Git Revert
       ↓
terraform plan
       ↓
terraform apply
```

---

## Example Git Command

```bash
git revert <commit-id>
```

---

## Important Exam Points

* Rollback is typically configuration-based.
* Git history is critical.

---

## Common Mistakes

* Assuming Terraform has a rollback command.

---

## Key Takeaway

Version control enables Terraform rollback strategies.

---

# Question 77

## Scenario

How would you audit six months of infrastructure changes?

---

## What Is Being Tested?

* Auditability
* Compliance

---

## Solution

Review:

* Git History
* Pull Requests
* CI/CD Logs
* HCP Terraform Runs

---

## Architecture

```text
GitHub
   ↓
Terraform
   ↓
Infrastructure
   ↓
Audit Trail
```

---

## Example Commands

```bash
git log

git show
```

---

## Important Exam Points

* Infrastructure should be version controlled.
* Auditing supports compliance requirements.

---

## Common Mistakes

* Manual undocumented changes.

---

## Key Takeaway

Every infrastructure change should be traceable.

---

# Question 78

## Scenario

How would you design operational runbooks for Terraform?

---

## What Is Being Tested?

* Operations
* Standardization

---

## Solution

Create documented procedures for common operations.

---

## Example Runbooks

```text
State Recovery

Failed Deployment

Drift Investigation

Import Process

Module Upgrade
```

---

## Example Deployment Runbook

```text
terraform fmt
      ↓
terraform validate
      ↓
terraform plan
      ↓
Review
      ↓
terraform apply
```

---

## Important Exam Points

* Runbooks improve operational consistency.

---

## Common Mistakes

* Tribal knowledge only.

---

## Key Takeaway

Documented procedures reduce operational risk.

---

# Question 79

## Scenario

What Terraform metrics should operations teams monitor?

---

## What Is Being Tested?

* Observability
* Operations

---

## Solution

Monitor:

* Successful Applies
* Failed Applies
* Drift Events
* Policy Violations
* Deployment Frequency

---

## Example Metrics

```text
Deployment Success Rate

Mean Recovery Time

Terraform Failures

Infrastructure Drift
```

---

## Architecture

```text
Terraform
     ↓
Metrics
     ↓
Dashboard
```

---

## Important Exam Points

* Metrics improve visibility.
* Monitoring improves reliability.

---

## Common Mistakes

* Monitoring only infrastructure uptime.

---

## Key Takeaway

Measure both deployment quality and operational health.

---

# Question 80

## Scenario

How would you improve Terraform operational maturity?

---

## What Is Being Tested?

* Terraform Operations
* Process Improvement

---

## Solution

Implement:

* Remote State
* CI/CD
* Governance
* Module Reuse
* Documentation

---

## Maturity Path

```text
Local State
      ↓
Remote State
      ↓
CI/CD
      ↓
Governance
      ↓
Platform Engineering
```

---

## Example Commands

```bash
terraform fmt

terraform validate

terraform plan
```

---

## Important Exam Points

* Standardization improves maturity.
* Automation improves reliability.

---

## Common Mistakes

* Manual deployments.
* No governance controls.

---

## Key Takeaway

Terraform maturity grows through automation, governance, and standardization.

---

# Question 81

## Scenario

Review a Terraform platform where every application uses a shared state file.

What problems do you identify?

---

## What Is Being Tested?

* State Management
* Architecture Review

---

## Solution

This is a poor design.

A shared state file creates a large blast radius.

---

## Architecture

Bad:

```text
App1
App2
App3
 ↓
Shared State
```

Better:

```text
App1 → State1

App2 → State2

App3 → State3
```

---

## Risks

* State corruption affects all applications
* Slow plans
* Difficult troubleshooting
* Team conflicts

---

## Commands

```bash
terraform state list

terraform plan
```

---

## Important Exam Points

* State should be isolated.
* Smaller state files are easier to manage.

---

## Common Mistakes

* One state file per department.

---

## Key Takeaway

Separate state reduces operational risk.

---

# Question 82

## Scenario

Review a Terraform architecture where all engineers have production apply permissions.

What risks exist?

---

## What Is Being Tested?

* Governance
* Security

---

## Solution

Production access should be restricted.

---

## Risks

```text
Accidental Deletion

Unauthorized Changes

Security Incidents

Compliance Violations
```

---

## Recommended Design

```text
Developer
   ↓
Pull Request
   ↓
Review
   ↓
Approval
   ↓
Production Apply
```

---

## Example IAM Strategy

```text
Developers
=
Read Access

Pipeline
=
Apply Access
```

---

## Important Exam Points

* Least privilege principle.
* Production access should be controlled.

---

## Common Mistakes

* Shared administrator access.

---

## Key Takeaway

Limit production permissions to reduce risk.

---

# Question 83

## Scenario

Review a Terraform platform with no module versioning strategy.

What could go wrong?

---

## What Is Being Tested?

* Module Management
* Change Control

---

## Solution

Unversioned modules can introduce unexpected changes.

---

## Risks

```text
Breaking Changes

Unpredictable Deployments

Difficult Rollbacks
```

---

## Example

Good:

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "~> 5.0"
}
```

---

## Important Exam Points

* Pin module versions.
* Test upgrades before production.

---

## Common Mistakes

* Using latest module versions everywhere.

---

## Key Takeaway

Module versioning improves stability and predictability.

---

# Question 84

## Scenario

Review an architecture where Terraform state is stored locally.

Would you approve it?

Why or why not?

---

## What Is Being Tested?

* State Management
* Collaboration

---

## Solution

Generally no for team environments.

Local state creates operational risk.

---

## Risks

```text
State Loss

No Collaboration

No Locking

No Recovery
```

---

## Better Design

```text
Terraform
     ↓
Remote Backend
     ↓
Versioning
```

---

## Example Backend

```hcl
terraform {
  backend "s3" {
    bucket = "terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}
```

---

## Important Exam Points

* Remote state is preferred.
* Local state is suitable mainly for learning.

---

## Common Mistakes

* Production deployments using local state.

---

## Key Takeaway

Remote state improves reliability and collaboration.

---

# Question 85

## Scenario

Review a Terraform environment where production changes bypass pull requests.

What governance issues exist?

---

## What Is Being Tested?

* Change Management
* Governance

---

## Solution

This removes review and approval processes.

---

## Risks

```text
Unreviewed Changes

Configuration Errors

Compliance Failures
```

---

## Recommended Workflow

```text
Code
 ↓
Pull Request
 ↓
Review
 ↓
Plan
 ↓
Apply
```

---

## Commands

```bash
terraform validate

terraform plan
```

---

## Important Exam Points

* Reviews improve deployment quality.
* Pull requests improve auditability.

---

## Common Mistakes

* Direct commits to production branches.

---

## Key Takeaway

Production infrastructure should follow controlled change management.

---

# Question 86

## Scenario

Review a Terraform platform that uses copy-pasted infrastructure rather than modules.

What long-term problems emerge?

---

## What Is Being Tested?

* Module Design
* Reusability

---

## Solution

Copy-paste infrastructure creates duplication.

---

## Risks

```text
Configuration Drift

Maintenance Burden

Inconsistent Standards
```

---

## Better Design

```text
Shared Module
      ↓
Multiple Deployments
```

---

## Example

```hcl
module "networking" {
  source = "./modules/networking"
}
```

---

## Important Exam Points

* Modules improve consistency.
* Reuse reduces maintenance effort.

---

## Common Mistakes

* Maintaining multiple copies of the same code.

---

## Key Takeaway

Modules scale better than copy-paste infrastructure.

---

# Question 87

## Scenario

Review a Terraform deployment process with no policy enforcement.

What risks exist?

---

## What Is Being Tested?

* Governance
* Security

---

## Solution

Without policies, unsafe infrastructure can be deployed.

---

## Risks

```text
Public Resources

Missing Encryption

Incorrect Regions

Missing Tags
```

---

## Better Design

```text
Terraform Plan
      ↓
Policy Validation
      ↓
Apply
```

---

## Example Policies

```text
Encryption Required

Mandatory Tags

Approved Regions
```

---

## Important Exam Points

* Policy-as-Code automates governance.

---

## Common Mistakes

* Relying solely on manual reviews.

---

## Key Takeaway

Policy enforcement reduces security and compliance risk.

---

# Question 88

## Scenario

Review an environment where developers can directly modify cloud infrastructure.

How would you redesign it?

---

## What Is Being Tested?

* Governance
* Drift Prevention

---

## Solution

Make Terraform the source of truth.

Restrict direct cloud changes.

---

## Architecture

Bad:

```text
Developer
     ↓
Cloud Console
```

Better:

```text
Developer
     ↓
Git
     ↓
Terraform
     ↓
Cloud
```

---

## Controls

* Pull Requests
* CI/CD
* IAM Restrictions

---

## Important Exam Points

* Manual changes create drift.
* Terraform should manage infrastructure.

---

## Common Mistakes

* Allowing unrestricted console access.

---

## Key Takeaway

Infrastructure changes should flow through Terraform.

---

# Question 89

## Scenario

Review a Terraform organization with no disaster recovery strategy.

What improvements would you recommend?

---

## What Is Being Tested?

* Disaster Recovery
* Operational Readiness

---

## Solution

Implement:

* Remote State
* Versioning
* Backups
* Recovery Testing

---

## Architecture

```text
Terraform
     ↓
Remote State
     ↓
Versioning
     ↓
Recovery
```

---

## Example AWS Setup

```text
S3
+
Versioning
+
DynamoDB Locking
```

---

## Important Exam Points

* Recovery planning is essential.
* State loss can impact deployments.

---

## Common Mistakes

* No backup validation.

---

## Key Takeaway

Disaster recovery should be planned before incidents occur.

---

# Question 90

## Scenario

Review a Terraform platform and identify its likely operational bottlenecks.

---

## What Is Being Tested?

* Platform Analysis
* Operations

---

## Solution

Common bottlenecks include:

```text
Large State Files

Manual Approvals

Copy-Paste Code

No Module Reuse

No CI/CD

Manual Deployments
```

---

## Review Checklist

```text
State Management

Module Strategy

CI/CD

Governance

Security

Documentation
```

---

## Commands

```bash
terraform plan

terraform validate
```

---

## Important Exam Points

* Operational bottlenecks reduce scalability.
* Standardization improves efficiency.

---

## Common Mistakes

* Growing infrastructure without improving processes.

---

## Key Takeaway

Operational maturity depends on automation, governance, and reusable patterns.

---

# Question 91

## Scenario

What separates a Terraform user from a Terraform architect?

---

## What Is Being Tested?

* Terraform Maturity
* Architecture Thinking

---

## Solution

A Terraform user focuses on writing Terraform code.

A Terraform architect focuses on designing scalable, secure, and maintainable Terraform platforms.

---

## Comparison

| Terraform User        | Terraform Architect   |
| --------------------- | --------------------- |
| Creates Resources     | Designs Platforms     |
| Uses Modules          | Designs Modules       |
| Runs Commands         | Designs Workflows     |
| Focuses on Deployment | Focuses on Governance |

---

## Important Exam Points

* Architecture focuses on systems.
* Terraform is more than writing resources.

---

## Key Takeaway

Architects design processes, standards, and platforms—not just infrastructure.

---

# Question 92

## Scenario

What Terraform design decisions scale well?

---

## What Is Being Tested?

* Scalability
* Best Practices

---

## Solution

Scalable decisions include:

```text
Reusable Modules

Remote State

CI/CD

Environment Isolation

Policy Enforcement

Version Control
```

---

## Architecture

```text
Modules
   ↓
Reusable Infrastructure
   ↓
Scalable Platform
```

---

## Important Exam Points

* Reuse improves scalability.
* Automation reduces operational burden.

---

## Common Mistakes

* Manual deployments.
* Copy-paste infrastructure.

---

## Key Takeaway

Scalable Terraform relies on standardization and automation.

---

# Question 93

## Scenario

What Terraform design decisions fail at scale?

---

## What Is Being Tested?

* Architecture Review
* Anti-Patterns

---

## Solution

Common anti-patterns:

```text
Local State

Shared State

Manual Deployments

No Versioning

No Governance

Hardcoded Secrets
```

---

## Architecture

Bad:

```text
Everyone
    ↓
Shared State
```

---

## Risks

* Security issues
* Operational failures
* Difficult troubleshooting

---

## Important Exam Points

* Small mistakes become large problems at scale.

---

## Key Takeaway

What works for one engineer often fails for hundreds.

---

# Question 94

## Scenario

What would your ideal enterprise Terraform platform look like?

---

## What Is Being Tested?

* Platform Design
* Terraform Ecosystem

---

## Solution

An ideal platform includes:

* Git
* CI/CD
* Terraform Modules
* Remote State
* Governance
* Security Controls

---

## Architecture

```text
GitHub
   ↓
Terraform
   ↓
Policies
   ↓
Cloud
```

---

## Components

```text
Module Registry

Remote State

Approval Workflow

Security Scanning
```

---

## Important Exam Points

* Automation improves consistency.
* Governance improves safety.

---

## Key Takeaway

An ideal platform balances speed, security, and governance.

---

# Question 95

## Scenario

How would you design Terraform for a Fortune 500 organization?

---

## What Is Being Tested?

* Enterprise Architecture

---

## Solution

Implement:

* Multi-Account Strategy
* Shared Modules
* Remote State
* CI/CD Pipelines
* Governance Controls

---

## Architecture

```text
Organization
     ↓
Accounts
     ↓
Environments
     ↓
Applications
```

---

## Example Structure

```text
prod/
stage/
dev/
```

---

## Important Exam Points

* Separate environments.
* Use reusable infrastructure.

---

## Key Takeaway

Enterprise Terraform requires structure, governance, and automation.

---

# Question 96

## Scenario

How would Platform Engineering change Terraform adoption?

---

## What Is Being Tested?

* Platform Engineering
* Terraform Operations

---

## Solution

Platform Engineering simplifies Terraform consumption.

Developers use approved infrastructure patterns.

---

## Architecture

```text
Platform Team
      ↓
Terraform Modules
      ↓
Application Teams
```

---

## Benefits

```text
Standardization

Security

Reuse

Automation
```

---

## Important Exam Points

* Platform teams provide paved roads.
* Developers consume approved solutions.

---

## Key Takeaway

Platform Engineering accelerates Terraform adoption.

---

# Question 97

## Scenario

What Terraform governance controls provide the highest value?

---

## What Is Being Tested?

* Governance
* Risk Reduction

---

## Solution

High-value controls:

```text
Pull Requests

Code Reviews

Remote State

Policy Enforcement

CI/CD
```

---

## Architecture

```text
Code
 ↓
Review
 ↓
Policy Validation
 ↓
Deploy
```

---

## Important Exam Points

* Governance reduces risk.
* Automation improves consistency.

---

## Common Mistakes

* Manual reviews only.

---

## Key Takeaway

Governance should be automated whenever possible.

---

# Question 98

## Scenario

How should Terraform evolve as organizations grow?

---

## What Is Being Tested?

* Growth Strategy
* Operational Maturity

---

## Solution

Maturity should progress through stages.

---

## Evolution Path

```text
Terraform Basics
       ↓
Modules
       ↓
Remote State
       ↓
CI/CD
       ↓
Governance
       ↓
Platform Engineering
```

---

## Important Exam Points

* Growth requires standardization.
* Governance becomes increasingly important.

---

## Key Takeaway

Terraform maturity grows through automation and standardization.

---

# Question 99

## Scenario

What lessons have you learned from Terraform architecture failures?

---

## What Is Being Tested?

* Architecture Awareness
* Anti-Patterns

---

## Solution

Common lessons:

```text
State Matters

Governance Matters

Modules Matter

Documentation Matters
```

---

## Common Failures

```text
Local State

Shared State

No Reviews

Hardcoded Secrets
```

---

## Important Exam Points

* Most failures are process failures.
* Governance reduces operational risk.

---

## Key Takeaway

Good Terraform architecture prevents common operational mistakes.

---

# Question 100

## Scenario

If starting from scratch today, how would you architect Terraform across an entire enterprise?

---

## What Is Being Tested?

* Enterprise Design
* Terraform Best Practices

---

## Solution

Build a platform based on:

* GitOps
* Remote State
* Reusable Modules
* CI/CD
* Governance
* Security

---

## Architecture

```text
GitHub
   ↓
Pull Request
   ↓
Terraform Plan
   ↓
Policy Checks
   ↓
Approval
   ↓
Apply
   ↓
Cloud
```

---

## Recommended Components

```text
Private Module Registry

Remote State

Sentinel Policies

Run Tasks

Audit Logging
```

---

## Example Commands

```bash
terraform fmt

terraform validate

terraform plan

terraform apply
```

---

## Important Exam Points

* Infrastructure should be version controlled.
* Governance should be automated.
* Security should be built in.

---

## Common Mistakes

* Manual deployments.
* No standardization.

---

## Key Takeaway

Start with automation, governance, reusable modules, and remote state from day one.

---

# Architecture Readiness Assessment

| Score  | Assessment                |
| ------ | ------------------------- |
| 0–20   | Terraform Fundamentals    |
| 21–40  | Terraform Practitioner    |
| 41–60  | Infrastructure Engineer   |
| 61–80  | Senior Terraform Engineer |
| 81–95  | Platform Engineer         |
| 96–100 | Terraform Architect       |
