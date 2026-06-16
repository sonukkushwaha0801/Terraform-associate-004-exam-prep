# MOCK EXAM 03

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

What is the primary purpose of Infrastructure as Code (IaC)?

A. To manage infrastructure through version-controlled configuration files

B. To replace cloud providers

C. To eliminate infrastructure teams

D. To store Terraform state

---

## Question 2

Which benefit is commonly associated with Infrastructure as Code?

A. Increased manual deployments

B. Reduced consistency

C. Repeatable infrastructure provisioning

D. Elimination of APIs

---

## Question 3

Terraform supports hybrid-cloud deployments primarily through:

A. Workspaces

B. Providers

C. Outputs

D. Variables

---

## Question 4

Which block configures how Terraform communicates with an API?

A. resource

B. variable

C. provider

D. output

---

## Question 5

What command initializes a Terraform working directory?

A. terraform apply

B. terraform plan

C. terraform validate

D. terraform init

---

## Question 6

What is downloaded during terraform init?

A. State files

B. Providers

C. Resources

D. Outputs

---

## Question 7

Which argument is used to constrain a provider version?

A. source

B. version

C. alias

D. backend

---

## Question 8

What is Terraform state primarily used for?

A. Storing provider binaries

B. Mapping resources to infrastructure

C. Formatting configuration files

D. Managing modules

---

## Question 9

Which file is commonly used for local state storage?

A. terraform.tfvars

B. terraform.lock.hcl

C. terraform.tfstate

D. variables.tf

---

## Question 10

What does terraform validate check?

A. Cloud resource health

B. Configuration validity

C. Provider installation

D. State locking

---

## Question 11

What is the purpose of terraform plan?

A. Create resources

B. Destroy resources

C. Preview proposed changes

D. Install providers

---

## Question 12

Which command applies infrastructure changes?

A. terraform fmt

B. terraform output

C. terraform validate

D. terraform apply

---

## Question 13

Which command removes Terraform-managed resources?

A. terraform destroy

B. terraform state rm

C. terraform plan

D. terraform show

---

## Question 14

What is the purpose of terraform fmt?

A. Validate configuration

B. Create resources

C. Format Terraform files

D. Manage state

---

## Question 15

Which Terraform block creates infrastructure?

A. provider

B. resource

C. data

D. output

---

## Question 16

What is the purpose of a data source?

A. Create infrastructure

B. Manage state

C. Read existing infrastructure

D. Configure providers

---

## Question 17

A Terraform configuration needs the ID of an existing subnet.

Which construct should be used?

A. resource

B. output

C. module

D. data

---

## Question 18

Which block defines an input value?

A. variable

B. output

C. provider

D. backend

---

## Question 19

What is the purpose of an output block?

A. Configure providers

B. Expose values from Terraform

C. Manage state

D. Create modules

---

## Question 20

Which type represents key-value pairs?

A. list

B. string

C. map

D. bool

---

## Question 21

Which Terraform type stores an ordered collection of values?

A. map

B. object

C. list

D. bool

---

## Question 22

Which Terraform type represents true or false values?

A. string

B. bool

C. list

D. map

---

## Question 23

Terraform automatically determines dependencies through:

A. Sentinel

B. Outputs

C. Resource references

D. Run Tasks

---

## Question 24

Which argument creates an explicit dependency?

A. source

B. version

C. provider

D. depends_on

---

## Question 25

Which function retrieves a value from a map?

A. concat()

B. length()

C. lookup()

D. merge()

---

## Question 26

Which function combines multiple maps?

A. merge()

B. lookup()

C. concat()

D. upper()

---

## Question 27

What is the purpose of custom variable validation?

A. Create resources

B. Validate user input

C. Configure providers

D. Configure backends

---

## Question 28

Which argument marks a variable or output as sensitive?

A. hidden = true

B. secret = true

C. encrypted = true

D. sensitive = true

---

## Question 29

What does sensitive = true do?

A. Encrypts values

B. Hides values from CLI output

C. Stores values in Vault

D. Removes values from state

---

## Question 30

What is the primary benefit of Terraform modules?

A. State locking

B. Encryption

C. Reusability

D. Provider installation

---

## Question 31

Which argument specifies where a module can be found?

A. source

B. backend

C. provider

D. output

---

## Question 32

Which location can Terraform use as a module source?

A. Terraform Registry

B. Git repository

C. Local path

D. All of the above

---

## Question 33

Why should module versions be constrained?

A. To reduce unexpected changes

B. To improve state locking

C. To create outputs

D. To create providers

---

## Question 34

How are values passed into modules?

A. Outputs

B. Variables

C. State

D. Providers

---

## Question 35

What is the primary purpose of a backend?

A. Store Terraform state

B. Install providers

C. Manage outputs

D. Configure modules

---

## Question 36

Which backend is used by default?

A. remote

B. s3

C. local

D. gcs

---

## Question 37

What is a major benefit of remote state?

A. Improved collaboration

B. Faster providers

C. More outputs

D. More modules

---

## Question 38

What problem does state locking help prevent?

A. Missing variables

B. Concurrent state updates

C. Provider version conflicts

D. Missing outputs

---

## Question 39

Infrastructure changes made outside Terraform are known as:

A. Validation

B. Initialization

C. Drift

D. Import

---

## Question 40

Which command is most commonly used to detect drift?

A. terraform output

B. terraform plan

C. terraform fmt

D. terraform validate

---
# MOCK EXAM 03

## Questions 41–57

---

## Question 41

What is the purpose of terraform import?

A. Create resources

B. Import provider plugins

C. Associate existing infrastructure with Terraform state

D. Create state locking

---

## Question 42

After importing a resource, what should typically be verified?

A. Provider source code

B. Configuration matches the imported resource

C. Module registry version

D. Terraform installation directory

---

## Question 43

Which command displays all resources tracked in state?

A. terraform state list

B. terraform state show

C. terraform output

D. terraform providers

---

## Question 44

Which command displays detailed information about a resource in state?

A. terraform show

B. terraform state rm

C. terraform state show

D. terraform state mv

---

## Question 45

Which environment variable enables Terraform logging?

A. TF_DEBUG

B. TF_PROVIDER

C. TF_STATE

D. TF_LOG

---

## Question 46

Which TF_LOG value is commonly used for troubleshooting?

A. SIMPLE

B. DEBUG

C. LOW

D. BASIC

---

## Question 47

What is the primary purpose of a workspace in HCP Terraform?

A. Store providers

B. Manage Terraform execution and state

C. Store modules

D. Replace organizations

---

## Question 48

What is the purpose of a project in HCP Terraform?

A. Group related workspaces

B. Store state files

C. Store providers

D. Replace workspaces

---

## Question 49

Which HCP Terraform feature provides Policy as Code?

A. Run Tasks

B. Projects

C. Sentinel

D. Registry

---

## Question 50

What can Sentinel policies enforce?

A. Governance and compliance requirements

B. Provider installation

C. Module creation

D. State storage

---

## Question 51

Which HCP Terraform feature allows integration with third-party systems during runs?

A. Outputs

B. Run Tasks

C. Variables

D. Providers

---

## Question 52

What is the purpose of a Private Module Registry?

A. Store state files

B. Host reusable modules

C. Manage providers

D. Execute plans

---

## Question 53

A company wants approved Terraform modules available to all teams.

Which feature should be used?

A. Sentinel

B. Run Tasks

C. State Locking

D. Private Module Registry

---

## Question 54

Which statement about Terraform workspaces is correct?

A. They provide isolated state instances

B. They install providers

C. They replace modules

D. They create resources

---

## Question 55

A team wants centralized state, remote execution, policy enforcement, and collaboration.

Which solution best fits these requirements?

A. Local Backend

B. HCP Terraform

C. terraform fmt

D. terraform import

---

## Question 56

Which statement about Terraform state is correct?

A. State is optional

B. State maps configuration to infrastructure

C. State replaces configuration files

D. State only exists in HCP Terraform

---

## Question 57

Which statement best describes Terraform?

A. Imperative infrastructure tool

B. Configuration management tool

C. Declarative Infrastructure as Code tool

D. Container orchestration platform

---

# Mock Exam 03 Completion

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
