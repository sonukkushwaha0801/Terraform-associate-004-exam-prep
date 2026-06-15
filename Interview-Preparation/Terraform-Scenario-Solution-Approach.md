# Terraform Scenario Solution Approach

> Companion Guide for:
>
> `Interview-Preparation/Terraform-Scenario-Based-Questions.md`
>
> Purpose:
>
> This guide teaches how to think through Terraform interview scenarios using a Senior DevOps Engineer, Cloud Engineer, Infrastructure Engineer, or Platform Engineer mindset.
>
> Coverage:
>
> * Root Cause Analysis
> * Terraform Decision Making
> * Risk Assessment
> * Governance
> * Architecture Thinking
> * State Recovery

---

# Scenario 1 — Manual Infrastructure Provisioning

## What Is The Interviewer Testing?

* IaC Fundamentals
* Terraform Adoption Strategy
* Migration Planning
* Governance Awareness

---

## Terraform Domains Involved

* Infrastructure as Code
* Version Control
* State Management
* Change Management

---

## Step 1 — Identify The Core Problem

Current environment:

``` id="s1a"
AWS Console
↓
Manual Resource Creation
↓
No Standardization
↓
Environment Drift
```

Problems:

* Human error
* No repeatability
* No auditability
* Inconsistent environments

---

## Step 2 — Business Risks

* Production outages
* Security misconfigurations
* Slow provisioning
* Compliance failures

---

## Step 3 — Investigation Questions

Ask:

* How many resources exist?
* Are environments documented?
* Which resources are business critical?
* Is any IaC already being used?

---

## Step 4 — Immediate Recommendation

Perform:

``` id="s1b"
Inventory
↓
Classification
↓
Documentation
↓
Terraform Design
```

---

## Step 5 — Migration Strategy

Recommended approach:

``` id="s1c"
Inventory Resources
↓
Write Terraform Code
↓
Import Resources
↓
Validate Plans
↓
Enable CI/CD
```

---

## Step 6 — Governance Controls

Implement:

* Git repositories
* Pull requests
* Code reviews
* Protected branches

---

## Senior-Level Discussion

Focus on:

* Controlled migration
* Risk reduction
* Organizational standards
* Long-term maintainability

---

# Scenario 2 — Multi-Cloud Standardization

## What Is The Interviewer Testing?

* Provider Architecture
* Multi-Cloud Design
* Terraform Abstraction

---

## Terraform Domains Involved

* Providers
* Modules
* Multi-Cloud Workflows

---

## Step 1 — Identify The Problem

Different teams use:

``` id="s2a"
AWS
Azure
```

but processes differ.

---

## Step 2 — Risks

* Inconsistent deployments
* Different standards
* Security gaps
* Operational complexity

---

## Step 3 — Terraform Solution

Terraform provides:

``` id="s2b"
Common Workflow

terraform init
terraform plan
terraform apply
```

regardless of cloud.

---

## Step 4 — Architecture Recommendation

Structure:

``` id="s2c"
Modules
↓
Environment Layer
↓
Cloud-Specific Providers
```

---

## Step 5 — Governance

Require:

* Shared modules
* Tagging standards
* Security baselines

---

## Senior-Level Discussion

Focus on:

* Standardization
* Cloud independence
* Governance consistency

---

# Scenario 3 — Manual Security Group Change

## What Is The Interviewer Testing?

* Drift Detection
* Operational Governance
* Incident Handling

---

## Terraform Domains Involved

* State
* Plan
* Drift Management

---

## Step 1 — Identify Problem

Infrastructure changed outside Terraform.

This is:

``` id="s3a"
Configuration Drift
```

---

## Step 2 — Risks

* Security exposure
* Compliance issues
* Future deployment failures

---

## Step 3 — Investigation

Run:

``` id="s3b"
terraform plan
```

Review:

``` id="s3c"
Desired State
vs
Actual State
```

---

## Step 4 — Determine Intent

Ask:

* Was change authorized?
* Was emergency access required?
* Is Terraform configuration outdated?

---

## Step 5 — Recovery

Choose one:

### Option A

Update Terraform code.

### Option B

Revert infrastructure.

---

## Step 6 — Prevention

Implement:

* Change management
* Restricted console access
* Terraform-only modifications

---

## Senior-Level Discussion

Focus on:

* Governance failures
* Drift prevention
* Operational discipline

---

# Scenario 4 — Apply Without Reviewing Plan

## What Is The Interviewer Testing?

* Deployment Safety
* Terraform Workflow
* Operational Maturity

---

## Terraform Domains Involved

* Plan
* Apply
* Governance

---

## Step 1 — Identify Failure

Engineer skipped:

``` id="s4a"
terraform plan
```

review process.

---

## Step 2 — Risks

* Resource deletion
* Downtime
* Cost increase
* Security issues

---

## Step 3 — Immediate Actions

Determine:

* What changed?
* What was destroyed?
* What services are impacted?

---

## Step 4 — Recovery

Review:

``` id="s4b"
terraform show
```

Review state.

Restore infrastructure if necessary.

---

## Step 5 — Prevention

Require:

``` id="s4c"
Plan
↓
Review
↓
Approval
↓
Apply
```

---

## Governance Controls

* Pull requests
* Approval gates
* Protected environments

---

## Senior-Level Discussion

Focus on:

* Process failures
* Safe deployment practices

---

# Scenario 5 — Auto-Approve In CI/CD

## What Is The Interviewer Testing?

* Automation Trade-Offs
* Governance
* Risk Management

---

## Step 1 — Identify Issue

Pipeline executes:

``` id="s5a"
terraform apply -auto-approve
```

for every commit.

---

## Step 2 — Risks

* Unreviewed changes
* Production outages
* Compliance violations

---

## Step 3 — Investigate

Determine:

* Environment scope
* Approval requirements
* Existing controls

---

## Step 4 — Recommended Model

Development:

``` id="s5b"
Auto Approve
(Optional)
```

Production:

``` id="s5c"
Plan
↓
Review
↓
Approval
↓
Apply
```

---

## Governance Improvements

* Manual approval stages
* HCP Terraform runs
* Sentinel policies

---

## Senior-Level Discussion

Trade-off:

``` id="s5d"
Speed
vs
Control
```

---

# Scenario 6 — Validate Succeeds, Apply Fails

## What Is The Interviewer Testing?

* Troubleshooting Process
* Terraform Internals

---

## Step 1 — Understand Situation

Validation checks:

``` id="s6a"
Syntax
Structure
References
```

Apply interacts with:

``` id="s6b"
Cloud APIs
Permissions
Quotas
```

---

## Step 2 — Possible Causes

* Invalid IAM permissions
* Missing resources
* Provider errors
* Service limits

---

## Step 3 — Investigation

Run:

``` id="s6c"
terraform plan
```

Enable:

``` id="s6d"
TF_LOG=DEBUG
```

---

## Step 4 — Verify

Check:

* Credentials
* Permissions
* Provider versions
* API responses

---

## Senior-Level Discussion

Explain:

``` id="s6e"
Validation ≠ Deployment Success
```

---

# Scenario 7 — Simultaneous Terraform Applies

## What Is The Interviewer Testing?

* State Locking
* Remote Backends
* Collaboration

---

## Step 1 — Identify Problem

Multiple applies executed simultaneously.

---

## Step 2 — Risks

* State corruption
* Lost updates
* Resource duplication

---

## Step 3 — Immediate Containment

Stop all Terraform operations.

Backup state.

---

## Step 4 — Investigation

Check:

* Backend type
* Locking status
* Run history

---

## Step 5 — Recovery

Review:

``` id="s7a"
terraform state list
```

Review:

``` id="s7b"
terraform plan
```

Repair state if required.

---

## Step 6 — Prevention

Implement:

``` id="s7c"
Remote Backend
+
State Locking
```

---

## Senior-Level Discussion

Discuss:

* Team workflows
* Deployment governance
* CI/CD ownership

---

# Scenario 8 — State File Stored In Git

## What Is The Interviewer Testing?

* Security Awareness
* State Management

---

## Step 1 — Identify Problem

State file committed to source control.

---

## Risks

Potential exposure of:

* Resource metadata
* Outputs
* Secrets
* Infrastructure structure

---

## Step 2 — Immediate Actions

Remove state file.

Rotate exposed credentials.

Audit repository history.

---

## Step 3 — Migration

Move state to:

* HCP Terraform
* S3 Backend
* Azure Storage
* GCS

---

## Step 4 — Prevention

Add:

``` id="s8a"
.gitignore
```

Protect backend access.

---

## Senior-Level Discussion

Focus on:

* State security
* Secret exposure
* Compliance implications

---

# Scenario 9 — Terraform State Deleted

## What Is The Interviewer Testing?

* Disaster Recovery
* State Importance

---

## Step 1 — Assess Damage

Determine:

* Local state?
* Remote backend?
* Available backups?

---

## Step 2 — Risks

* Terraform loses resource mapping
* Future plans become unreliable

---

## Step 3 — Recovery Options

### Best Case

Restore backup.

### Alternative

Reconstruct state through:

``` id="s9a"
terraform import
```

---

## Step 4 — Long-Term Solution

Implement:

* Remote backend
* Versioning
* Backups

---

## Senior-Level Discussion

State should be treated as critical infrastructure.

---

# Scenario 10 — Unexpected Resource Recreation

## What Is The Interviewer Testing?

* Resource Lifecycle
* State Analysis
* Terraform Planning

---

## Step 1 — Identify Problem

Plan shows:

``` id="s10a"
-/+
```

replacement operations.

---

## Step 2 — Investigation

Review:

``` id="s10b"
terraform plan
```

Determine:

* Which attributes changed?
* Force replacement?
* State mismatch?

---

## Step 3 — Common Causes

* Imported resources
* Immutable attributes
* Drift
* Refactoring mistakes

---

## Step 4 — Do Not Apply Immediately

First determine:

``` id="s10c"
Expected?
or
Unexpected?
```

---

## Step 5 — Recovery Strategy

Options:

* Correct configuration
* Import resources
* Repair state
* Accept replacement

---

## Senior-Level Discussion

Focus on:

* Change impact
* Downtime risk
* Data-loss risk
* Deployment strategy

---

# Scenario 11 — Engineer Manually Edits Terraform State

## What Is The Interviewer Testing?

* State Management Knowledge
* Risk Assessment
* Recovery Procedures

---

## Terraform Domains Involved

* State
* Backends
* Disaster Recovery

---

## Step 1 — Identify The Problem

An engineer directly modifies:

```
terraform.tfstate
```

outside Terraform.

---

## Step 2 — Risks

Potential consequences:

* State corruption
* Resource orphaning
* Incorrect plans
* Unexpected resource destruction
* Production outages

---

## Step 3 — Investigation

Determine:

* What was changed?
* Was a backup created?
* Was the change intentional?
* Did infrastructure change?

---

## Step 4 — Immediate Actions

Stop all Terraform operations.

Preserve:

```
Current State
Previous State
State History
```

---

## Step 5 — Recovery Strategy

Compare:

```
Desired Configuration
vs
Terraform State
vs
Actual Infrastructure
```

Use:

```
terraform plan
```

to identify inconsistencies.

---

## Step 6 — Long-Term Prevention

Implement:

* Remote backend
* State versioning
* Restricted access
* Change controls

---

## Senior-Level Discussion

State should be treated as critical infrastructure metadata.

Manual editing is an emergency operation, not a normal workflow.

---

# Scenario 12 — Duplicate VPC Configurations Across Teams

## What Is The Interviewer Testing?

* Module Design
* Reusability
* Standardization

---

## Terraform Domains Involved

* Modules
* Versioning
* Governance

---

## Step 1 — Identify The Problem

Current design:

```
Team A VPC
Team B VPC
Team C VPC
```

Each repository contains duplicated code.

---

## Step 2 — Risks

* Inconsistent deployments
* Maintenance overhead
* Configuration drift
* Security inconsistencies

---

## Step 3 — Recommended Solution

Create:

```
terraform-modules/
└── aws-vpc-module
```

---

## Step 4 — Migration Strategy

Extract common logic.

Replace duplicated code with:

```hcl
module "vpc" {
  source = "..."
}
```

---

## Step 5 — Governance

Require:

* Module versioning
* Code reviews
* Documentation

---

## Senior-Level Discussion

The goal is platform standardization rather than simple code reuse.

---

# Scenario 13 — Breaking Module Update

## What Is The Interviewer Testing?

* Version Management
* Production Change Control

---

## Terraform Domains Involved

* Modules
* Semantic Versioning
* Release Management

---

## Step 1 — Identify Risk

Shared module affects:

```
20 Production Environments
```

---

## Step 2 — Questions To Ask

* Is change backward compatible?
* What resources are impacted?
* Is downtime possible?

---

## Step 3 — Immediate Recommendation

Never upgrade blindly.

Review:

```
terraform plan
```

for every environment.

---

## Step 4 — Rollout Strategy

Recommended:

```
Development
↓
Testing
↓
Staging
↓
Production
```

---

## Step 5 — Prevention

Pin module versions:

```hcl
version = "~> 2.5"
```

---

## Senior-Level Discussion

Treat modules like software products.

Versioning is governance.

---

# Scenario 14 — Module Has 80+ Variables

## What Is The Interviewer Testing?

* Module Architecture
* Maintainability

---

## Step 1 — Identify Problem

Module is trying to solve too many use cases.

---

## Step 2 — Risks

* Complexity
* Poor adoption
* Difficult troubleshooting
* Documentation burden

---

## Step 3 — Root Cause

Likely design philosophy:

```
One Module
For Everything
```

---

## Step 4 — Recommended Solution

Break module into:

```
Network Module
Compute Module
Security Module
```

---

## Step 5 — Design Principles

Prioritize:

* Simplicity
* Opinionated defaults
* Clear interfaces

---

## Trade-Off Discussion

### Highly Flexible Module

Pros:

* Supports many use cases

Cons:

* Difficult to maintain

### Focused Module

Pros:

* Easier adoption

Cons:

* More modules

---

## Senior-Level Discussion

A module should optimize for usability, not maximum configurability.

---

# Scenario 15 — Child Module Needs VPC ID

## What Is The Interviewer Testing?

* Module Communication
* Encapsulation

---

## Terraform Domains Involved

* Variables
* Outputs
* Modules

---

## Step 1 — Identify Requirement

Module A creates:

```
VPC
```

Module B needs:

```
VPC ID
```

---

## Step 2 — Correct Solution

Expose output:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

Pass as input.

---

## Step 3 — Why Not Direct References?

Direct access breaks:

* Encapsulation
* Reusability
* Maintainability

---

## Step 4 — Architecture Pattern

```
Network Module
↓ Output
VPC ID
↓ Input
Compute Module
```

---

## Senior-Level Discussion

Modules should communicate through explicit contracts.

---

# Scenario 16 — Database Password Committed To GitHub

## What Is The Interviewer Testing?

* Security Response
* Secret Management

---

## Terraform Domains Involved

* Secrets
* Vault
* Governance

---

## Step 1 — Treat As Security Incident

Assume compromise.

---

## Step 2 — Immediate Actions

Perform:

```
Rotate Password
Revoke Access
Audit Usage
```

Immediately.

---

## Step 3 — Repository Actions

Remove exposed secrets.

Review:

* Commit history
* Forks
* Clones

---

## Step 4 — Terraform Solution

Store secrets in:

* Vault
* AWS Secrets Manager
* Azure Key Vault

---

## Step 5 — Prevention

Implement:

* Secret scanning
* PR reviews
* Developer training

---

## Senior-Level Discussion

Focus on incident response and prevention.

---

# Scenario 17 — Engineer Assumes sensitive = true Fully Protects Secret

## What Is The Interviewer Testing?

* Terraform Security Knowledge
* Exam Trap Awareness

---

## Step 1 — Identify Incorrect Assumption

Engineer believes:

```hcl
sensitive = true
```

encrypts secrets.

---

## Step 2 — Reality

Sensitive values may still exist in:

* State
* Backend storage
* Provider systems

---

## Step 3 — Explain Risk

Hidden output ≠ protected secret.

---

## Step 4 — Proper Security Model

Combine:

```
Sensitive Variables
+
Vault
+
Encrypted Backend
```

---

## Senior-Level Discussion

This is one of the most common Terraform interview traps.

---

# Scenario 18 — Credential Rotation Every 30 Days

## What Is The Interviewer Testing?

* Secret Lifecycle Management
* Enterprise Security

---

## Terraform Domains Involved

* Vault
* Dynamic Credentials

---

## Step 1 — Identify Challenge

Manual rotation creates:

* Operational burden
* Human error
* Downtime risk

---

## Step 2 — Terraform Concern

Hardcoded credentials become difficult to manage.

---

## Step 3 — Recommended Solution

Use:

```
Vault
↓
Dynamic Credentials
↓
Terraform
```

---

## Step 4 — Benefits

* Automatic rotation
* Reduced exposure
* Better auditing

---

## Senior-Level Discussion

Focus on secret lifecycle rather than storage alone.

---

# Scenario 19 — Encryption Required For All Storage Buckets

## What Is The Interviewer Testing?

* Governance
* Policy Enforcement

---

## Terraform Domains Involved

* Modules
* Sentinel
* Compliance

---

## Step 1 — Identify Requirement

Organization mandates:

```
Encryption Everywhere
```

---

## Step 2 — Module-Level Enforcement

Implement secure defaults.

Example:

```
Encryption Enabled By Default
```

---

## Step 3 — Policy-Level Enforcement

Implement Sentinel:

```
No Encryption
=
Deployment Blocked
```

---

## Step 4 — Recommended Governance Model

Use both:

```
Modules
+
Policies
```

---

## Senior-Level Discussion

Defense in depth is preferred.

---

# Scenario 20 — 500 Existing AWS Resources

## What Is The Interviewer Testing?

* Migration Strategy
* Enterprise Terraform Adoption

---

## Terraform Domains Involved

* Import
* State
* Governance

---

## Step 1 — Do Not Start With Import

First:

```
Inventory
↓
Classification
↓
Prioritization
```

---

## Step 2 — Categorize Resources

Examples:

```
Networking
Security
Compute
Storage
Databases
```

---

## Step 3 — Migration Strategy

Recommended:

```
Pilot Environment
↓
Low Risk Resources
↓
Critical Resources
↓
Production
```

---

## Step 4 — Import Process

For each resource:

```
Write Terraform Code
↓
Import Resource
↓
Validate Plan
↓
Review
```

---

## Step 5 — Success Criteria

Terraform should become:

```
Single Source Of Truth
```

---

## Senior-Level Discussion

Large migrations are organizational projects, not merely technical projects.

Risk management is often more important than Terraform knowledge.

---

# Scenario 21 — Imported EC2 Instance Appears For Replacement

## What Is The Interviewer Testing?

* Import Workflow
* State Understanding
* Resource Lifecycle

---

## Terraform Domains Involved

* Import
* State
* Plan Analysis

---

## Step 1 — Identify The Problem

Resource was imported successfully.

However:

```
terraform plan
```

shows:

```
-/+
Resource Replacement
```

---

## Step 2 — Do Not Apply Immediately

Applying may:

* Destroy Production Resources
* Cause Downtime
* Lose Data

---

## Step 3 — Investigation

Review:

```
terraform plan
```

Questions:

* Which attribute changed?
* Is it immutable?
* Was configuration written correctly?
* Was import accurate?

---

## Step 4 — Common Causes

### Missing Attributes

Terraform configuration does not fully match resource.

### ForceNew Attributes

Certain changes require replacement.

### Incorrect Configuration

Imported infrastructure differs from code.

---

## Step 5 — Recovery Strategy

Compare:

```
AWS Resource
↓
Terraform State
↓
Terraform Code
```

Align all three.

---

## Senior-Level Discussion

Imports should always be followed by detailed plan review.

---

# Scenario 22 — Infrastructure Imported Without Configuration

## What Is The Interviewer Testing?

* Import Fundamentals
* Terraform State Knowledge

---

## Step 1 — Identify Problem

Engineer ran:

```
terraform import
```

but never created resource definitions.

---

## Step 2 — Why This Is Dangerous

Terraform only knows:

```
State Exists
```

but not:

```
Desired Configuration
```

---

## Step 3 — Risks

* Future plan failures
* Resource replacement
* Inconsistent deployments

---

## Step 4 — Correct Process

```
Write Configuration
↓
Import Resource
↓
Validate Plan
↓
Review State
```

---

## Step 5 — Long-Term Recommendation

Infrastructure ownership requires:

* State
* Configuration
* Version Control

All three must exist.

---

## Senior-Level Discussion

Import alone is not Terraform adoption.

---

# Scenario 23 — Local State + Email Approvals

## What Is The Interviewer Testing?

* HCP Terraform Value Proposition
* Governance

---

## Terraform Domains Involved

* HCP Terraform
* Remote State
* Collaboration

---

## Step 1 — Identify Problems

Current model:

```
Local State
+
Email Approval
```

Issues:

* No audit trail
* No locking
* Weak governance
* Poor visibility

---

## Step 2 — Risks

* State loss
* Unauthorized changes
* Approval ambiguity

---

## Step 3 — Recommended Solution

Migrate to:

```
HCP Terraform
```

---

## Step 4 — Features Gained

* Remote State
* State Locking
* Run History
* Access Controls
* Approval Workflows

---

## Step 5 — Migration Plan

```
Create Organization
↓
Create Workspaces
↓
Migrate State
↓
Integrate GitHub
↓
Enable Governance
```

---

## Senior-Level Discussion

Replace human processes with platform controls.

---

# Scenario 24 — Production Infrastructure Modified Through Pull Request

## What Is The Interviewer Testing?

* Speculative Plans
* Review Processes

---

## Step 1 — Identify Requirement

Team wants visibility before deployment.

---

## Step 2 — HCP Terraform Feature

Use:

```
Speculative Plans
```

---

## Step 3 — Workflow

```
Pull Request
↓
Speculative Plan
↓
Review
↓
Approval
↓
Apply
```

---

## Step 4 — Benefits

* Infrastructure preview
* Early error detection
* Safer deployments

---

## Step 5 — Governance Improvements

Require:

* PR approvals
* Branch protection
* Change review

---

## Senior-Level Discussion

Treat infrastructure reviews like application code reviews.

---

# Scenario 25 — Automated Compliance Checks Required

## What Is The Interviewer Testing?

* Policy-As-Code
* Governance

---

## Terraform Domains Involved

* Sentinel
* HCP Terraform

---

## Step 1 — Identify Requirement

Compliance must be enforced automatically.

---

## Step 2 — Recommended Solution

Implement:

```
Sentinel Policies
```

---

## Step 3 — Example Policies

### Security

```
No Public S3 Buckets
```

### Cost Control

```
Approved Instance Types
```

### Governance

```
Mandatory Tags
```

---

## Step 4 — Failure Handling

```
Policy Failure
↓
Apply Blocked
```

---

## Senior-Level Discussion

Governance should be automated, not dependent on reviewers.

---

# Scenario 26 — Security Scanning During Terraform Runs

## What Is The Interviewer Testing?

* Run Tasks
* Security Integration

---

## Step 1 — Requirement

Security team wants automated scanning.

---

## Step 2 — HCP Terraform Solution

Implement:

```
Run Tasks
```

---

## Step 3 — Example Integrations

* Wiz
* Prisma Cloud
* Checkov
* Snyk

---

## Step 4 — Workflow

```
Terraform Plan
↓
Run Task
↓
Security Analysis
↓
Pass / Fail
```

---

## Step 5 — Benefits

* Shift-left security
* Automated governance
* Consistent enforcement

---

## Senior-Level Discussion

Security should be integrated into deployment workflows.

---

# Scenario 27 — 50 AWS Accounts, Hundreds Of Applications

## What Is The Interviewer Testing?

* Enterprise Terraform Architecture
* Multi-Account Strategy

---

## Step 1 — Identify Scale

Environment contains:

```
50 AWS Accounts
Multiple Regions
Hundreds of Services
```

---

## Step 2 — Design Principles

Prioritize:

* Isolation
* Reuse
* Governance
* Scalability

---

## Step 3 — Recommended Architecture

```
Shared Modules
↓
Environment Repositories
↓
Account Separation
↓
Independent State
```

---

## Step 4 — State Strategy

Never use:

```
Single Shared State
```

Use:

```
State Per Environment
State Per Account
```

---

## Step 5 — Governance

Implement:

* Sentinel
* CI/CD
* Role-Based Access

---

## Senior-Level Discussion

Organizational scalability matters more than Terraform syntax.

---

# Scenario 28 — Emergency Production Changes

## What Is The Interviewer Testing?

* Incident Management
* Drift Handling

---

## Step 1 — Incident Occurs

Production outage requires immediate action.

---

## Step 2 — Decision Point

Should engineers make manual changes?

Answer:

```
Possibly
```

if service restoration requires it.

---

## Step 3 — Priority

```
Restore Service
↓
Protect Customers
↓
Restore Availability
```

---

## Step 4 — Post-Incident Actions

Update:

```
Terraform Code
```

to match changes.

---

## Step 5 — Drift Resolution

Run:

```
terraform plan
```

Determine differences.

---

## Senior-Level Discussion

Service restoration takes priority.

Terraform consistency follows immediately afterward.

---

# Scenario 29 — Auditor Requests Infrastructure Change History

## What Is The Interviewer Testing?

* Auditability
* Governance

---

## Step 1 — Identify Requirement

Auditor wants:

```
Who
Changed
What
When
Why
```

---

## Step 2 — Evidence Sources

Use:

* Git History
* Pull Requests
* HCP Run History
* Audit Logs

---

## Step 3 — Governance Controls

Implement:

* Mandatory Reviews
* Ticket References
* Protected Branches

---

## Step 4 — Long-Term Recommendation

Infrastructure changes should always be:

```
Version Controlled
```

---

## Senior-Level Discussion

Auditability is a platform capability, not a manual process.

---

# Scenario 30 — Internal Developer Platform

## What Is The Interviewer Testing?

* Platform Engineering
* Self-Service Infrastructure

---

## Step 1 — Identify Goal

Hundreds of developers require infrastructure.

---

## Step 2 — Challenges

* Governance
* Standardization
* Security
* Scalability

---

## Step 3 — Recommended Architecture

```
Approved Modules
↓
Developer Portal
↓
CI/CD
↓
Terraform
```

---

## Step 4 — Governance Controls

Implement:

* Sentinel
* Run Tasks
* Policy Enforcement
* Access Controls

---

## Step 5 — Self-Service Model

Developers consume:

```
Products
```

not raw infrastructure.

---

## Example

Instead of:

```
Create VPC
Create Subnets
Create Security Groups
```

Developers request:

```
Standard Application Environment
```

---

## Senior-Level Discussion

Terraform becomes a platform capability rather than a deployment tool.

---

# Scenario 31 — Design Terraform Architecture for Development, Staging, and Production

## What Is The Interviewer Testing?

* Environment Strategy
* Enterprise Terraform Design
* Isolation Principles

---

## Terraform Domains Involved

* Workspaces
* State Management
* Modules
* Governance

---

## Step 1 — Identify Requirements

Organization requires:

```
Development
Staging
Production
```

with strict isolation.

---

## Step 2 — Define Design Goals

Requirements:

* Environment isolation
* Independent deployments
* Independent state
* Controlled promotion

---

## Step 3 — Architecture Recommendation

Avoid:

```
Single State
Single Environment
```

Recommended:

```
terraform-live/

├── dev/
├── stage/
└── prod/
```

---

## Step 4 — Module Strategy

Shared:

```
terraform-modules/

├── networking
├── compute
├── security
└── database
```

Environment folders consume modules.

---

## Step 5 — State Strategy

Each environment gets:

```
Dedicated Backend
Dedicated State
Dedicated Locking
```

Example:

```
Dev State
Stage State
Prod State
```

Never share state across environments.

---

## Step 6 — Deployment Flow

Recommended:

```
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

## Step 7 — Governance

Implement:

* Pull Requests
* CI/CD Validation
* Sentinel Policies
* Approval Gates

---

## Trade-Off Discussion

### Single Environment

Pros:

* Simple

Cons:

* Unsafe
* Poor scalability

---

### Environment Isolation

Pros:

* Secure
* Scalable
* Predictable

Cons:

* Additional management overhead

---

## Senior-Level Discussion

The primary objective is not infrastructure creation.

The objective is safe change promotion across environments.

---

# Scenario 32 — Design Remote State Architecture for Multi-Team AWS Organization

## What Is The Interviewer Testing?

* State Design
* Collaboration
* Governance

---

## Terraform Domains Involved

* Backends
* State Locking
* HCP Terraform

---

## Step 1 — Identify Scale

Organization contains:

```
Multiple Teams
Multiple Accounts
Multiple Environments
```

---

## Step 2 — Design Principles

State must provide:

* Isolation
* Recovery
* Locking
* Auditability

---

## Step 3 — Poor Design Example

Avoid:

```
One State File
For Entire Organization
```

Problems:

* Large blast radius
* Complex recovery
* Team conflicts

---

## Step 4 — Recommended Design

```
Account
↓
Environment
↓
Application
↓
State File
```

---

## Example

```
AWS Account A
 ├── Dev
 ├── Stage
 └── Prod

AWS Account B
 ├── Dev
 ├── Stage
 └── Prod
```

Each environment owns separate state.

---

## Step 5 — Backend Recommendation

Preferred:

```
HCP Terraform
```

Alternative:

```
S3
+
DynamoDB
```

---

## Step 6 — Recovery Strategy

Implement:

* Versioning
* Backups
* State History
* Recovery Testing

---

## Senior-Level Discussion

State architecture should minimize organizational blast radius.

---

# Scenario 33 — Design Module Strategy for Hundreds of Microservices

## What Is The Interviewer Testing?

* Module Architecture
* Platform Engineering

---

## Terraform Domains Involved

* Modules
* Versioning
* Governance

---

## Step 1 — Identify Challenge

Environment contains:

```
Hundreds of Services
Many Teams
Many Deployments
```

---

## Step 2 — Common Failure

Teams create:

```
Custom Terraform
For Every Service
```

Result:

* Duplication
* Drift
* Maintenance burden

---

## Step 3 — Platform Approach

Build reusable modules.

Example:

```
Application Module
Database Module
Networking Module
Monitoring Module
```

---

## Step 4 — Design Principles

Modules should be:

* Opinionated
* Versioned
* Documented
* Secure by Default

---

## Step 5 — Versioning Strategy

Implement:

```
Semantic Versioning
```

Example:

```
v1.0.0
v1.1.0
v2.0.0
```

---

## Step 6 — Governance

Require:

* Approved Modules
* Security Reviews
* CI/CD Validation

---

## Trade-Off Discussion

### Flexible Modules

Pros:

* Highly customizable

Cons:

* Complex

---

### Opinionated Modules

Pros:

* Easy adoption
* Consistency

Cons:

* Reduced flexibility

---

## Senior-Level Discussion

Enterprise platforms optimize for consistency rather than customization.

---

# Scenario 34 — Design Disaster Recovery Strategy for Terraform State

## What Is The Interviewer Testing?

* Business Continuity
* State Recovery

---

## Terraform Domains Involved

* State
* Backends
* Recovery

---

## Step 1 — Identify Importance

Terraform State is:

```
Critical Infrastructure Metadata
```

Loss can impact:

* Deployments
* Recovery
* Operations

---

## Step 2 — Define Recovery Objectives

Questions:

* How quickly must recovery occur?
* What data loss is acceptable?

---

## Step 3 — Recommended Architecture

```
Remote Backend
↓
Versioning
↓
Backups
↓
Recovery Testing
```

---

## Step 4 — Example AWS Design

```
S3 Backend
↓
Versioning Enabled
↓
Cross-Region Backup
↓
DynamoDB Locking
```

---

## Step 5 — Recovery Procedure

```
Identify Failure
↓
Locate Backup
↓
Restore State
↓
Validate Infrastructure
↓
Resume Operations
```

---

## Step 6 — Validation

Run:

```
terraform plan
```

Confirm:

```
State
=
Infrastructure
```

---

## Governance Controls

Implement:

* Backup Verification
* Recovery Drills
* Access Controls

---

## Senior-Level Discussion

Disaster recovery plans that are never tested do not exist.

---

# Scenario 35 — Design Governance Framework Using HCP Terraform, Sentinel, Run Tasks, and GitHub

## What Is The Interviewer Testing?

* Platform Governance
* Enterprise Terraform Operations

---

## Terraform Domains Involved

* HCP Terraform
* Sentinel
* Run Tasks
* GitOps

---

## Step 1 — Define Governance Goals

Requirements:

* Security
* Compliance
* Auditability
* Standardization

---

## Step 2 — GitHub Responsibilities

GitHub becomes:

```
Source of Truth
```

Responsibilities:

* Version Control
* Pull Requests
* Code Reviews
* Branch Protection

---

## Step 3 — HCP Terraform Responsibilities

Provides:

* Remote Execution
* State Management
* Run History
* Access Controls

---

## Step 4 — Sentinel Responsibilities

Enforce:

```
Mandatory Tags
Approved Regions
Encryption
Naming Standards
```

---

## Step 5 — Run Tasks Responsibilities

Integrate:

* Security Scanners
* Compliance Tools
* Cost Analysis Tools

---

## Step 6 — Recommended Workflow

```
Developer
↓
GitHub Pull Request
↓
Speculative Plan
↓
Sentinel Policies
↓
Run Tasks
↓
Approval
↓
Terraform Apply
```

---

## Step 7 — Failure Handling

Examples:

### Sentinel Failure

```
Deployment Blocked
```

### Security Scan Failure

```
Deployment Blocked
```

### Approval Missing

```
Deployment Blocked
```

---

## Step 8 — Governance Layers

```
Layer 1
GitHub Reviews

Layer 2
Terraform Plans

Layer 3
Sentinel Policies

Layer 4
Run Tasks

Layer 5
Approvals
```

---

## Trade-Off Discussion

### Heavy Governance

Pros:

* Security
* Compliance
* Auditability

Cons:

* Slower delivery

---

### Lightweight Governance

Pros:

* Faster deployments

Cons:

* Increased risk

---

## Senior-Level Discussion

The objective is not preventing deployments.

The objective is enabling safe deployments at organizational scale.

---
