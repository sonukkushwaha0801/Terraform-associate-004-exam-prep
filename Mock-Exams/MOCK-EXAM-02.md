# MOCK EXAM 02

> Terraform Associate (004)
>
> Questions: 57
>
> Time Recommendation: 60 Minutes
>
> Passing Target: 48+/57
>
> Instructions:
>
> * Choose the best answer.
> * Each question has one correct answer.
> * Do not use documentation.
> * Simulate real exam conditions.

---

## Question 1

Which statement best describes Infrastructure as Code (IaC)?

A. Infrastructure is configured manually through cloud consoles

B. Infrastructure is managed through version-controlled configuration files

C. Infrastructure is managed through spreadsheets

D. Infrastructure requires no documentation

---

## Question 2

What is a primary advantage of using Infrastructure as Code?

A. Increased manual configuration

B. Reduced automation

C. Consistent infrastructure deployments

D. Elimination of APIs

---

## Question 3

Terraform is considered service-agnostic because:

A. It only supports AWS

B. It only supports Azure

C. It can interact with many platforms through providers

D. It requires separate installations for each cloud

---

## Question 4

What is a Terraform provider?

A. A state file

B. A plugin that interacts with APIs

C. A module

D. A backend

---

## Question 5

Where are required providers typically declared?

A. backend block

B. output block

C. terraform block

D. variable block

---

## Question 6

Which command downloads required provider plugins?

A. terraform apply

B. terraform init

C. terraform validate

D. terraform destroy

---

## Question 7

What is the purpose of a provider alias?

A. Encrypt state

B. Create outputs

C. Configure multiple instances of a provider

D. Create modules

---

## Question 8

Which Terraform component tracks managed infrastructure?

A. Variables

B. Outputs

C. State

D. Providers

---

## Question 9

What information is stored in Terraform state?

A. Provider documentation

B. Infrastructure mappings and metadata

C. Cloud provider source code

D. Terraform binaries

---

## Question 10

Which statement about state is correct?

A. Terraform can function without state

B. State is optional for managed resources

C. State maps configuration to infrastructure

D. State only exists in HCP Terraform

---

## Question 11

What is the typical Terraform workflow order?

A. plan → init → apply

B. init → validate → plan → apply

C. apply → plan → destroy

D. validate → init → apply

---

## Question 12

What does terraform validate check?

A. Cloud infrastructure health

B. State locking

C. Configuration validity

D. Provider installation

---

## Question 13

What does terraform plan generate?

A. State file

B. Execution plan

C. Provider plugin

D. Module registry

---

## Question 14

Which command actually modifies infrastructure?

A. terraform plan

B. terraform validate

C. terraform fmt

D. terraform apply

---

## Question 15

What is the primary purpose of terraform destroy?

A. Remove Terraform-managed infrastructure

B. Remove provider plugins

C. Delete Terraform code

D. Remove variables

---

## Question 16

Which command standardizes Terraform file formatting?

A. terraform output

B. terraform state list

C. terraform fmt

D. terraform show

---

## Question 17

Which block creates and manages infrastructure?

A. data

B. resource

C. provider

D. terraform

---

## Question 18

What is the primary purpose of a data source?

A. Create resources

B. Read existing infrastructure information

C. Manage state

D. Configure modules

---

## Question 19

Which statement is true?

A. Data blocks create infrastructure

B. Resource blocks read existing infrastructure only

C. Data blocks retrieve information from existing infrastructure

D. Resources and data blocks are identical

---

## Question 20

A team needs the ID of an existing VPC.

Which Terraform construct should they use?

A. output

B. module

C. data source

D. backend

---

## Question 21

What is a Terraform variable used for?

A. Managing state

B. Providing input values

C. Installing providers

D. Creating modules

---

## Question 22

What is the purpose of an output block?

A. Return values from a configuration

B. Configure state

C. Install providers

D. Create resources

---

## Question 23

Which type stores ordered values?

A. string

B. bool

C. list

D. map

---

## Question 24

Which type stores key-value pairs?

A. object

B. map

C. list

D. tuple

---

## Question 25

Terraform automatically creates dependencies through:

A. Sentinel

B. Run Tasks

C. Resource references

D. Outputs

---

## Question 26

When should depends_on typically be used?

A. For every resource

B. When Terraform cannot infer a dependency

C. To create variables

D. To install providers

---

## Question 27

Which function combines two maps?

A. concat()

B. lookup()

C. merge()

D. length()

---

## Question 28

Which function returns a value from a map?

A. lookup()

B. upper()

C. lower()

D. concat()

---

## Question 29

What is the purpose of custom variable validation?

A. Enforce input requirements

B. Create state files

C. Install providers

D. Create outputs

---

## Question 30

What does sensitive = true do?

A. Encrypts state

B. Encrypts variables

C. Hides values from CLI output

D. Stores secrets in Vault

---

## Question 31

Why are Terraform modules used?

A. To increase duplication

B. To improve reuse

C. To replace providers

D. To replace state

---

## Question 32

Which argument specifies a module location?

A. source

B. provider

C. backend

D. output

---

## Question 33

Which is a valid Terraform module source?

A. Local path

B. Git repository

C. Terraform Registry

D. All of the above

---

## Question 34

Why should production modules use version constraints?

A. To avoid unexpected changes

B. To create outputs

C. To create providers

D. To manage state locking

---

## Question 35

How are values supplied to a module?

A. Through outputs

B. Through variables

C. Through state

D. Through providers

---

## Question 36

What is the purpose of a backend?

A. Manage variables

B. Manage state storage

C. Manage providers

D. Manage modules

---

## Question 37

Which backend is used if none is configured?

A. remote

B. s3

C. local

D. gcs

---

## Question 38

What benefit does remote state provide?

A. Easier collaboration

B. Faster providers

C. More resources

D. Automatic encryption

---

## Question 39

What problem does state locking solve?

A. Missing variables

B. Concurrent state modifications

C. Missing providers

D. Module versioning

---

## Question 40

What is resource drift?

A. State deletion

B. Provider upgrade

C. Infrastructure changes outside Terraform

D. Module version mismatch

---

## Question 41

Which command is most commonly used to identify drift?

A. terraform plan

B. terraform fmt

C. terraform output

D. terraform init

---

## Question 42

What does terraform import primarily update?

A. Configuration files

B. State

C. Providers

D. Outputs

---

## Question 43

Which statement about terraform import is correct?

A. It generates complete Terraform code

B. It imports provider plugins

C. It associates existing resources with state

D. It creates state locking

---

## Question 44

Which command lists resources in state?

A. terraform state list

B. terraform state show

C. terraform show

D. terraform output

---

## Question 45

Which command displays detailed information about a state resource?

A. terraform state rm

B. terraform state mv

C. terraform state show

D. terraform validate

---

## Question 46

What environment variable enables Terraform logging?

A. TF_STATE

B. TF_PROVIDER

C. TF_LOG

D. TF_DEBUGGER

---

## Question 47

Which TF_LOG level is commonly used for troubleshooting?

A. SIMPLE

B. DEBUG

C. LOW

D. BASIC

---

## Question 48

Which HCP Terraform component is the primary execution environment?

A. Project

B. Workspace

C. Organization

D. Registry

---

## Question 49

What is the primary purpose of a project?

A. Group related workspaces

B. Store providers

C. Replace organizations

D. Store state locally

---

## Question 50

Which HCP Terraform feature supports remote state management?

A. Workspaces

B. Outputs

C. Variables

D. Providers

---

## Question 51

Which HCP Terraform feature provides Policy as Code?

A. Run Tasks

B. Sentinel

C. Projects

D. Variables

---

## Question 52

What can Sentinel policies enforce?

A. Governance requirements

B. Provider installation

C. Module creation

D. State storage

---

## Question 53

What is the purpose of Run Tasks?

A. Replace workspaces

B. Integrate external systems

C. Store state

D. Manage variables

---

## Question 54

What is stored in a Private Module Registry?

A. State files

B. Variables

C. Reusable modules

D. Providers

---

## Question 55

A company wants centrally approved modules available to all teams.

Which feature should be used?

A. Sentinel

B. Run Tasks

C. Private Module Registry

D. State Locking

---

## Question 56

Which statement about workspaces is correct?

A. They install providers

B. They create modules

C. They provide isolated state

D. They replace projects

---

## Question 57

Which HCP Terraform capability improves collaboration among teams?

A. Remote execution and shared workspaces

B. Local state files

C. Manual deployments

D. Provider aliases

---

# Mock Exam 02 Completion

## Scoring Sheet

```text
Correct Answers = _____ / 57
```

---

## Readiness Assessment

| Score | Assessment         |
| ----- | ------------------ |
| 0–30  | Needs More Study   |
| 31–40 | Developing         |
| 41–47 | Near Exam Ready    |
| 48–52 | Exam Ready         |
| 53–57 | Strong Pass Likely |

---
