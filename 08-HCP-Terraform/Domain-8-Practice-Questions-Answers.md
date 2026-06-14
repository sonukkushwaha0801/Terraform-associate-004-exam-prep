# Domain 8 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 4
- Total Questions: 40

---

# Objective Coverage

| Objective                                     | Questions                          |
| --------------------------------------------- | ---------------------------------- |
| 8a Use HCP Terraform to Create Infrastructure | 1,2,3,4,5,16,17,18,27,28,30        |
| 8b Collaboration and Governance               | 6,7,8,9,10,19,20,21,22,25,26,33,37 |
| 8c Workspaces and Projects                    | 11,12,23,24,29,31,32,38,40         |
| 8d Integrations                               | 13,14,15,27,30,34,35,36,39         |

---

# Answer Key

| Q   | Ans | Q   | Ans | Q   | Ans | Q   | Ans |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | B   | 11  | C   | 21  | B   | 31  | B   |
| 2   | B   | 12  | B   | 22  | B   | 32  | B   |
| 3   | C   | 13  | B   | 23  | B   | 33  | A   |
| 4   | B   | 14  | C   | 24  | B   | 34  | B   |
| 5   | B   | 15  | C   | 25  | A   | 35  | C   |
| 6   | C   | 16  | B   | 26  | A   | 36  | C   |
| 7   | B   | 17  | C   | 27  | B   | 37  | A   |
| 8   | A   | 18  | C   | 28  | A   | 38  | C   |
| 9   | A   | 19  | B   | 29  | B   | 39  | C   |
| 10  | B   | 20  | A   | 30  | C   | 40  | C   |

---

# Detailed Explanations

## Questions 1-5 (HCP Terraform Fundamentals)

### Q1

**Answer:** B

HCP Terraform is HashiCorp's managed platform for operating Terraform workflows.

It provides:

- Remote Execution
- Remote State
- Collaboration
- Governance

---

### Q2

**Answer:** B

The primary benefit is:

```text
Centralized Terraform Operations
```

rather than every engineer managing infrastructure independently.

---

### Q3

**Answer:** C

State is stored within:

```text
Workspace
```

in HCP Terraform.

---

### Q4

**Answer:** B

A Run is a Terraform operation such as:

```text
Plan
Apply
Destroy
```

---

### Q5

**Answer:** B

Every run consists primarily of:

```text
Plan
Apply
```

---

# Questions 6-10 (Governance Features)

### Q6

**Answer:** C

RBAC controls:

```text
Permissions
Access
Roles
```

---

### Q7

**Answer:** B

Sentinel is:

```text
Policy as Code
```

for governance enforcement.

---

### Q8

**Answer:** A

Audit Trails record:

- User Actions
- Run History
- Changes

---

### Q9

**Answer:** A

Variable Sets allow variables to be reused across multiple workspaces.

---

### Q10

**Answer:** B

Drift Detection identifies:

```text
Infrastructure Changes Outside Terraform
```

---

# Questions 11-15 (Workspaces and Integrations)

### Q11

**Answer:** C

Workspace is the primary operational unit.

---

### Q12

**Answer:** B

Projects organize multiple workspaces.

---

### Q13

**Answer:** B

Authenticate CLI:

```bash
terraform login
```

---

### Q14

**Answer:** C

Cloud block:

```hcl
cloud {}
```

connects Terraform to HCP Terraform.

---

### Q15

**Answer:** C

Most enterprise environments use:

```text
VCS-Driven Workflow
```

---

# Questions 16-20 (Scenario-Based)

### Q16

**Answer:** B

Remote Execution allows Terraform runs to occur in HCP Terraform.

---

### Q17

**Answer:** C

Remote State Storage centralizes state.

---

### Q18

**Answer:** C

Git commits automatically triggering runs:

```text
VCS-Driven Workflow
```

---

### Q19

**Answer:** B

Preventing public S3 buckets:

```text
Sentinel Policy
```

---

### Q20

**Answer:** A

RBAC provides:

```text
View Only
Read
Write
Admin
```

permissions.

---

# Questions 21-30

### Q21

**Answer:** B

Audit Trails show:

```text
Who Approved
Who Changed
When It Happened
```

---

### Q22

**Answer:** B

Shared variables:

```text
Variable Sets
```

---

### Q23

**Answer:** B

Grouping multiple workspaces:

```text
Project
```

---

### Q24

**Answer:** B

Automatic workspace execution:

```text
Run Triggers
```

---

### Q25

**Answer:** A

Cost Estimation predicts costs before deployment.

---

### Q26

**Answer:** A

Reusable approved modules belong in:

```text
Private Module Registry
```

---

### Q27

**Answer:** B

State migration typically occurs during:

```bash
terraform init
```

---

### Q28

**Answer:** A

Remote execution executes runs inside HCP Terraform.

---

### Q29

**Answer:** B

Workspace contains:

- State
- Variables
- Outputs
- Runs

---

### Q30

**Answer:** C

GitHub-triggered plans are:

```text
VCS-Driven
```

---

# Questions 31-40 (Exam Traps)

### Q31

**Answer:** B

HCP Workspaces and CLI Workspaces are NOT the same.

---

### Q32

**Answer:** B

Workspace stores Terraform state.

---

### Q33

**Answer:** A

Sentinel policies can block applies.

---

### Q34

**Answer:** B

terraform login authenticates Terraform CLI.

---

### Q35

**Answer:** C

Cloud block:

```hcl
cloud {}
```

---

### Q36

**Answer:** C

Git-triggered workflow:

```text
VCS-Driven
```

---

### Q37

**Answer:** A

Variable Sets can be attached to multiple workspaces.

---

### Q38

**Answer:** C

Projects organize workspaces.

---

### Q39

**Answer:** C

After adding cloud block:

```bash
terraform init
```

---

### Q40

**Answer:** C

Workspace contains:

- State
- Variables
- Runs
- Outputs

---

# HCP Terraform Feature Comparison

| Feature         | Purpose              |
| --------------- | -------------------- |
| Workspace       | Operational Unit     |
| Project         | Organizational Unit  |
| Variable Set    | Shared Variables     |
| Sentinel        | Policy Enforcement   |
| Audit Trail     | Activity Tracking    |
| Team            | User Group           |
| Run Trigger     | Workspace Automation |
| Cost Estimation | Cost Visibility      |
| Drift Detection | Drift Monitoring     |

---

# Workspace vs Project

| Workspace        | Project               |
| ---------------- | --------------------- |
| Stores State     | Contains Workspaces   |
| Executes Runs    | Organizes Workspaces  |
| Stores Variables | Groups Infrastructure |
| Operational Unit | Organizational Unit   |

---

# HCP Workspace vs CLI Workspace

| HCP Workspace      | CLI Workspace           |
| ------------------ | ----------------------- |
| Cloud Resource     | Local Terraform Feature |
| Stores State       | State Separation        |
| Supports Runs      | No Runs                 |
| Team Collaboration | Local Usage             |
| HCP Feature        | CLI Feature             |

---

# Top 20 Domain 8 Exam Traps

### 1

HCP Terraform is a managed Terraform platform.

### 2

Runs execute remotely.

### 3

State stored in Workspaces.

### 4

Workspace = Operational Unit.

### 5

Project = Organizational Unit.

### 6

Projects contain Workspaces.

### 7

Sentinel = Policy as Code.

### 8

RBAC controls permissions.

### 9

Audit Trails track actions.

### 10

Variable Sets share variables.

### 11

Run Triggers automate workspace dependencies.

### 12

Drift Detection identifies infrastructure drift.

### 13

Cost Estimation predicts deployment costs.

### 14

Private Registry stores reusable modules.

### 15

terraform login authenticates CLI.

### 16

cloud block connects Terraform to HCP Terraform.

### 17

terraform init performs state migration.

### 18

VCS-Driven Workflow is most common.

### 19

HCP Workspaces ≠ CLI Workspaces.

### 20

Policies can block applies.

---

# 5-Minute Domain 8 Revision

```text
HCP Terraform
=
Managed Terraform Platform
```

---

```text
Workspace
=
State + Variables + Runs
```

---

```text
Project
=
Collection Of Workspaces
```

---

```text
Sentinel
=
Policy As Code
```

---

```text
RBAC
=
Permissions
```

---

```text
Audit Trail
=
Who Did What
```

---

```text
Variable Set
=
Shared Variables
```

---

```text
Run Trigger
=
Automatic Workspace Run
```

---

```text
terraform login
```

↓

```text
Authenticate CLI
```

---

```hcl
cloud {}
```

↓

```text
Connect To HCP Terraform
```

---

```bash
terraform init
```

↓

```text
State Migration
```

---

```text
VCS Driven
```

↓

```text
Most Common Enterprise Workflow
```

---

# Exam Readiness Score

### 35-40 Correct

Domain 8 Exam Ready

### 30-34 Correct

Strong Understanding

### 24-29 Correct

Review Workspaces and Integrations

### Below 24 Correct

Re-read Domain 8 Theory And Retake Questions
