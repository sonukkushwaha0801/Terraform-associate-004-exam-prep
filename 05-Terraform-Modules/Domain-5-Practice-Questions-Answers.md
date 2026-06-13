# Domain 5 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 4
- Total Questions: 30
- Conceptual Questions: 10
- Scenario-Based Questions: 10
- Exam-Trap Questions: 10

---

# Objective Coverage

| Objective                   | Questions                   |
| --------------------------- | --------------------------- |
| 5a - Module Sources         | 3,14,15,16,21,22,27,29      |
| 5b - Variable Scope         | 4,5,6,7,8,12,13,17,23,24,28 |
| 5c - Use Modules            | 1,2,6,7,8,11,12,13,17,30    |
| 5d - Manage Module Versions | 9,10,18,19,20,25,26,27      |

---

# Answer Key

| Question | Answer |
| -------- | ------ |
| 1        | B      |
| 2        | C      |
| 3        | C      |
| 4        | D      |
| 5        | A      |
| 6        | B      |
| 7        | C      |
| 8        | A      |
| 9        | B      |
| 10       | C      |
| 11       | C      |
| 12       | B      |
| 13       | C      |
| 14       | B      |
| 15       | B      |
| 16       | C      |
| 17       | A      |
| 18       | B      |
| 19       | C      |
| 20       | C      |
| 21       | C      |
| 22       | B      |
| 23       | B      |
| 24       | C      |
| 25       | B      |
| 26       | C      |
| 27       | C      |
| 28       | B      |
| 29       | C      |
| 30       | C      |

---

# Detailed Explanations

## Question 1

**Answer:** B

**Objective:** 5c

Terraform modules allow infrastructure code to be reused.

Benefits:

- Reduced Duplication
- Standardization
- Easier Maintenance
- Faster Deployment

---

## Question 2

**Answer:** C

**Objective:** 5c

Modules are called using:

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

---

## Question 3

**Answer:** C

**Objective:** 5a

The source argument tells Terraform where a module is located.

Example:

```hcl
source = "./modules/vpc"
```

---

## Question 4

**Answer:** D

**Objective:** 5b

The root module is the directory where Terraform commands are executed.

Example:

```bash
terraform apply
```

executed from:

```text
project/
```

---

## Question 5

**Answer:** A

**Objective:** 5b

A child module is a module called by another module.

Example:

```hcl
module "network" {
  source = "./modules/network"
}
```

---

## Question 6

**Answer:** B

**Objective:** 5b, 5c

Modules receive data through variables.

Example:

```hcl
module "vpc" {
  cidr_block = "10.0.0.0/16"
}
```

---

## Question 7

**Answer:** C

**Objective:** 5b, 5c

Modules expose information through outputs.

Example:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---

## Question 8

**Answer:** A

**Objective:** 5b, 5c

Correct syntax:

```hcl
module.vpc.vpc_id
```

Pattern:

```hcl
module.<module_name>.<output_name>
```

---

## Question 9

**Answer:** B

**Objective:** 5d

Terraform modules generally follow:

```text
MAJOR.MINOR.PATCH
```

Semantic Versioning.

---

## Question 10

**Answer:** C

**Objective:** 5d

Module upgrades:

```bash
terraform init -upgrade
```

---

## Question 11

**Answer:** C

**Objective:** 5c

Shared infrastructure logic should be implemented as modules.

---

## Question 12

**Answer:** B

**Objective:** 5b

Input values enter modules through variables.

---

## Question 13

**Answer:** C

**Objective:** 5b

Information exits modules through outputs.

---

## Question 14

**Answer:** B

**Objective:** 5a

Local module:

```hcl
source = "./modules/network"
```

---

## Question 15

**Answer:** B

**Objective:** 5a

Terraform Registry format:

```text
namespace/module/provider
```

Example:

```text
terraform-aws-modules/vpc/aws
```

---

## Question 16

**Answer:** C

**Objective:** 5a

Git repositories are valid Terraform module sources.

Example:

```hcl
source = "git::https://github.com/company/vpc-module.git"
```

---

## Question 17

**Answer:** A

**Objective:** 5b

Outputs are referenced using:

```hcl
module.network.vpc_id
```

---

## Question 18

**Answer:** B

**Objective:** 5d

Version constraints prevent unexpected upgrades.

---

## Question 19

**Answer:** C

**Objective:** 5d

```hcl
version = "~> 5.0"
```

Allows:

```text
5.x
```

Blocks:

```text
6.x
```

---

## Question 20

**Answer:** C

**Objective:** 5d

```hcl
~> 5.2.0
```

Allows:

```text
5.2.1
5.2.5
5.2.8
```

Not:

```text
5.3.0
```

---

## Question 21

**Answer:** C

**Objective:** 5a

Modules are downloaded during:

```bash
terraform init
```

---

## Question 22

**Answer:** B

**Objective:** 5a

Downloaded modules are stored in:

```text
.terraform/modules
```

---

## Question 23

**Answer:** B

**Objective:** 5b

Module variables are isolated.

Terraform does not automatically pass root variables into child modules.

---

## Question 24

**Answer:** C

**Objective:** 5b

Correct communication model:

```text
Root → Child
```

via Variables

and

```text
Child → Root
```

via Outputs

---

## Question 25

**Answer:** B

**Objective:** 5d

```hcl
~> 5.0
```

means:

```text
>= 5.0.0
< 6.0.0
```

---

## Question 26

**Answer:** C

**Objective:** 5d

Semantic Versioning:

```text
MAJOR.MINOR.PATCH
```

MAJOR introduces breaking changes.

---

## Question 27

**Answer:** C

**Objective:** 5a, 5d

Git modules commonly use:

```text
?ref=
```

Examples:

```text
?ref=v1.0.0
?ref=main
?ref=a1b2c3d
```

---

## Question 28

**Answer:** B

**Objective:** 5b

Modules communicate using:

- Inputs
- Outputs

---

## Question 29

**Answer:** C

**Objective:** 5a

Every module block requires:

```hcl
source
```

---

## Question 30

**Answer:** C

**Objective:** 5c

Primary benefits:

- Reusability
- Standardization
- Maintainability

---

# Exam Readiness Score

### 27-30 Correct

Domain 5 Exam Ready

### 23-26 Correct

Strong Understanding

### 18-22 Correct

Review Module Scope and Version Constraints

### Below 18 Correct

Re-read Domain 5 Theory and Retake Questions
