# Domain 3 Practice Questions

## Core Terraform Workflow

### Domain Statistics

* Objectives Covered: 7
* Total Questions: 30
* Conceptual Questions: 10
* Scenario-Based Questions: 10
* Exam-Trap Questions: 10
* Domain Coverage: 100%

---

## Instructions

Attempt all questions before checking the answers.

✅ Do not scroll to the answer section until you have completed all questions.

✅ Record your answers separately (for example: 1-C, 2-B, 3-A).

✅ After completing all questions, verify your responses using the Answer Key.

---

# Conceptual Questions

### Question 1

Which command is typically executed first in a Terraform project?

A. terraform apply

B. terraform validate

C. terraform init

D. terraform destroy

---

### Question 2

Which command validates Terraform configuration syntax and consistency?

A. terraform fmt

B. terraform validate

C. terraform apply

D. terraform state list

---

### Question 3

Which command generates an execution plan?

A. terraform apply

B. terraform fmt

C. terraform plan

D. terraform destroy

---

### Question 4

Which command actually modifies infrastructure?

A. terraform validate

B. terraform plan

C. terraform fmt

D. terraform apply

---

### Question 5

Which command removes Terraform-managed infrastructure?

A. terraform destroy

B. terraform fmt

C. terraform validate

D. terraform providers

---

### Question 6

Which command formats Terraform configuration files?

A. terraform validate

B. terraform fmt

C. terraform apply

D. terraform state show

---

### Question 7

What does the + symbol represent in an execution plan?

A. Update

B. Destroy

C. Create

D. Replace

---

### Question 8

What does the ~ symbol represent in an execution plan?

A. Update

B. Create

C. Destroy

D. Import

---

### Question 9

What does the - symbol represent in an execution plan?

A. Create

B. Modify

C. Destroy

D. Refresh

---

### Question 10

Which command saves an execution plan?

A. terraform apply

B. terraform plan -out=tfplan

C. terraform validate

D. terraform state pull

---

# Scenario-Based Questions

### Question 11

A developer clones a Terraform repository for the first time.

Which command should be executed before any other Terraform workflow command?

A. terraform plan

B. terraform validate

C. terraform init

D. terraform apply

---

### Question 12

A CI/CD pipeline must verify that Terraform code follows standard formatting without modifying files.

Which command should be used?

A. terraform fmt

B. terraform validate

C. terraform fmt -check

D. terraform plan

---

### Question 13

An engineer wants to verify configuration correctness before reviewing infrastructure changes.

Which command should be executed?

A. terraform validate

B. terraform apply

C. terraform destroy

D. terraform state show

---

### Question 14

A team wants to review proposed infrastructure changes before deployment.

Which command should they use?

A. terraform apply

B. terraform validate

C. terraform plan

D. terraform providers

---

### Question 15

A security team approves a previously reviewed execution plan.

Which command should be used to apply that exact plan?

A. terraform apply

B. terraform apply tfplan

C. terraform validate

D. terraform plan

---

### Question 16

A Terraform plan contains:

```text
+ aws_instance.web
```

What will happen if applied?

A. Resource Updated

B. Resource Destroyed

C. Resource Created

D. Resource Imported

---

### Question 17

A Terraform plan contains:

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

What action will Terraform perform?

A. Destroy

B. Create

C. Modify

D. Import

---

### Question 18

A Terraform plan contains:

```text
- aws_instance.web
```

What action will Terraform perform?

A. Create

B. Modify

C. Destroy

D. Refresh

---

### Question 19

A temporary test environment must be removed after testing.

Which command is most appropriate?

A. terraform fmt

B. terraform validate

C. terraform destroy

D. terraform providers

---

### Question 20

A CI/CD pipeline requires infrastructure deployment without manual confirmation.

Which command is most appropriate?

A. terraform apply

B. terraform apply -auto-approve

C. terraform validate

D. terraform plan

---

# HashiCorp Exam-Trap Questions

### Question 21

Which command creates infrastructure?

A. terraform validate

B. terraform plan

C. terraform apply

D. terraform init

---

### Question 22

Which command previews infrastructure changes without making changes?

A. terraform apply

B. terraform plan

C. terraform destroy

D. terraform init

---

### Question 23

Which command checks formatting?

A. terraform validate

B. terraform plan

C. terraform fmt

D. terraform apply

---

### Question 24

Which statement is TRUE?

A. terraform validate creates resources

B. terraform fmt validates configuration

C. terraform plan modifies infrastructure

D. terraform apply modifies infrastructure

---

### Question 25

Which statement is TRUE?

A. terraform init creates infrastructure

B. terraform init downloads providers

C. terraform init destroys resources

D. terraform init validates configuration

---

### Question 26

Which command previews resource destruction?

A. terraform apply

B. terraform destroy

C. terraform plan -destroy

D. terraform validate

---

### Question 27

Which file is updated after a successful apply?

A. main.tf

B. variables.tf

C. terraform.tfstate

D. outputs.tf

---

### Question 28

What does the symbol -/+ indicate?

A. Create

B. Update

C. Destroy

D. Replace Resource

---

### Question 29

Which Terraform command should generally run before validate, plan, or apply?

A. terraform destroy

B. terraform fmt

C. terraform init

D. terraform output

---

### Question 30

What is the correct Terraform workflow order?

A.

```text
Apply → Plan → Validate → Init
```

B.

```text
Validate → Init → Apply → Plan
```

C.

```text
Init → Validate → Plan → Apply
```

D.

```text
Plan → Apply → Init → Validate
```

---

## Domain 3 Coverage Matrix

| Objective                         | Questions                              |
| --------------------------------- | -------------------------------------- |
| 3a - Terraform Workflow           | 1, 11, 29, 30                          |
| 3b - Initialize Working Directory | 1, 11, 25, 29                          |
| 3c - Validate Configuration       | 2, 13, 24                              |
| 3d - Execution Plans              | 3, 7, 8, 9, 10, 14, 16, 17, 18, 22, 28 |
| 3e - Apply Changes                | 4, 15, 20, 21, 27                      |
| 3f - Destroy Infrastructure       | 5, 19, 26                              |
| 3g - Formatting                   | 6, 12, 23                              |

---

## High-Probability Exam Topics

* Terraform Workflow Order
* terraform init
* terraform validate
* terraform plan
* terraform apply
* terraform destroy
* terraform fmt
* Plan Symbols (+, ~, -, -/+)
* Saved Plans
* Auto Approve
* Destroy Plans
* State Updates After Apply

---

## Self-Assessment

### 27-30 Correct

Excellent. Domain 3 is exam-ready.

### 23-26 Correct

Strong understanding. Review missed questions.

### 18-22 Correct

Good understanding. Revisit Objectives 3a-3g.

### Below 18 Correct

Review Domain 3 notes completely before proceeding.

---

## Domain Completion Checklist

* [ ] Read 3a - Terraform Workflow
* [ ] Read 3b - Initialize Working Directory
* [ ] Read 3c - Validate Configuration
* [ ] Read 3d - Execution Plans
* [ ] Read 3e - Apply Changes
* [ ] Read 3f - Destroy Infrastructure
* [ ] Read 3g - Formatting
* [ ] Completed Domain 3 Practice Questions
* [ ] Scored 27+/30
* [ ] Reviewed Incorrect Answers
* [ ] Ready for Domain 4
