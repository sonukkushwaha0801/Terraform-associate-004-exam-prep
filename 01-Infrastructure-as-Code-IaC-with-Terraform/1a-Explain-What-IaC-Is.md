# Objective: 1a - Explain What IaC Is

## Definition

Infrastructure as Code (IaC) is the practice of provisioning, configuring, and managing infrastructure through machine-readable configuration files rather than manual processes.

Infrastructure resources such as virtual machines, networks, databases, load balancers, and security policies are defined as code and managed using version control systems.

Terraform is an Infrastructure as Code tool that uses declarative configuration files to define the desired state of infrastructure.

---

## Core Concepts

### Infrastructure

Infrastructure includes:

* Virtual Machines
* Networks
* Storage
* Databases
* Load Balancers
* DNS Records
* Security Groups

### Code-Driven Management

Infrastructure is defined in files rather than manually configured through a web console.

### Version Control

Infrastructure definitions can be stored in Git repositories, enabling collaboration, auditing, and rollback capabilities.

### Automation

Infrastructure can be provisioned automatically through Terraform commands and CI/CD pipelines.

### Desired State

Terraform focuses on defining the desired infrastructure state rather than specifying every step required to create it.

---

## How It Works

Traditional Infrastructure Management:

1. Log in to cloud console
2. Create resources manually
3. Configure settings manually
4. Repeat for every environment

Infrastructure as Code:

1. Define infrastructure in configuration files
2. Store configuration in version control
3. Review changes
4. Apply configuration using Terraform
5. Terraform provisions infrastructure automatically

---

## Terraform Perspective

Terraform implements Infrastructure as Code using declarative configuration files written in HashiCorp Configuration Language (HCL).

Example:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456789"
  instance_type = "t3.micro"
}
```

Terraform compares:

* Current State
* Desired State

Then determines the actions required to reach the desired state.

---

## Real-World Example

A company requires:

* 3 Virtual Machines
* 1 Database
* 1 Load Balancer
* 2 Subnets

Without IaC:

An engineer manually provisions every component.

With IaC:

All resources are defined in Terraform configuration files and deployed consistently using:

```bash
terraform apply
```

---

## Production Use Case

A fintech organization manages:

* Development Environment
* Staging Environment
* Production Environment

Using Terraform:

* Infrastructure definitions are stored in Git
* Pull requests review infrastructure changes
* CI/CD pipelines automate deployments
* Infrastructure remains consistent across environments

---

## Important Exam Points

* Terraform is an Infrastructure as Code tool.
* Terraform uses a declarative approach.
* Infrastructure is managed through configuration files.
* Infrastructure definitions can be version controlled.
* IaC promotes consistency and repeatability.
* Terraform manages desired state.
* Terraform is not a configuration management tool like Ansible.

---

## Common Exam Traps

### Trap 1

Question:

What does Terraform manage?

Wrong:

* AWS
* Azure
* Virtual Machines

Correct:

Terraform manages infrastructure through configuration files.

### Trap 2

Question:

Is Terraform imperative or declarative?

Correct:

Terraform is declarative.

### Trap 3

Question:

Does Terraform execute manual provisioning steps?

Correct:

No. Terraform determines the required actions automatically based on the desired state.

---

## Interview Questions

### What is Infrastructure as Code?

Infrastructure as Code is the practice of managing and provisioning infrastructure using machine-readable configuration files instead of manual processes.

### Why do organizations adopt IaC?

To improve consistency, automation, repeatability, scalability, collaboration, and auditability.

### How does Terraform implement IaC?

Terraform uses declarative configuration files that define the desired state of infrastructure.

### What is the difference between traditional provisioning and IaC?

Traditional provisioning relies on manual actions, whereas IaC uses code-driven automation.

### Why is version control important for infrastructure?

Version control provides history, collaboration, change tracking, reviews, and rollback capabilities.

---

## Practice Questions

### Question 1

Which statement best describes Infrastructure as Code?

A. Managing infrastructure through cloud consoles

B. Managing infrastructure through machine-readable configuration files

C. Managing source code repositories

D. Monitoring infrastructure performance

**Answer:** B

**Explanation:** IaC provisions and manages infrastructure through configuration files rather than manual processes.

---

### Question 2

Terraform primarily follows which model?

A. Imperative

B. Declarative

C. Procedural

D. Object-Oriented

**Answer:** B

**Explanation:** Terraform defines the desired state and determines how to achieve it.

---

### Question 3

Which capability is NOT commonly associated with Infrastructure as Code?

A. Version Control

B. Repeatability

C. Manual Configuration

D. Automation

**Answer:** C

**Explanation:** IaC replaces manual configuration with automated, code-driven infrastructure management.

---

### Question 4

What is Terraform's primary purpose?

A. Monitoring Infrastructure

B. Managing Infrastructure as Code

C. Managing Source Code

D. Performing Application Testing

**Answer:** B

**Explanation:** Terraform provisions and manages infrastructure through declarative configuration files.

---

### Question 5

A team stores Terraform configurations in Git. Which IaC benefit is being utilized?

A. Version Control

B. Load Balancing

C. Encryption

D. Monitoring

**Answer:** A

**Explanation:** Git provides version control, auditing, and collaboration capabilities for infrastructure definitions.

---

## Related Objectives

* 1b Describe the Advantages of IaC Patterns
* 2d Explain How Terraform Uses and Manages State
* 3a Describe the Terraform Workflow
* 4f Define Resource Dependencies in Configuration
* 6d Manage Resource Drift and Terraform State

---

## Key Takeaways

* Infrastructure as Code manages infrastructure through code.
* Terraform is a declarative IaC tool.
* Infrastructure definitions are version controlled.
* IaC enables automation, consistency, and repeatability.
* Terraform manages desired state through configuration files.
* Understanding IaC fundamentals is essential for the Terraform Associate (004) exam.
