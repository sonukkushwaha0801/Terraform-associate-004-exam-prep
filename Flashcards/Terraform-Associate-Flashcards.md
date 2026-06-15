# Terraform Associate Flashcards

> Terraform Associate (004) Certification Flashcards
>
> Purpose:
> Rapid revision of all Terraform Associate exam objectives.
>
> Usage:
>
> * Read Question → Answer
> * Review daily during exam preparation
> * Focus on weak domains during revision
> * Use for last-minute exam review

---

# Domain 1 — Infrastructure as Code (IaC)

### Flashcard 1

**Q:** What is Infrastructure as Code (IaC)?

**A:** Managing and provisioning infrastructure through machine-readable configuration files instead of manual processes.

---

### Flashcard 2

**Q:** What Terraform file extension is commonly used?

**A:** `.tf`

---

### Flashcard 3

**Q:** What problem does IaC solve?

**A:** Manual configuration drift and inconsistent environments.

---

### Flashcard 4

**Q:** Name four benefits of IaC.

**A:**

* Consistency
* Automation
* Version Control
* Repeatability

---

### Flashcard 5

**Q:** What is configuration drift?

**A:** When actual infrastructure differs from declared configuration.

---

### Flashcard 6

**Q:** Why is Terraform considered declarative?

**A:** Users define desired state rather than procedural steps.

---

### Flashcard 7

**Q:** What does service-agnostic mean?

**A:** Terraform can manage many platforms using a common workflow.

---

### Flashcard 8

**Q:** What enables Terraform multi-cloud deployments?

**A:** Providers.

---

### Flashcard 9

**Q:** Give an example of hybrid cloud.

**A:** AWS infrastructure integrated with on-premises VMware resources.

---

### Flashcard 10

**Q:** What is Terraform's desired state model?

**A:** Infrastructure is continuously compared against declared configuration and state.

---

# Domain 2 — Terraform Fundamentals

### Flashcard 11

**Q:** What is a provider?

**A:** Plugin that enables Terraform to interact with external APIs.

---

### Flashcard 12

**Q:** Where are provider requirements defined?

**A:** `terraform` block.

---

### Flashcard 13

**Q:** Which command downloads providers?

**A:** `terraform init`

---

### Flashcard 14

**Q:** Why should provider versions be pinned?

**A:** To ensure reproducible deployments.

---

### Flashcard 15

**Q:** What is a provider source address?

**A:** Provider namespace and name location.

Example:

```hcl
hashicorp/aws
```

---

### Flashcard 16

**Q:** What is an alias provider?

**A:** Multiple configurations of the same provider.

---

### Flashcard 17

**Q:** Why use provider aliases?

**A:** Multi-region or multi-account deployments.

---

### Flashcard 18

**Q:** What file records provider versions?

**A:** `.terraform.lock.hcl`

---

### Flashcard 19

**Q:** What is Terraform State?

**A:** Metadata file tracking managed resources.

---

### Flashcard 20

**Q:** Default Terraform state filename?

**A:** `terraform.tfstate`

---

# Domain 3 — Core Terraform Workflow

### Flashcard 21

**Q:** Standard Terraform workflow?

**A:**

1. Write
2. Init
3. Validate
4. Plan
5. Apply

---

### Flashcard 22

**Q:** What does `terraform init` do?

**A:** Initializes working directory and downloads dependencies.

---

### Flashcard 23

**Q:** What does `terraform validate` do?

**A:** Checks configuration syntax and validity.

---

### Flashcard 24

**Q:** What does `terraform fmt` do?

**A:** Automatically formats Terraform code.

---

### Flashcard 25

**Q:** What does `terraform plan` produce?

**A:** Execution plan showing proposed changes.

---

### Flashcard 26

**Q:** What symbols appear in a plan?

**A:**

* `+` Create
* `~` Modify
* `-` Destroy

---

### Flashcard 27

**Q:** What does `terraform apply` do?

**A:** Executes planned infrastructure changes.

---

### Flashcard 28

**Q:** What does `terraform destroy` do?

**A:** Removes managed infrastructure.

---

### Flashcard 29

**Q:** What command generates a saved execution plan?

**A:**

```bash
terraform plan -out=tfplan
```

---

### Flashcard 30

**Q:** Why review plans before apply?

**A:** Detect unintended infrastructure changes.

---

# Domain 4 — Terraform Configuration

### Flashcard 31

**Q:** What is a resource block?

**A:** Creates or manages infrastructure objects.

---

### Flashcard 32

**Q:** What is a data block?

**A:** Reads existing infrastructure information.

---

### Flashcard 33

**Q:** Resource vs Data Source?

**A:**

* Resource → Create/Manage
* Data Source → Read Only

---

### Flashcard 34

**Q:** What are input variables used for?

**A:** Parameterizing configurations.

---

### Flashcard 35

**Q:** What are outputs used for?

**A:** Exposing values after deployment.

---

### Flashcard 36

**Q:** What are Terraform primitive types?

**A:**

* string
* number
* bool

---

### Flashcard 37

**Q:** What are Terraform collection types?

**A:**

* list
* map
* set

---

### Flashcard 38

**Q:** What are Terraform structural types?

**A:**

* object
* tuple

---

### Flashcard 39

**Q:** What does `count` do?

**A:** Creates multiple instances of a resource.

---

### Flashcard 40

**Q:** What is `for_each`?

**A:** Creates resources from maps or sets.

---

### Flashcard 41

**Q:** Difference between count and for_each?

**A:**

* count → Index-based
* for_each → Key-based

---

### Flashcard 42

**Q:** What is an implicit dependency?

**A:** Created through attribute references.

---

### Flashcard 43

**Q:** What is explicit dependency?

**A:** Defined using `depends_on`.

---

### Flashcard 44

**Q:** What is variable validation?

**A:** Custom rules enforcing valid input values.

---

### Flashcard 45

**Q:** What is a sensitive variable?

**A:** Variable hidden from Terraform output.

---

### Flashcard 46

**Q:** Does sensitive prevent state storage?

**A:** No.

---

### Flashcard 47

**Q:** Why integrate Vault with Terraform?

**A:** Secure secret retrieval and management.

---

# Domain 5 — Terraform Modules

### Flashcard 48

**Q:** What is a Terraform module?

**A:** Reusable collection of Terraform resources.

---

### Flashcard 49

**Q:** What is the root module?

**A:** Main working directory configuration.

---

### Flashcard 50

**Q:** What is a child module?

**A:** Module called from another module.

---

### Flashcard 51

**Q:** Where can modules be sourced from?

**A:**

* Local paths
* Git repositories
* Terraform Registry

---

### Flashcard 52

**Q:** Why use modules?

**A:**

* Reusability
* Standardization
* Maintainability

---

### Flashcard 53

**Q:** How are module versions controlled?

**A:** Version constraints.

---

### Flashcard 54

**Q:** Can child modules access parent variables directly?

**A:** No.

---

### Flashcard 55

**Q:** How do modules expose values?

**A:** Outputs.

---

# Domain 6 — Terraform State Management

### Flashcard 56

**Q:** What is the Local Backend?

**A:** State stored on local filesystem.

---

### Flashcard 57

**Q:** Why is local state risky?

**A:** Poor collaboration and recovery.

---

### Flashcard 58

**Q:** What is state locking?

**A:** Prevents concurrent state modifications.

---

### Flashcard 59

**Q:** Why is state locking important?

**A:** Prevents state corruption.

---

### Flashcard 60

**Q:** What is a remote backend?

**A:** State stored in shared remote storage.

---

### Flashcard 61

**Q:** Common remote backend example?

**A:** AWS S3.

---

### Flashcard 62

**Q:** What command refreshes state during planning?

**A:** `terraform plan`

---

### Flashcard 63

**Q:** What is resource drift?

**A:** Infrastructure changed outside Terraform.

---

### Flashcard 64

**Q:** How is drift detected?

**A:** State comparison during planning.

---

### Flashcard 65

**Q:** Why should state files be protected?

**A:** They may contain sensitive data.

---

# Domain 7 — Maintain Infrastructure with Terraform

### Flashcard 66

**Q:** What is Terraform import?

**A:** Bringing existing infrastructure under Terraform management.

---

### Flashcard 67

**Q:** Does import create configuration?

**A:** No.

---

### Flashcard 68

**Q:** What command lists state resources?

**A:**

```bash
terraform state list
```

---

### Flashcard 69

**Q:** What command shows state details?

**A:**

```bash
terraform state show
```

---

### Flashcard 70

**Q:** What environment variable enables debug logging?

**A:**

```bash
TF_LOG=DEBUG
```

---

### Flashcard 71

**Q:** What are common TF_LOG levels?

**A:**

* TRACE
* DEBUG
* INFO
* WARN
* ERROR

---

### Flashcard 72

**Q:** Why avoid permanent verbose logging?

**A:** Performance impact and sensitive information exposure.

---

# Domain 8 — HCP Terraform

### Flashcard 73

**Q:** What is HCP Terraform?

**A:** HashiCorp managed Terraform platform.

---

### Flashcard 74

**Q:** What replaces local execution in HCP Terraform?

**A:** Remote Runs.

---

### Flashcard 75

**Q:** What is a Workspace?

**A:** Execution environment for Terraform configurations.

---

### Flashcard 76

**Q:** What is a Project?

**A:** Logical grouping of workspaces.

---

### Flashcard 77

**Q:** Name three HCP Terraform governance features.

**A:**

* Sentinel
* Run Tasks
* Policy Enforcement

---

### Flashcard 78

**Q:** What is Sentinel?

**A:** Policy-as-Code framework.

---

### Flashcard 79

**Q:** What are Run Tasks?

**A:** External integrations executed during runs.

---

### Flashcard 80

**Q:** Why use VCS integration?

**A:** Automate Terraform runs from repository changes.

---

### Flashcard 81

**Q:** What is speculative planning?

**A:** Plan generation without applying changes.

---

### Flashcard 82

**Q:** What is remote state sharing?

**A:** Controlled access to workspace outputs.

---

# Exam Trap Flashcards

### Flashcard 83

**Q:** Does sensitive prevent storage in state?

**A:** No.

---

### Flashcard 84

**Q:** Does import generate Terraform code?

**A:** No.

---

### Flashcard 85

**Q:** Does terraform plan change infrastructure?

**A:** No.

---

### Flashcard 86

**Q:** Does terraform validate contact providers?

**A:** No.

---

### Flashcard 87

**Q:** Does terraform fmt validate configuration?

**A:** No.

---

### Flashcard 88

**Q:** Can Terraform manage resources without state?

**A:** No.

---

### Flashcard 89

**Q:** Does depends_on replace resource references?

**A:** No.

---

### Flashcard 90

**Q:** Is Terraform imperative?

**A:** No. Terraform is declarative.

---

# Final Rapid Review

Remember:

* Terraform is Declarative
* Providers interact with APIs
* State tracks resources
* Plan previews changes
* Apply executes changes
* Modules provide reuse
* Remote State enables collaboration
* State Locking prevents corruption
* Import does not create configuration
* Sensitive does not encrypt state
* HCP Terraform provides governance and remote execution

---
