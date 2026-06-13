# Domain 6 Practice Questions

## Terraform State Management

### Domain Statistics

- Objectives Covered: 4
- Total Questions: 40
- Conceptual Questions: 15
- Scenario-Based Questions: 15
- HashiCorp Exam-Trap Questions: 10

---

# Instructions

Attempt all questions before checking answers.

✅ Record answers separately.

✅ Complete all questions before reviewing explanations.

✅ Passing Target: 35+/40

---

# Conceptual Questions

### Question 1

What is the primary purpose of Terraform state?

A. Store Providers

B. Track Managed Infrastructure

C. Store Variables

D. Store Modules

---

### Question 2

What is Terraform's default backend?

A. S3

B. AzureRM

C. Local

D. HCP Terraform

---

### Question 3

Which file stores Terraform state?

A. terraform.tfvars

B. terraform.lock.hcl

C. terraform.tfstate

D. state.tf

---

### Question 4

Which file stores the previous state version?

A. terraform.backup

B. terraform.tfstate.backup

C. state.bak

D. backup.tfstate

---

### Question 5

Which component determines where Terraform stores state?

A. Provider

B. Module

C. Backend

D. Output

---

### Question 6

Why does Terraform require state?

A. To Install Providers

B. To Track Infrastructure

C. To Format Code

D. To Validate Syntax

---

### Question 7

What is a remote backend?

A. Stores State Remotely

B. Stores Providers

C. Stores Variables

D. Stores Modules

---

### Question 8

What is state locking designed to prevent?

A. Resource Creation

B. Concurrent State Modifications

C. Provider Installation

D. Drift Detection

---

### Question 9

When does Terraform acquire a state lock?

A. After Apply

B. Before State Modification

C. During Init Only

D. During Destroy Only

---

### Question 10

When is a state lock released?

A. Before Planning

B. During Validation

C. After Operation Completion

D. Before Init

---

### Question 11

What is resource drift?

A. State File Corruption

B. Infrastructure Changes Outside Terraform

C. Provider Upgrade

D. Module Refactoring

---

### Question 12

Which command commonly detects drift?

A. terraform fmt

B. terraform validate

C. terraform plan

D. terraform init

---

### Question 13

Which command lists resources tracked by state?

A. terraform state show

B. terraform show

C. terraform state list

D. terraform state rm

---

### Question 14

Which command displays detailed resource information from state?

A. terraform state show

B. terraform state list

C. terraform inspect

D. terraform refresh

---

### Question 15

Which command imports existing infrastructure into Terraform state?

A. terraform state import

B. terraform import

C. terraform state mv

D. terraform state rm

---

# Scenario-Based Questions

### Question 16

A team stores Terraform state on a developer laptop.

What backend is being used?

A. S3

B. HCP Terraform

C. Local

D. AzureRM

---

### Question 17

Two engineers run:

```bash
terraform apply
```

simultaneously.

Which Terraform feature prevents state corruption?

A. Variables

B. Outputs

C. State Locking

D. Modules

---

### Question 18

A company wants centralized state shared across multiple engineers.

What should be implemented?

A. Local Backend

B. Remote Backend

C. Local Variables

D. Outputs

---

### Question 19

A company stores Terraform state in an S3 bucket.

What type of backend is this?

A. Local

B. Remote

C. Dynamic

D. Module

---

### Question 20

An engineer manually changes an EC2 instance size through the AWS Console.

What has occurred?

A. State Lock

B. Resource Drift

C. Backend Migration

D. Import

---

### Question 21

An engineer wants to see all resources Terraform currently manages.

Which command should be used?

A. terraform show

B. terraform state show

C. terraform state list

D. terraform graph

---

### Question 22

An engineer wants to inspect the details of:

```text
aws_instance.web
```

Which command should be used?

A. terraform state show

B. terraform state list

C. terraform inspect

D. terraform validate

---

### Question 23

A company wants to move a resource entry to a different state address after refactoring.

Which command should be used?

A. terraform state rm

B. terraform state mv

C. terraform import

D. terraform show

---

### Question 24

An engineer wants Terraform to stop tracking a resource without deleting it.

Which command should be used?

A. terraform destroy

B. terraform state rm

C. terraform state mv

D. terraform import

---

### Question 25

A VPC already exists in AWS.

Terraform should begin managing it.

Which command should be used?

A. terraform state rm

B. terraform apply

C. terraform import

D. terraform validate

---

### Question 26

A team migrates state from local storage to S3.

Which command initializes the backend migration?

A. terraform validate

B. terraform init

C. terraform fmt

D. terraform state list

---

### Question 27

Terraform reports:

```text
Error acquiring state lock
```

What is the most likely reason?

A. Syntax Error

B. Concurrent Operation

C. Missing Variable

D. Invalid Module

---

### Question 28

A stale lock remains after a system crash.

Which command removes it?

A. terraform unlock

B. terraform force-unlock

C. terraform state rm

D. terraform refresh

---

### Question 29

A team wants backup, centralized storage, and collaboration.

Which backend type should be used?

A. Local

B. Remote

C. Dynamic

D. Embedded

---

### Question 30

An engineer runs:

```bash
terraform plan
```

and Terraform proposes reverting console changes.

What is Terraform detecting?

A. Locking

B. Drift

C. Import

D. Module Upgrade

---

# HashiCorp Exam-Trap Questions

### Question 31

Which backend is used when no backend block is configured?

A. S3

B. Local

C. HCP Terraform

D. AzureRM

---

### Question 32

Can Terraform use multiple backends simultaneously?

A. Yes

B. No

---

### Question 33

Does:

```bash
terraform state rm
```

delete infrastructure?

A. Yes

B. No

---

### Question 34

Does:

```bash
terraform import
```

generate Terraform configuration files?

A. Yes

B. No

---

### Question 35

What does terraform import primarily modify?

A. Infrastructure

B. State

C. Providers

D. Modules

---

### Question 36

Can state files contain secrets?

A. Yes

B. No

---

### Question 37

Which command upgrades backend configuration after changes?

A. terraform fmt

B. terraform validate

C. terraform init

D. terraform graph

---

### Question 38

Which command is associated with stale lock removal?

A. terraform unlock

B. terraform force-unlock

C. terraform release-lock

D. terraform state unlock

---

### Question 39

What is the most important benefit of remote state?

A. Smaller Files

B. Team Collaboration

C. Faster Resources

D. Faster Providers

---

### Question 40

Which statement is TRUE?

A. Local backend is preferred for enterprise teams.

B. State locking prevents concurrent modifications.

C. terraform state rm destroys infrastructure.

D. terraform import creates Terraform code automatically.

---

# Domain 6 Coverage Matrix

| Objective                   | Questions                                       |
| --------------------------- | ----------------------------------------------- |
| 6a Local Backend            | 1,2,3,4,5,6,16,31                               |
| 6b State Locking            | 8,9,10,17,27,28,38,40                           |
| 6c Remote State             | 7,18,19,26,29,32,37,39                          |
| 6d Drift & State Management | 11,12,13,14,15,20,21,22,23,24,25,30,33,34,35,36 |

---

# Self-Assessment

### 35-40 Correct

Excellent. Domain 6 is exam-ready.

### 30-34 Correct

Strong understanding. Review missed explanations.

### 24-29 Correct

Good foundation. Revisit state commands and remote backends.

### Below 24 Correct

Review Domain 6 notes completely before moving forward.

---

# Domain Completion Checklist

- [ ] Read 6a - Local Backend
- [ ] Read 6b - State Locking
- [ ] Read 6c - Remote State
- [ ] Read 6d - Drift and State Management
- [ ] Completed Domain 6 Practice Questions
- [ ] Scored 35+/40
- [ ] Reviewed Incorrect Answers
- [ ] Ready for Domain 7
