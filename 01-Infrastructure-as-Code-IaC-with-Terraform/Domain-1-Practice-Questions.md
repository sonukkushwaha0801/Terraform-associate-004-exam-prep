# Domain 1 Practice Questions

## Infrastructure as Code (IaC) with Terraform

### Instructions

Attempt all questions before checking the answers.

✅ Do not scroll to the answer section until you have completed all questions.

✅ Record your answers separately (for example: 1-B, 2-B, 3-D, etc.).

✅ After completing all questions, verify your responses using the Answer Key at the end of this document.

---

### Question 1

Which statement best defines Infrastructure as Code (IaC)?

A. Managing infrastructure through cloud consoles

B. Managing infrastructure through machine-readable configuration files

C. Managing application source code

D. Managing infrastructure through spreadsheets

---

### Question 2

Terraform primarily follows which infrastructure management approach?

A. Imperative

B. Declarative

C. Procedural

D. Sequential

---

### Question 3

Which of the following is considered infrastructure?

A. Virtual Machines

B. Networks

C. Databases

D. All of the above

---

### Question 4

Which problem is Infrastructure as Code designed to reduce?

A. Network latency

B. Human error

C. Database indexing

D. Source code compilation

---

### Question 5

Why do organizations store Terraform configurations in Git?

A. To improve network performance

B. To provide version control and collaboration

C. To replace Terraform state

D. To host infrastructure resources

---

### Question 6

Terraform manages infrastructure through:

A. Manual console operations

B. Configuration files

C. Database records

D. Monitoring dashboards

---

### Question 7

Which characteristic allows infrastructure to be recreated consistently across environments?

A. Monitoring

B. Encryption

C. Repeatability

D. Compression

---

### Question 8

Which IaC benefit helps teams understand who changed infrastructure and when?

A. Auditability

B. Scalability

C. Load Balancing

D. Replication

---

### Question 9

Terraform determines the actions required to reach:

A. Current State

B. Desired State

C. Previous State

D. Temporary State

---

### Question 10

Which statement is TRUE about Terraform?

A. Terraform only works with AWS

B. Terraform only manages virtual machines

C. Terraform is a cloud-agnostic Infrastructure as Code tool

D. Terraform requires separate workflows for every cloud provider

---

## Scenario-Based Questions

### Question 11

A company provisions all cloud resources manually through the cloud console. Different engineers often create resources with slightly different configurations.

Which Infrastructure as Code benefit would MOST directly solve this problem?

A. Monitoring

B. Consistency

C. Encryption

D. Replication

---

### Question 12

A team wants to recreate an identical staging environment whenever needed using the same Terraform configuration.

Which IaC benefit are they utilizing?

A. Auditability

B. Scalability

C. Repeatability

D. Logging

---

### Question 13

An engineer accidentally deletes an AWS VPC. The Terraform configuration still exists in Git.

Which IaC benefit helps recover from this situation?

A. Disaster Recovery

B. Compression

C. Monitoring

D. Replication

---

### Question 14

A company requires all infrastructure changes to be reviewed before deployment.

Which IaC-related practice best supports this requirement?

A. Manual Provisioning

B. Git Pull Requests

C. Console-Based Changes

D. Direct Production Access

---

### Question 15

A company uses AWS for compute resources and Azure for identity services.

Which architecture model is being used?

A. Hybrid Cloud

B. Multi-Cloud

C. Immutable Infrastructure

D. Configuration Management

---

### Question 16

A company manages AWS resources, Azure resources, and Cloudflare DNS records using Terraform.

Which Terraform capability enables this approach?

A. State Files

B. Variables

C. Providers

D. Outputs

---

### Question 17

An organization wants to track who modified infrastructure and when the change occurred.

Which IaC advantage is MOST relevant?

A. Auditability

B. Scalability

C. Availability

D. Performance

---

### Question 18

A company uses VMware infrastructure on-premises and AWS in the cloud. Terraform manages both environments.

Which deployment model is this?

A. Multi-Cloud

B. Hybrid Cloud

C. Single Cloud

D. Serverless

---

### Question 19

A team provisions infrastructure using Terraform and stores all configuration files in Git.

Which two IaC benefits are MOST directly achieved?

A. Version Control and Collaboration

B. Monitoring and Logging

C. Encryption and Security

D. Compression and Replication

---

### Question 20

A company manages GitHub repositories, Kubernetes clusters, and AWS resources using Terraform.

What does this demonstrate?

A. Terraform is AWS-specific

B. Terraform only manages cloud infrastructure

C. Terraform is service-agnostic

D. Terraform is a configuration management tool

---

## HashiCorp Exam-Trap Questions

### Question 21

Which statement BEST describes Terraform?

A. A cloud provider

B. A configuration management tool

C. An Infrastructure as Code tool

D. A container orchestration platform

---

### Question 22

Terraform primarily manages infrastructure through:

A. Cloud Console Operations

B. Manual Administrative Actions

C. Configuration Files

D. Monitoring Dashboards

---

### Question 23

Which statement about Terraform is TRUE?

A. Terraform only works with AWS

B. Terraform only supports cloud resources

C. Terraform can manage infrastructure across multiple providers

D. Terraform requires separate workflows for every provider

---

### Question 24

A team defines infrastructure in Terraform and commits it to Git.

Which IaC capability is MOST directly achieved?

A. High Availability

B. Version Control

C. Encryption

D. Monitoring

---

### Question 25

Terraform users specify:

A. Every API request to execute

B. Every infrastructure provisioning step

C. The desired state of infrastructure

D. The cloud provider implementation details

---

### Question 26

Which statement about Infrastructure as Code is FALSE?

A. Infrastructure definitions can be version controlled.

B. Infrastructure can be recreated consistently.

C. Infrastructure changes must always be performed manually.

D. Infrastructure can be automated.

---

### Question 27

Which Terraform feature enables management of AWS, Azure, Kubernetes, GitHub, and Cloudflare?

A. Variables

B. Providers

C. Outputs

D. Locals

---

### Question 28

A company manages infrastructure on AWS and Azure using Terraform.

Which Terraform capability is being demonstrated?

A. Configuration Drift

B. Multi-Cloud Management

C. State Locking

D. Resource Import

---

### Question 29

A company manages VMware infrastructure on-premises and AWS in the cloud.

Which architecture does this represent?

A. Multi-Cloud

B. Service Discovery

C. Hybrid Cloud

D. Immutable Infrastructure

---

### Question 30

Which statement BEST describes a provider?

A. A Terraform state file

B. A plugin that allows Terraform to interact with APIs

C. A Terraform module

D. A Terraform workspace

---


## Domain 1 Coverage Matrix

| Topic                      | Questions Covered |
| -------------------------- | ----------------- |
| IaC Definition             | 1, 21, 22         |
| Declarative Model          | 2, 25             |
| Infrastructure Components  | 3                 |
| Human Error Reduction      | 4                 |
| Version Control            | 5, 24             |
| Configuration Files        | 6, 22             |
| Repeatability              | 7, 12             |
| Auditability               | 8, 17             |
| Desired State              | 9, 25             |
| Cloud-Agnostic Terraform   | 10, 23            |
| Consistency                | 11                |
| Disaster Recovery          | 13                |
| Collaboration              | 14, 19            |
| Multi-Cloud                | 15, 28            |
| Providers                  | 16, 27, 30        |
| Hybrid Cloud               | 18, 29            |
| Service-Agnostic Workflows | 20                |

---

## Self-Assessment

### 27-30 Correct

Excellent. Domain 1 is exam-ready.

### 23-26 Correct

Strong understanding. Review explanations and retry missed questions.

### 18-22 Correct

Good foundation. Revisit objectives 1a, 1b, and 1c.

### Below 18 Correct

Review Domain 1 notes completely before moving to Domain 2.

---

## Domain Completion Checklist

* [ ] Read 1a - Explain What IaC Is
* [ ] Read 1b - Advantages of IaC Patterns
* [ ] Read 1c - Multi-Cloud, Hybrid Cloud, and Service-Agnostic Workflows
* [ ] Completed Domain 1 Practice Questions
* [ ] Scored 27+/30
* [ ] Reviewed Incorrect Answers
* [ ] Ready for Domain 2
