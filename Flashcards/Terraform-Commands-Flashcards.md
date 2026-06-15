# Terraform Commands Flashcards

> Terraform Associate (004) Command Reference Flashcards
>
> Purpose:
>
> * Rapid command memorization
> * Exam preparation
> * Interview revision
> * Terraform CLI mastery
>
> Focus:
>
> * Frequently tested Terraform commands
> * Command behavior
> * Common flags
> * State operations
> * Debugging commands
> * Exam traps

---

# Core Workflow Commands

### Flashcard 1

**Q:** Which command initializes a Terraform working directory?

**A:**

```bash
terraform init
```

---

### Flashcard 2

**Q:** What does `terraform init` do?

**A:**

* Downloads providers
* Downloads modules
* Configures backend
* Creates `.terraform/`

---

### Flashcard 3

**Q:** Does `terraform init` modify infrastructure?

**A:** No.

---

### Flashcard 4

**Q:** Which command validates Terraform syntax?

**A:**

```bash
terraform validate
```

---

### Flashcard 5

**Q:** Does `terraform validate` contact cloud providers?

**A:** No.

---

### Flashcard 6

**Q:** Which command formats Terraform code?

**A:**

```bash
terraform fmt
```

---

### Flashcard 7

**Q:** Does `terraform fmt` validate configuration?

**A:** No.

---

### Flashcard 8

**Q:** Which command creates an execution plan?

**A:**

```bash
terraform plan
```

---

### Flashcard 9

**Q:** Does `terraform plan` change infrastructure?

**A:** No.

---

### Flashcard 10

**Q:** Which command applies infrastructure changes?

**A:**

```bash
terraform apply
```

---

### Flashcard 11

**Q:** Which command destroys Terraform-managed resources?

**A:**

```bash
terraform destroy
```

---

### Flashcard 12

**Q:** What is the standard Terraform workflow?

**A:**

```text
Write
↓
Init
↓
Validate
↓
Plan
↓
Apply
```

---

# Plan & Apply Commands

### Flashcard 13

**Q:** Save a plan to a file.

**A:**

```bash
terraform plan -out=tfplan
```

---

### Flashcard 14

**Q:** Apply a saved execution plan.

**A:**

```bash
terraform apply tfplan
```

---

### Flashcard 15

**Q:** Why use saved plans?

**A:**

* Review before apply
* Consistent deployment
* Change approval workflows

---

### Flashcard 16

**Q:** Generate plan without refreshing state.

**A:**

```bash
terraform plan -refresh=false
```

---

### Flashcard 17

**Q:** Auto-approve an apply.

**A:**

```bash
terraform apply -auto-approve
```

---

### Flashcard 18

**Q:** Auto-approve a destroy.

**A:**

```bash
terraform destroy -auto-approve
```

---

### Flashcard 19

**Q:** Which command displays planned resource actions?

**A:**

```bash
terraform plan
```

---

### Flashcard 20

**Q:** Meaning of "+" in plan output?

**A:** Resource creation.

---

### Flashcard 21

**Q:** Meaning of "~" in plan output?

**A:** Resource modification.

---

### Flashcard 22

**Q:** Meaning of "-" in plan output?

**A:** Resource destruction.

---

### Flashcard 23

**Q:** Meaning of "-/+" in plan output?

**A:** Destroy and recreate resource.

---

# State Commands

### Flashcard 24

**Q:** List resources in state.

**A:**

```bash
terraform state list
```

---

### Flashcard 25

**Q:** Show detailed resource information.

**A:**

```bash
terraform state show
```

---

### Flashcard 26

**Q:** Show specific resource details.

**A:**

```bash
terraform state show aws_instance.web
```

---

### Flashcard 27

**Q:** Remove resource from state only.

**A:**

```bash
terraform state rm
```

---

### Flashcard 28

**Q:** Does `state rm` destroy infrastructure?

**A:** No.

---

### Flashcard 29

**Q:** Move state resource address.

**A:**

```bash
terraform state mv
```

---

### Flashcard 30

**Q:** Pull remote state locally.

**A:**

```bash
terraform state pull
```

---

### Flashcard 31

**Q:** Push local state to backend.

**A:**

```bash
terraform state push
```

---

### Flashcard 32

**Q:** Why are state commands dangerous?

**A:** They directly manipulate Terraform state.

---

# Import Commands

### Flashcard 33

**Q:** Import existing infrastructure.

**A:**

```bash
terraform import
```

---

### Flashcard 34

**Q:** Example import command.

**A:**

```bash
terraform import aws_instance.web i-123456
```

---

### Flashcard 35

**Q:** Does import create configuration?

**A:** No.

---

### Flashcard 36

**Q:** What happens after import?

**A:** Resource is added to state.

---

### Flashcard 37

**Q:** Why review configuration after import?

**A:** Imported state and code may not match.

---

# Workspace Commands

### Flashcard 38

**Q:** List workspaces.

**A:**

```bash
terraform workspace list
```

---

### Flashcard 39

**Q:** Create a workspace.

**A:**

```bash
terraform workspace new dev
```

---

### Flashcard 40

**Q:** Select a workspace.

**A:**

```bash
terraform workspace select dev
```

---

### Flashcard 41

**Q:** Show current workspace.

**A:**

```bash
terraform workspace show
```

---

### Flashcard 42

**Q:** Delete a workspace.

**A:**

```bash
terraform workspace delete dev
```

---

### Flashcard 43

**Q:** Primary use of workspaces?

**A:** Multiple state instances from same configuration.

---

# Output & Console Commands

### Flashcard 44

**Q:** Display outputs.

**A:**

```bash
terraform output
```

---

### Flashcard 45

**Q:** Display a specific output.

**A:**

```bash
terraform output vpc_id
```

---

### Flashcard 46

**Q:** Open Terraform expression console.

**A:**

```bash
terraform console
```

---

### Flashcard 47

**Q:** Use case of console?

**A:**

* Test functions
* Evaluate expressions
* Debug variables

---

# Graph & Visualization Commands

### Flashcard 48

**Q:** Generate dependency graph.

**A:**

```bash
terraform graph
```

---

### Flashcard 49

**Q:** What does terraform graph visualize?

**A:** Resource dependency relationships.

---

# Provider Commands

### Flashcard 50

**Q:** Show provider dependencies.

**A:**

```bash
terraform providers
```

---

### Flashcard 51

**Q:** Why inspect providers?

**A:** Troubleshooting provider usage.

---

### Flashcard 52

**Q:** Which file locks provider versions?

**A:**

```text
.terraform.lock.hcl
```

---

# Debugging Commands

### Flashcard 53

**Q:** Enable Terraform debug logs.

**A:**

```bash
export TF_LOG=DEBUG
```

---

### Flashcard 54

**Q:** Most verbose logging level?

**A:**

```bash
TF_LOG=TRACE
```

---

### Flashcard 55

**Q:** Disable logging.

**A:**

```bash
unset TF_LOG
```

---

### Flashcard 56

**Q:** Save logs to file.

**A:**

```bash
export TF_LOG_PATH=terraform.log
```

---

### Flashcard 57

**Q:** Why avoid TRACE logging in production?

**A:** Large output and possible sensitive information exposure.

---

# Utility Commands

### Flashcard 58

**Q:** Display Terraform version.

**A:**

```bash
terraform version
```

---

### Flashcard 59

**Q:** Upgrade provider versions.

**A:**

```bash
terraform init -upgrade
```

---

### Flashcard 60

**Q:** Reconfigure backend.

**A:**

```bash
terraform init -reconfigure
```

---

### Flashcard 61

**Q:** Migrate backend state.

**A:**

```bash
terraform init -migrate-state
```

---

### Flashcard 62

**Q:** Show Terraform help.

**A:**

```bash
terraform -help
```

---

### Flashcard 63

**Q:** Show help for a command.

**A:**

```bash
terraform plan -help
```

---

# Exam Trap Flashcards

### Flashcard 64

**Q:** Which command downloads providers?

**A:**

```bash
terraform init
```

---

### Flashcard 65

**Q:** Which command verifies syntax?

**A:**

```bash
terraform validate
```

---

### Flashcard 66

**Q:** Which command previews changes?

**A:**

```bash
terraform plan
```

---

### Flashcard 67

**Q:** Which command executes changes?

**A:**

```bash
terraform apply
```

---

### Flashcard 68

**Q:** Which command imports infrastructure?

**A:**

```bash
terraform import
```

---

### Flashcard 69

**Q:** Which command removes infrastructure?

**A:**

```bash
terraform destroy
```

---

### Flashcard 70

**Q:** Which command manages state?

**A:**

```bash
terraform state
```

---

### Flashcard 71

**Q:** Which command manages workspaces?

**A:**

```bash
terraform workspace
```

---

### Flashcard 72

**Q:** Which command evaluates expressions interactively?

**A:**

```bash
terraform console
```

---

# One-Minute Command Review

| Command              | Purpose                |
| -------------------- | ---------------------- |
| terraform init       | Initialize project     |
| terraform fmt        | Format code            |
| terraform validate   | Validate configuration |
| terraform plan       | Preview changes        |
| terraform apply      | Deploy changes         |
| terraform destroy    | Remove resources       |
| terraform import     | Import resources       |
| terraform output     | Display outputs        |
| terraform console    | Evaluate expressions   |
| terraform state list | List state resources   |
| terraform state show | Show resource details  |
| terraform workspace  | Manage workspaces      |
| terraform graph      | Dependency graph       |
| terraform providers  | Show providers         |
| terraform version    | Show version           |

---
