# Domain 1 Revision Sheet

## Infrastructure as Code (IaC) with Terraform

### Objectives Covered

* 1a - Explain What IaC Is
* 1b - Describe the Advantages of IaC Patterns
* 1c - Explain How Terraform Manages Multi-Cloud, Hybrid Cloud, and Service-Agnostic Workflows

---

# Infrastructure as Code (IaC)

## Definition

Infrastructure managed through machine-readable configuration files instead of manual processes.

Terraform is an Infrastructure as Code (IaC) tool.

---

## Terraform Characteristics

| Characteristic         | Terraform |
| ---------------------- | --------- |
| Infrastructure as Code | ✅         |
| Declarative            | ✅         |
| Open Source            | ✅         |
| Cloud Agnostic         | ✅         |
| Service Agnostic       | ✅         |
| Multi-Cloud Support    | ✅         |
| Hybrid Cloud Support   | ✅         |

---

## Infrastructure Examples

* Virtual Machines
* Networks
* Subnets
* Databases
* Load Balancers
* Storage
* DNS Records
* Security Groups

---

# Declarative vs Imperative

## Declarative

Define:

```text id="a3rt01"
What infrastructure should look like
```

Terraform determines:

```text id="u1hloq"
How to achieve it
```

Terraform uses:

✅ Declarative Model

---

## Imperative

Define:

```text id="5jxks7"
Step-by-step instructions
```

Examples:

* Shell Scripts
* Manual Commands

Terraform is NOT imperative.

---

# Desired State

Terraform manages:

✅ Desired State

Terraform compares:

```text id="z69z54"
Current State
        vs
Desired State
```

Terraform then calculates required actions.

---

# Core Benefits of IaC

## Consistency

Same configuration → Same infrastructure

---

## Repeatability

Infrastructure can be recreated reliably.

---

## Automation

Reduced manual provisioning.

---

## Auditability

Track:

* Who changed it
* What changed
* When it changed

---

## Collaboration

Teams work through:

* Git
* Pull Requests
* Code Reviews

---

## Scalability

Infrastructure can grow through configuration updates.

---

## Disaster Recovery

Infrastructure can be rebuilt from code.

---

# Version Control Benefits

Git enables:

* Change Tracking
* Rollback
* Collaboration
* Auditability
* Pull Requests

Infrastructure definitions should be stored in Git.

---

# Terraform Providers

## Definition

Providers are plugins that allow Terraform to communicate with APIs.

---

## Examples

* hashicorp/aws
* hashicorp/azurerm
* hashicorp/google
* hashicorp/kubernetes
* integrations/github
* cloudflare/cloudflare

---

## Provider Role

```text
Terraform
    │
    ├── AWS Provider
    ├── Azure Provider
    ├── Google Provider
    ├── GitHub Provider
    └── Cloudflare Provider
```

Without providers:

❌ Terraform cannot manage resources.

---

# Multi-Cloud

## Definition

Using multiple cloud providers.

### Example

* AWS
* Azure

Result:

✅ Multi-Cloud

---

# Hybrid Cloud

## Definition

Using:

* Public Cloud
* On-Premises Infrastructure

Together.

### Example

* AWS
* VMware

Result:

✅ Hybrid Cloud

---

# Service-Agnostic

Terraform can manage:

* Cloud Resources
* Kubernetes
* GitHub
* Cloudflare
* Datadog

Terraform is NOT limited to cloud infrastructure.

---

# High-Probability Exam Facts

* Terraform is an IaC tool.
* Terraform is declarative.
* Terraform manages desired state.
* Terraform uses configuration files.
* Terraform uses providers.
* Providers are plugins.
* Terraform is cloud-agnostic.
* Terraform is service-agnostic.
* Terraform supports multi-cloud.
* Terraform supports hybrid cloud.
* Infrastructure should be version controlled.
* Git is commonly used for infrastructure versioning.

---

# Common Exam Traps

## Trap 1

Terraform is:

✅ Infrastructure as Code

❌ Configuration Management

---

## Trap 2

Terraform uses:

✅ Declarative Model

❌ Imperative Model

---

## Trap 3

Terraform manages:

✅ Desired State

❌ Execution Steps

---

## Trap 4

AWS + Azure

✅ Multi-Cloud

❌ Hybrid Cloud

---

## Trap 5

AWS + VMware

✅ Hybrid Cloud

❌ Multi-Cloud

---

## Trap 6

Providers are:

✅ Plugins

❌ Modules

❌ State Files

❌ Workspaces

---

# 30-Second Final Revision

Remember:

* IaC = Infrastructure through code.
* Terraform = Declarative IaC tool.
* Terraform manages desired state.
* Git provides version control.
* Providers are plugins.
* AWS + Azure = Multi-Cloud.
* AWS + VMware = Hybrid Cloud.
* Terraform is cloud-agnostic.
* Terraform is service-agnostic.
* Consistency + Repeatability + Auditability are major IaC benefits.
