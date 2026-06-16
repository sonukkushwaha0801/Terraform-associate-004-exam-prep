# MOCK EXAM 01

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
> * Do not use Terraform documentation.
> * Simulate real exam conditions.

---

## Question 1

What is the primary purpose of Infrastructure as Code (IaC)?

A. To manually configure infrastructure through cloud consoles

B. To manage infrastructure using version-controlled configuration files

C. To replace cloud providers

D. To eliminate the need for infrastructure

---

## Question 2

Which benefit is commonly associated with Infrastructure as Code?

A. Increased manual configuration

B. Reduced consistency across environments

C. Repeatable infrastructure deployments

D. Elimination of state management

---

## Question 3

How does Terraform support multi-cloud deployments?

A. By requiring separate Terraform installations

B. Through provider plugins for different platforms

C. Through operating system virtualization

D. By storing resources in a shared state file

---

## Question 4

Which block is used to configure a provider?

A. module

B. resource

C. provider

D. variable

---

## Question 5

What command initializes a Terraform working directory?

A. terraform apply

B. terraform validate

C. terraform init

D. terraform plan

---

## Question 6

During terraform init, which action occurs?

A. Infrastructure is created

B. Providers are downloaded

C. State is destroyed

D. Resources are imported

---

## Question 7

Which argument is commonly used to constrain provider versions?

A. source

B. backend

C. required_version

D. version

---

## Question 8

A Terraform configuration uses resources from AWS and Azure.

What Terraform feature makes this possible?

A. Workspaces

B. Providers

C. Outputs

D. Variables

---

## Question 9

What is the purpose of Terraform state?

A. To store provider binaries

B. To store Terraform documentation

C. To map resources to real infrastructure

D. To replace configuration files

---

## Question 10

Which file typically stores Terraform state when using the local backend?

A. terraform.lock.hcl

B. terraform.tfvars

C. terraform.tfstate

D. variables.tf

---

## Question 11

Which command checks whether Terraform configuration is syntactically valid?

A. terraform plan

B. terraform validate

C. terraform apply

D. terraform output

---

## Question 12

What does terraform plan do?

A. Creates infrastructure

B. Destroys infrastructure

C. Displays proposed changes

D. Imports resources

---

## Question 13

A team wants to review changes before infrastructure is modified.

Which command should they use?

A. terraform apply

B. terraform destroy

C. terraform init

D. terraform plan

---

## Question 14

Which command applies proposed infrastructure changes?

A. terraform validate

B. terraform apply

C. terraform output

D. terraform fmt

---

## Question 15

What is the purpose of terraform fmt?

A. Create resources

B. Validate syntax

C. Format configuration files

D. Import infrastructure

---

## Question 16

Which command removes Terraform-managed infrastructure?

A. terraform destroy

B. terraform state rm

C. terraform validate

D. terraform output

---

## Question 17

What is a Terraform resource?

A. A plugin used to communicate with APIs

B. A managed infrastructure object

C. A state file entry

D. A backend configuration

---

## Question 18

What is the purpose of a Terraform data source?

A. Create infrastructure

B. Destroy infrastructure

C. Read existing infrastructure information

D. Manage state locking

---

## Question 19

Which statement correctly describes a data block?

A. It creates infrastructure resources

B. It reads existing infrastructure

C. It configures providers

D. It stores state

---

## Question 20

A Terraform configuration needs information about an existing VPC.

Which construct should be used?

A. resource block

B. backend block

C. data block

D. output block

---

## Question 21

Which block is used to define input values for a Terraform configuration?

A. output

B. provider

C. variable

D. backend

---

## Question 22

What is the purpose of an output value?

A. Store provider credentials

B. Return information from Terraform configuration

C. Configure state locking

D. Install providers

---

## Question 23

Which Terraform type represents a collection of values identified by keys?

A. string

B. list

C. bool

D. map

---

## Question 24

Which expression creates an explicit dependency?

A. resource reference

B. depends_on

C. variable

D. output

---

## Question 25

Terraform automatically determines resource ordering using:

A. Sentinel

B. Run Tasks

C. Resource references

D. HCP Projects

---

## Question 26

Which function returns the number of elements in a collection?

A. lookup()

B. merge()

C. concat()

D. length()

---

## Question 27

What does the lookup() function return?

A. Resource ID

B. Value from a map

C. Provider version

D. Backend type

---

## Question 28

What is the purpose of validation blocks in variables?

A. Create resources

B. Validate user-provided values

C. Configure providers

D. Lock state files

---

## Question 29

Which argument marks an output as sensitive?

A. encrypted = true

B. hidden = true

C. sensitive = true

D. protected = true

---

## Question 30

What does sensitive = true primarily do?

A. Encrypts values

B. Hides values from CLI output

C. Removes values from state

D. Stores values in Vault

---

## Question 31

What is the primary benefit of Terraform modules?

A. State locking

B. Resource encryption

C. Reusability

D. Provider installation

---

## Question 32

Which argument specifies where Terraform should obtain a module?

A. provider

B. source

C. backend

D. output

---

## Question 33

Which source can Terraform use for modules?

A. Terraform Registry

B. Git repository

C. Local path

D. All of the above

---

## Question 34

Why should module versions be constrained?

A. To avoid unexpected changes

B. To enable state locking

C. To encrypt outputs

D. To create providers

---

## Question 35

How are values passed into a module?

A. Through outputs

B. Through variables

C. Through state

D. Through backends

---

## Question 36

What is a backend used for?

A. Managing providers

B. Managing state storage

C. Managing variables

D. Managing outputs

---

## Question 37

Which backend is used by default?

A. remote

B. s3

C. local

D. gcs

---

## Question 38

What is the primary advantage of remote state?

A. Faster provider downloads

B. Team collaboration

C. Automatic module creation

D. Reduced resource count

---

## Question 39

Why is state locking important?

A. Prevents concurrent state modification

B. Encrypts state

C. Creates backups

D. Installs providers

---

## Question 40

A user manually modifies infrastructure outside Terraform.

What has occurred?

A. Import

B. Drift

C. Validation

D. Initialization

---

## Question 41

Which command is commonly used to detect infrastructure drift?

A. terraform output

B. terraform fmt

C. terraform plan

D. terraform init

---

## Question 42

What is the purpose of the terraform import command?

A. Generate Terraform configuration automatically

B. Bring existing infrastructure under Terraform management

C. Create a new provider

D. Initialize a backend

---

## Question 43

After importing a resource, what should typically be done next?

A. Run terraform destroy

B. Remove the resource from state

C. Verify configuration matches the imported resource

D. Reinstall Terraform

---

## Question 44

Which command displays resources currently tracked in Terraform state?

A. terraform state list

B. terraform output

C. terraform validate

D. terraform providers

---

## Question 45

Which command displays detailed information about a specific state resource?

A. terraform state mv

B. terraform state rm

C. terraform state show

D. terraform plan

---

## Question 46

You need detailed troubleshooting information during Terraform execution.

Which environment variable should be configured?

A. TF_VAR_DEBUG

B. TF_LOG

C. TF_PROVIDER_LOG

D. TF_STATE_LOG

---

## Question 47

Which TF_LOG value provides detailed debugging information?

A. OFF

B. BASIC

C. DEBUG

D. SIMPLE

---

## Question 48

Which HCP Terraform feature provides remote execution of Terraform runs?

A. State Locking

B. Workspaces

C. Variable Validation

D. Providers

---

## Question 49

In HCP Terraform, what is the purpose of a workspace?

A. Store provider plugins

B. Manage Terraform execution and state for a configuration

C. Store module source code

D. Replace projects

---

## Question 50

What is the primary purpose of a project in HCP Terraform?

A. Store state files

B. Group related workspaces

C. Replace organizations

D. Manage providers

---

## Question 51

Which HCP Terraform feature provides Policy as Code?

A. Run Tasks

B. Private Registry

C. Sentinel

D. Projects

---

## Question 52

What can Sentinel policies do?

A. Install providers

B. Enforce governance rules

C. Replace Terraform state

D. Generate modules

---

## Question 53

Which HCP Terraform feature allows integration with third-party tools during runs?

A. Run Tasks

B. Outputs

C. Variables

D. Providers

---

## Question 54

What is the purpose of a private module registry?

A. Store Terraform state

B. Host reusable modules

C. Execute Terraform plans

D. Manage workspaces

---

## Question 55

A team wants to share approved Terraform modules across the organization.

Which HCP Terraform feature best supports this requirement?

A. Run Tasks

B. Sentinel

C. Private Module Registry

D. State Locking

---

## Question 56

Which statement about Terraform workspaces is correct?

A. Workspaces create provider configurations

B. Workspaces provide separate state instances

C. Workspaces replace modules

D. Workspaces install providers

---

## Question 57

A team wants centralized state management, policy enforcement, remote execution, and collaboration features.

Which solution best meets these requirements?

A. Local Backend

B. Terraform Variables

C. HCP Terraform

D. Terraform Import

---

# Mock Exam 01 Completion

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

