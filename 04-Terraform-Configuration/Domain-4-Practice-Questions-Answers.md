# Domain 4 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 8
- Total Questions: 50
- Conceptual Questions: 20
- Scenario-Based Questions: 20
- Exam-Trap Questions: 10

---

# Objective Coverage

| Objective                      | Questions                           |
| ------------------------------ | ----------------------------------- |
| 4a - Resource and Data Blocks  | 1,2,21,22,45,46                     |
| 4b - Resource References       | 3,23,37                             |
| 4c - Variables and Outputs     | 4,5,24,25                           |
| 4d - Complex Types             | 6,7,8,9,10,26,27,40                 |
| 4e - Expressions and Functions | 11,12,13,14,15,16,28,29,30,32,44,47 |
| 4f - Dependencies              | 37,38,39,43                         |
| 4g - Validation                | 17,18,19,31,33,34                   |
| 4h - Sensitive Data Management | 20,35,36,41,42,48,49,50             |

---

# Answer Key

| Question | Answer |
| -------- | ------ |
| 1        | B      |
| 2        | D      |
| 3        | C      |
| 4        | B      |
| 5        | C      |
| 6        | C      |
| 7        | C      |
| 8        | C      |
| 9        | C      |
| 10       | B      |
| 11       | B      |
| 12       | C      |
| 13       | B      |
| 14       | C      |
| 15       | C      |
| 16       | B      |
| 17       | C      |
| 18       | B      |
| 19       | C      |
| 20       | B      |
| 21       | C      |
| 22       | B      |
| 23       | A      |
| 24       | B      |
| 25       | B      |
| 26       | C      |
| 27       | B      |
| 28       | B      |
| 29       | C      |
| 30       | A      |
| 31       | A      |
| 32       | A      |
| 33       | C      |
| 34       | A      |
| 35       | B      |
| 36       | B      |
| 37       | C      |
| 38       | C      |
| 39       | B      |
| 40       | C      |
| 41       | B      |
| 42       | A      |
| 43       | B      |
| 44       | B      |
| 45       | A      |
| 46       | B      |
| 47       | B      |
| 48       | B      |
| 49       | B      |
| 50       | C      |

---

# Detailed Explanations

## Question 1

**Answer:** B

**Objective:** 4a

Resource blocks create and manage infrastructure.

Example:

```hcl
resource "aws_instance" "web" {
}
```

Terraform tracks resources in state and manages their lifecycle.

---

## Question 2

**Answer:** D

**Objective:** 4a

Data sources retrieve information from existing infrastructure.

Example:

```hcl
data "aws_ami" "latest" {
}
```

Terraform reads information only.

---

## Question 3

**Answer:** C

**Objective:** 4b

Correct syntax:

```text
aws_vpc.main.id
```

Pattern:

```text
resource_type.resource_name.attribute
```

---

## Question 4

**Answer:** B

**Objective:** 4c

Variables are referenced using:

```text
var.variable_name
```

Example:

```hcl
var.region
```

---

## Question 5

**Answer:** C

**Objective:** 4c

Outputs expose information after deployment.

Common examples:

- VPC IDs
- Subnet IDs
- Load Balancer DNS Names
- Resource ARNs

---

## Question 6

**Answer:** C

**Objective:** 4d

List:

- Ordered
- Same Data Type
- Duplicates Allowed

Example:

```hcl
["a","b","c"]
```

---

## Question 7

**Answer:** C

**Objective:** 4d

Set:

- Unordered
- Unique Values Only

Duplicates are automatically removed.

---

## Question 8

**Answer:** C

**Objective:** 4d

Map stores:

```hcl
{
  dev  = "small"
  prod = "large"
}
```

Key-value pairs.

---

## Question 9

**Answer:** C

**Objective:** 4d

Objects contain named attributes.

Example:

```hcl
{
  name = "web"
  cpu  = 4
}
```

---

## Question 10

**Answer:** B

**Objective:** 4d

Tuple supports multiple data types.

Example:

```hcl
[
  "web",
  4,
  true
]
```

---

## Question 11

**Answer:** B

**Objective:** 4e

Terraform conditional syntax:

```hcl
condition ? true_value : false_value
```

Frequently tested.

---

## Question 12

**Answer:** C

**Objective:** 4e

count creates multiple instances.

Example:

```hcl
count = 3
```

Creates:

```text
resource[0]
resource[1]
resource[2]
```

---

## Question 13

**Answer:** B

**Objective:** 4e

HashiCorp generally prefers:

```hcl
for_each
```

for unique resources.

Reason:

Stable resource addresses.

---

## Question 14

**Answer:** C

**Objective:** 4e

```hcl
each.key
```

returns current collection key.

Example:

```text
dev
prod
```

---

## Question 15

**Answer:** C

**Objective:** 4e

```hcl
length()
```

returns collection size.

Example:

```hcl
length(["a","b","c"])
```

Result:

```text
3
```

---

## Question 16

**Answer:** B

**Objective:** 4e

```hcl
lookup()
```

retrieves values from maps.

Example:

```hcl
lookup(var.instance_types, "prod")
```

---

## Question 17

**Answer:** C

**Objective:** 4g

Validation blocks use:

```hcl
condition
```

to define validation logic.

---

## Question 18

**Answer:** B

**Objective:** 4g

Preconditions run:

```text
Before Resource Actions
```

---

## Question 19

**Answer:** C

**Objective:** 4g

Postconditions run:

```text
After Resource Actions
```

---

## Question 20

**Answer:** B

**Objective:** 4h

Sensitive values are hidden in CLI output.

Example:

```text
(sensitive value)
```

---

## Question 21

**Answer:** C

**Objective:** 4a

Creating infrastructure requires:

```hcl
resource
```

block.

---

## Question 22

**Answer:** B

**Objective:** 4a

Existing AMI lookup:

```hcl
data "aws_ami"
```

---

## Question 23

**Answer:** A

**Objective:** 4b

Subnet references VPC ID using:

```hcl
aws_vpc.main.id
```

---

## Question 24

**Answer:** B

**Objective:** 4c

Module inputs are provided using variables.

---

## Question 25

**Answer:** B

**Objective:** 4c

Module outputs expose values.

Example:

```hcl
output "vpc_id" {
}
```

---

## Question 26

**Answer:** C

**Objective:** 4d

Multiple subnet IDs:

```hcl
list(string)
```

---

## Question 27

**Answer:** B

**Objective:** 4d

Environment mappings:

```hcl
{
  dev  = "t3.micro"
  prod = "t3.large"
}
```

Best represented by:

```hcl
map(string)
```

---

## Question 28

**Answer:** B

**Objective:** 4e

Three identical resources:

```hcl
count = 3
```

---

## Question 29

**Answer:** C

**Objective:** 4e

Named resources:

```hcl
for_each
```

Preferred.

---

## Question 30

**Answer:** A

**Objective:** 4e

Environment-specific sizing:

```hcl
var.environment == "prod"
? "t3.large"
: "t3.micro"
```

Conditional expression.

---

## Question 31

**Answer:** A

**Objective:** 4g

Validation block ensures allowed values.

---

## Question 32

**Answer:** A

**Objective:** 4e

Conditional resource creation:

```hcl
count = var.enabled ? 1 : 0
```

---

## Question 33

**Answer:** C

**Objective:** 4g

Verify expected state after creation:

```hcl
postcondition
```

---

## Question 34

**Answer:** A

**Objective:** 4g

Password standards are enforced through validation.

---

## Question 35

**Answer:** B

**Objective:** 4h

Hide passwords using:

```hcl
sensitive = true
```

---

## Question 36

**Answer:** B

**Objective:** 4h

Vault usage represents proper secret management.

---

## Question 37

**Answer:** C

**Objective:** 4f

References automatically create:

```text
Implicit Dependencies
```

---

## Question 38

**Answer:** C

**Objective:** 4f

Manual dependency declaration:

```hcl
depends_on
```

---

## Question 39

**Answer:** B

**Objective:** 4f

Dependency graph:

```bash
terraform graph
```

---

## Question 40

**Answer:** C

**Objective:** 4d

Unique values:

```hcl
set(string)
```

---

## Question 41

**Answer:** B

**Exam Trap**

Sensitive values are hidden.

They are NOT encrypted.

---

## Question 42

**Answer:** A

**Exam Trap**

Secrets may still exist in:

```text
terraform.tfstate
```

Very common exam question.

---

## Question 43

**Answer:** B

**Exam Trap**

Preferred dependency type:

```text
Implicit Dependency
```

---

## Question 44

**Answer:** B

**Exam Trap**

Preferred:

```hcl
for_each
```

for unique resources.

---

## Question 45

**Answer:** A

Resource blocks manage lifecycle.

---

## Question 46

**Answer:** B

Data blocks retrieve information only.

---

## Question 47

**Answer:** B

for_each iterates over:

- Maps
- Sets
- Collections

---

## Question 48

**Answer:** B

HashiCorp secret management solution:

```text
Vault
```

---

## Question 49

**Answer:** B

Most sensitive Terraform file:

```text
terraform.tfstate
```

---

## Question 50

**Answer:** C

Vault provides:

- Secret Storage
- Dynamic Credentials
- Rotation
- Access Control
- Auditing

---

## Exam Readiness Score

### 45-50 Correct

Domain 4 Exam Ready.

### 40-44 Correct

Strong Understanding.

### 35-39 Correct

Review Expressions, Validation, and Dependencies.

### Below 35 Correct

Re-read Domain 4 Theory and Retake Practice Questions.
