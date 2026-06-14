# Domain 8 Practice Questions

## HCP Terraform

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

✅ Complete all questions before reviewing answers.

✅ Passing Target: 35+/40

---

# Conceptual Questions

### Question 1

What is HCP Terraform?

A. Cloud Provider

B. Managed Terraform Platform

C. Kubernetes Distribution

D. Configuration Language

---

### Question 2

What is the primary benefit of HCP Terraform?

A. Faster Internet

B. Centralized Terraform Operations

C. More Terraform Resources

D. Additional Providers

---

### Question 3

Where is Terraform state typically stored in HCP Terraform?

A. Local Machine

B. GitHub

C. Workspace

D. Variable Set

---

### Question 4

What is a Terraform Run?

A. Provider Configuration

B. Terraform Operation

C. Variable Set

D. Backend

---

### Question 5

What are the two primary phases of a Terraform Run?

A. Init and Validate

B. Plan and Apply

C. Create and Destroy

D. Login and Apply

---

### Question 6

What feature controls user permissions in HCP Terraform?

A. Sentinel

B. Variable Sets

C. RBAC

D. Projects

---

### Question 7

What is Sentinel?

A. State Backend

B. Policy-as-Code Framework

C. Workspace Type

D. Module Registry

---

### Question 8

What feature records user actions?

A. Audit Trails

B. Variable Sets

C. Outputs

D. Run Triggers

---

### Question 9

What is a Variable Set?

A. Shared Variables Across Workspaces

B. Shared State

C. Shared Providers

D. Shared Outputs

---

### Question 10

What does Drift Detection identify?

A. Provider Changes

B. Infrastructure Drift

C. Module Changes

D. Variable Changes

---

### Question 11

What is the primary operational unit in HCP Terraform?

A. Project

B. Team

C. Workspace

D. Variable Set

---

### Question 12

What is a Project?

A. Collection of Providers

B. Collection of Workspaces

C. Collection of Variables

D. Collection of Outputs

---

### Question 13

What command authenticates Terraform CLI with HCP Terraform?

A. terraform auth

B. terraform login

C. terraform connect

D. terraform cloud

---

### Question 14

Which block connects Terraform to HCP Terraform?

A. provider

B. backend

C. cloud

D. resource

---

### Question 15

Which workflow is most common in enterprise environments?

A. Manual

B. CLI-Driven

C. VCS-Driven

D. Local

---

# Scenario-Based Questions

### Question 16

A company wants centralized Terraform execution instead of running Terraform from engineer laptops.

Which HCP Terraform capability addresses this?

A. Variable Sets

B. Remote Execution

C. Outputs

D. Modules

---

### Question 17

An organization wants all Terraform state centrally managed.

Which HCP Terraform feature provides this?

A. Projects

B. Workspaces

C. Remote State Storage

D. Outputs

---

### Question 18

A company wants infrastructure changes automatically triggered after GitHub commits.

Which workflow should be used?

A. CLI-Driven

B. Manual

C. VCS-Driven

D. Local

---

### Question 19

A security team wants to block public S3 buckets from being created.

Which feature should be implemented?

A. Variable Sets

B. Sentinel Policies

C. Outputs

D. Run Triggers

---

### Question 20

A company wants developers to view workspaces but not apply infrastructure changes.

Which feature should be used?

A. RBAC

B. Outputs

C. Variable Sets

D. Run Triggers

---

### Question 21

An engineer wants to determine who approved a production deployment.

Which feature provides this information?

A. Outputs

B. Audit Trails

C. Workspaces

D. Projects

---

### Question 22

A company wants one AWS region variable shared across 20 workspaces.

Which feature should be used?

A. Outputs

B. Variable Sets

C. Workspaces

D. Run Triggers

---

### Question 23

A company organizes infrastructure into:

```text
network-prod
app-prod
db-prod
```

under a single grouping.

What HCP Terraform feature is being used?

A. Variable Set

B. Project

C. Policy Set

D. Team

---

### Question 24

A workspace finishes applying network infrastructure.

Another workspace should automatically begin deployment.

Which feature should be used?

A. Outputs

B. Run Triggers

C. Audit Trails

D. Variable Sets

---

### Question 25

An organization wants to estimate infrastructure cost before approval.

Which HCP Terraform feature should be used?

A. Cost Estimation

B. Drift Detection

C. Outputs

D. Run Triggers

---

### Question 26

A company wants reusable approved Terraform modules.

Which feature should be used?

A. Private Module Registry

B. Variable Sets

C. Outputs

D. Audit Trails

---

### Question 27

A company migrates from local state to HCP Terraform.

Which command commonly performs the migration?

A. terraform apply

B. terraform init

C. terraform validate

D. terraform graph

---

### Question 28

A team wants Terraform runs executed remotely.

Which HCP Terraform feature enables this?

A. Remote Execution

B. Outputs

C. Variable Sets

D. Run Triggers

---

### Question 29

An engineer wants detailed workspace state, variables, and run history.

Which HCP Terraform component contains all of these?

A. Project

B. Workspace

C. Team

D. Policy Set

---

### Question 30

A company uses GitHub webhooks to trigger Terraform plans.

What workflow is being used?

A. Local

B. CLI-Driven

C. VCS-Driven

D. Manual

---

# HashiCorp Exam-Trap Questions

### Question 31

Are HCP Terraform Workspaces and Terraform CLI Workspaces the same thing?

A. Yes

B. No

---

### Question 32

What stores Terraform state in HCP Terraform?

A. Project

B. Workspace

C. Team

D. Variable Set

---

### Question 33

Can Sentinel policies block an apply operation?

A. Yes

B. No

---

### Question 34

What does terraform login do?

A. Creates Workspace

B. Authenticates Terraform CLI

C. Creates State

D. Installs Providers

---

### Question 35

What block connects Terraform configurations to HCP Terraform?

A. backend

B. resource

C. cloud

D. provider

---

### Question 36

Which workflow automatically starts runs after Git commits?

A. CLI-Driven

B. Manual

C. VCS-Driven

D. Workspace-Driven

---

### Question 37

Can Variable Sets be shared across multiple workspaces?

A. Yes

B. No

---

### Question 38

What is the primary purpose of Projects?

A. Execute Runs

B. Store State

C. Organize Workspaces

D. Store Outputs

---

### Question 39

What command is commonly used after adding a cloud block?

A. terraform fmt

B. terraform graph

C. terraform init

D. terraform show

---

### Question 40

Which statement is TRUE?

A. Sentinel is used for authentication.

B. Projects store Terraform state.

C. Workspaces contain state, variables, and runs.

D. Variable Sets store Terraform code.

---

# Domain 8 Coverage Matrix

| Objective                     | Questions                          |
| ----------------------------- | ---------------------------------- |
| 8a Create Infrastructure      | 1,2,3,4,5,16,17,18,27,28,30        |
| 8b Collaboration & Governance | 6,7,8,9,10,19,20,21,22,25,26,33,37 |
| 8c Workspaces & Projects      | 11,12,23,24,29,31,32,38,40         |
| 8d Integration                | 13,14,15,27,30,34,35,36,39         |

---

# Self-Assessment

### 35-40 Correct

Excellent. Domain 8 is exam-ready.

### 30-34 Correct

Strong understanding. Review missed explanations.

### 24-29 Correct

Good foundation. Review Workspaces, Projects, and Integrations.

### Below 24 Correct

Re-read Domain 8 notes before moving forward.

---

# Domain Completion Checklist

- [ ] Read 8a - Use HCP Terraform to Create Infrastructure
- [ ] Read 8b - Collaboration and Governance Features
- [ ] Read 8c - Workspaces and Projects
- [ ] Read 8d - HCP Terraform Integration
- [ ] Completed Practice Questions
- [ ] Scored 35+/40
- [ ] Reviewed Incorrect Answers
- [ ] Terraform Associate (004) Exam Ready
