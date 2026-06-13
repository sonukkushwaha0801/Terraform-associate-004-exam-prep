# Domain 3 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 7
- Total Questions: 30
- Conceptual Questions: 10
- Scenario-Based Questions: 10
- Exam-Trap Questions: 10
- Domain Coverage: 100%

---

## Objective Coverage

| Objective | Questions |
|------------|------------|
| 3a - Describe the Terraform Workflow | 1, 11, 29, 30 |
| 3b - Initialize a Terraform Working Directory | 1, 11, 25, 29 |
| 3c - Validate a Terraform Configuration | 2, 13, 24 |
| 3d - Generate and Review an Execution Plan | 3, 7, 8, 9, 10, 14, 16, 17, 18, 22, 28 |
| 3e - Apply Changes to Infrastructure | 4, 15, 20, 21, 27 |
| 3f - Destroy Terraform-Managed Infrastructure | 5, 19, 26 |
| 3g - Apply Formatting and Style Adjustments | 6, 12, 23 |

---

# Answer Key

| Question | Answer |
|-----------|----------|
| 1 | C |
| 2 | B |
| 3 | C |
| 4 | D |
| 5 | A |
| 6 | B |
| 7 | C |
| 8 | A |
| 9 | C |
| 10 | B |
| 11 | C |
| 12 | C |
| 13 | A |
| 14 | C |
| 15 | B |
| 16 | C |
| 17 | C |
| 18 | C |
| 19 | C |
| 20 | B |
| 21 | C |
| 22 | B |
| 23 | C |
| 24 | D |
| 25 | B |
| 26 | C |
| 27 | C |
| 28 | D |
| 29 | C |
| 30 | C |

---

# Detailed Explanations

### Question 1

**Answer:** C

**Objective:** 3a, 3b

**Explanation:**

```bash
terraform init
```

is typically the first command executed in a Terraform project.

It prepares the working directory by:

- Downloading providers
- Downloading modules
- Configuring backends

---

### Question 2

**Answer:** B

**Objective:** 3c

**Explanation:**

```bash
terraform validate
```

checks:

- Syntax correctness
- Configuration consistency
- Resource references

It does not create resources or generate plans.

---

### Question 3

**Answer:** C

**Objective:** 3d

**Explanation:**

```bash
terraform plan
```

generates an execution plan showing proposed infrastructure changes.

Terraform compares:

```text
Current State
      vs
Desired State
```

before generating the plan.

---

### Question 4

**Answer:** D

**Objective:** 3e

**Explanation:**

```bash
terraform apply
```

is the command that actually performs infrastructure changes.

Terraform may:

- Create resources
- Modify resources
- Destroy resources

depending on the execution plan.

---

### Question 5

**Answer:** A

**Objective:** 3f

**Explanation:**

```bash
terraform destroy
```

removes Terraform-managed infrastructure.

Terraform updates state after successful destruction.

---

### Question 6

**Answer:** B

**Objective:** 3g

**Explanation:**

```bash
terraform fmt
```

formats Terraform configuration files according to Terraform style standards.

---

### Question 7

**Answer:** C

**Objective:** 3d

**Explanation:**

```text
+
```

indicates resource creation.

Example:

```text
+ aws_instance.web
```

Terraform plans to create the resource.

---

### Question 8

**Answer:** A

**Objective:** 3d

**Explanation:**

```text
~
```

indicates modification of an existing resource.

Example:

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

---

### Question 9

**Answer:** C

**Objective:** 3d

**Explanation:**

```text
-
```

indicates resource destruction.

Example:

```text
- aws_instance.web
```

---

### Question 10

**Answer:** B

**Objective:** 3d

**Explanation:**

Execution plans can be saved using:

```bash
terraform plan -out=tfplan
```

Saved plans can later be applied exactly as reviewed.

---

### Question 11

**Answer:** C

**Objective:** 3a, 3b

**Explanation:**

After cloning a repository, Terraform must be initialized before running validate, plan, or apply.

---

### Question 12

**Answer:** C

**Objective:** 3g

**Explanation:**

```bash
terraform fmt -check
```

checks formatting compliance without modifying files.

Frequently used in CI/CD pipelines.

---

### Question 13

**Answer:** A

**Objective:** 3c

**Explanation:**

Validation should occur before reviewing infrastructure changes.

```bash
terraform validate
```

detects configuration issues early.

---

### Question 14

**Answer:** C

**Objective:** 3d

**Explanation:**

```bash
terraform plan
```

allows teams to review proposed changes before deployment.

---

### Question 15

**Answer:** B

**Objective:** 3e

**Explanation:**

Approved plans can be applied using:

```bash
terraform apply tfplan
```

This guarantees the exact reviewed plan is executed.

---

### Question 16

**Answer:** C

**Objective:** 3d

**Explanation:**

```text
+ aws_instance.web
```

means Terraform intends to create the resource.

---

### Question 17

**Answer:** C

**Objective:** 3d

**Explanation:**

```text
~ instance_type = "t2.micro" -> "t3.micro"
```

means Terraform will modify the existing resource.

---

### Question 18

**Answer:** C

**Objective:** 3d

**Explanation:**

```text
- aws_instance.web
```

means Terraform will destroy the resource.

---

### Question 19

**Answer:** C

**Objective:** 3f

**Explanation:**

Temporary environments are commonly removed using:

```bash
terraform destroy
```

to reduce costs and clean up resources.

---

### Question 20

**Answer:** B

**Objective:** 3e

**Explanation:**

```bash
terraform apply -auto-approve
```

skips manual confirmation and is commonly used in automation pipelines.

---

### Question 21

**Answer:** C

**Objective:** 3e

**Explanation:**

Only:

```bash
terraform apply
```

creates infrastructure.

Many candidates incorrectly select:

```bash
terraform plan
```

which only previews changes.

---

### Question 22

**Answer:** B

**Objective:** 3d

**Explanation:**

```bash
terraform plan
```

previews changes without modifying infrastructure.

---

### Question 23

**Answer:** C

**Objective:** 3g

**Explanation:**

Formatting is handled by:

```bash
terraform fmt
```

not validate or apply.

---

### Question 24

**Answer:** D

**Objective:** 3e

**Explanation:**

Terraform apply executes infrastructure changes.

Other options describe incorrect command behavior.

---

### Question 25

**Answer:** B

**Objective:** 3b

**Explanation:**

```bash
terraform init
```

downloads providers and prepares the working directory.

It does not create infrastructure.

---

### Question 26

**Answer:** C

**Objective:** 3f

**Explanation:**

Destruction can be previewed using:

```bash
terraform plan -destroy
```

before resources are removed.

---

### Question 27

**Answer:** C

**Objective:** 3e

**Explanation:**

Terraform updates:

```text
terraform.tfstate
```

after successful infrastructure changes.

---

### Question 28

**Answer:** D

**Objective:** 3d

**Explanation:**

```text
-/+
```

means Terraform must destroy and recreate the resource.

This is known as resource replacement.

---

### Question 29

**Answer:** C

**Objective:** 3a, 3b

**Explanation:**

Terraform should generally be initialized before validate, plan, or apply.

---

### Question 30

**Answer:** C

**Objective:** 3a

**Explanation:**

Correct workflow:

```text
Init
  ↓
Validate
  ↓
Plan
  ↓
Apply
```

This is one of the highest-probability exam topics.

---
