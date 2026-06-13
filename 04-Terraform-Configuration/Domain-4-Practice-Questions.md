# Domain 4 Practice Questions

## Terraform Configuration

### Domain Statistics

- Objectives Covered: 8
- Total Questions: 50
- Conceptual Questions: 20
- Scenario-Based Questions: 20
- HashiCorp Exam-Trap Questions: 10

---

# Instructions

Attempt all questions before checking answers.

✅ Record answers separately.

✅ Complete all questions before reviewing explanations.

✅ Passing Target: 45+/50

---

# Conceptual Questions

### Question 1

Which Terraform block is used to create and manage infrastructure?

A. data

B. resource

C. output

D. variable

---

### Question 2

Which Terraform block retrieves information about existing infrastructure?

A. resource

B. variable

C. output

D. data

---

### Question 3

Which syntax correctly references a resource attribute?

A.

```text
aws_vpc.id.main
```

B.

```text
main.aws_vpc.id
```

C.

```text
aws_vpc.main.id
```

D.

```text
id.aws_vpc.main
```

---

### Question 4

How are variables referenced?

A.

```text
variable.region
```

B.

```text
var.region
```

C.

```text
region.variable
```

D.

```text
input.region
```

---

### Question 5

What is the primary purpose of outputs?

A. Create Resources

B. Store State

C. Expose Values

D. Install Providers

---

### Question 6

Which Terraform type represents an ordered collection of values of the same type?

A. set

B. tuple

C. list

D. object

---

### Question 7

Which Terraform type removes duplicate values?

A. list

B. tuple

C. set

D. map

---

### Question 8

Which Terraform type stores key-value pairs?

A. object

B. tuple

C. map

D. list

---

### Question 9

Which Terraform type uses named attributes?

A. list

B. set

C. object

D. tuple

---

### Question 10

Which Terraform type allows mixed data types in a fixed order?

A. list

B. tuple

C. map

D. set

---

### Question 11

Which expression syntax represents conditional logic?

A.

```hcl
if condition then true else false
```

B.

```hcl
condition ? true_value : false_value
```

C.

```hcl
condition => value
```

D.

```hcl
condition || value
```

---

### Question 12

Which meta-argument creates multiple resource instances using a number?

A. lifecycle

B. provider

C. count

D. depends_on

---

### Question 13

Which meta-argument is generally preferred for unique resources?

A. count

B. for_each

C. provider

D. lifecycle

---

### Question 14

What does each.key represent?

A. Resource ID

B. Provider Name

C. Current Collection Key

D. Current State

---

### Question 15

Which function returns the number of elements in a collection?

A. lookup()

B. concat()

C. length()

D. merge()

---

### Question 16

Which function retrieves a value from a map?

A. upper()

B. lookup()

C. join()

D. split()

---

### Question 17

Which argument defines validation logic?

A. default

B. value

C. condition

D. provider

---

### Question 18

When are preconditions evaluated?

A. After Resource Creation

B. Before Resource Actions

C. During Init

D. During Destroy

---

### Question 19

When are postconditions evaluated?

A. Before Planning

B. Before Resource Actions

C. After Resource Actions

D. During Init

---

### Question 20

What does sensitive = true do?

A. Encrypt Data

B. Hide Output Values

C. Delete Secrets

D. Remove State Entries

---

# Scenario-Based Questions

### Question 21

You need Terraform to create a new VPC.

Which block should be used?

A. variable

B. output

C. resource

D. data

---

### Question 22

You need the latest Amazon Linux AMI.

Which block should be used?

A. resource

B. data

C. variable

D. output

---

### Question 23

A subnet requires the ID of a VPC.

Which expression should be used?

A.

```text
aws_vpc.main.id
```

B.

```text
var.vpc_id
```

C.

```text
output.vpc_id
```

D.

```text
resource.vpc.id
```

---

### Question 24

A Terraform module must receive an environment name from users.

Which feature should be used?

A. Output

B. Variable

C. Backend

D. Data Source

---

### Question 25

A Terraform module must expose a VPC ID to another module.

Which feature should be used?

A. Variable

B. Output

C. Provider

D. Local

---

### Question 26

A configuration stores multiple subnet IDs.

Which type is most appropriate?

A. bool

B. number

C. list(string)

D. string

---

### Question 27

A configuration stores environment-specific instance types.

Which type is most appropriate?

A. tuple

B. map(string)

C. list(number)

D. bool

---

### Question 28

An engineer wants three identical EC2 instances.

Which feature should be used?

A. depends_on

B. count

C. lookup

D. validation

---

### Question 29

An engineer wants separate instances for:

```text
dev
test
prod
```

using names as identifiers.

Which feature should be used?

A. count

B. provider

C. for_each

D. lifecycle

---

### Question 30

A Terraform deployment should use larger instances in production.

Which feature is most appropriate?

A. Conditional Expression

B. Output

C. Data Source

D. Backend

---

### Question 31

A company only allows:

```text
dev
test
prod
```

as valid environments.

Which Terraform feature should enforce this?

A. Validation Block

B. Output

C. Provider

D. Resource

---

### Question 32

A resource should only be created if a variable is true.

Which expression is commonly used?

A.

```hcl
count = var.enabled ? 1 : 0
```

B.

```hcl
count = true
```

C.

```hcl
provider = true
```

D.

```hcl
depends_on = true
```

---

### Question 33

A Terraform deployment must verify an EC2 instance reaches the running state after creation.

Which feature is appropriate?

A. Variable Validation

B. Precondition

C. Postcondition

D. Output

---

### Question 34

A team wants to prevent weak passwords from being supplied.

Which feature should be used?

A. Validation

B. Resource

C. Backend

D. Provider

---

### Question 35

An application password should not appear in CLI output.

What should be used?

A. output

B. sensitive = true

C. backend

D. depends_on

---

### Question 36

A company stores secrets in HashiCorp Vault.

Terraform retrieves credentials during deployment.

What security practice is being followed?

A. Hardcoded Secrets

B. Secret Management

C. State Manipulation

D. Dynamic Providers

---

### Question 37

Terraform automatically creates a dependency between subnet and VPC because subnet references VPC ID.

What type of dependency is this?

A. Explicit

B. Manual

C. Implicit

D. Forced

---

### Question 38

A dependency exists but Terraform cannot infer it automatically.

What should be used?

A. lifecycle

B. count

C. depends_on

D. lookup

---

### Question 39

An engineer wants to visualize Terraform dependencies.

Which command should be used?

A.

```bash
terraform output
```

B.

```bash
terraform graph
```

C.

```bash
terraform validate
```

D.

```bash
terraform providers
```

---

### Question 40

A Terraform configuration needs a collection of unique AWS regions.

Which type is most appropriate?

A. list

B. tuple

C. set

D. object

---

# HashiCorp Exam-Trap Questions

### Question 41

Does sensitive = true encrypt secrets?

A. Yes

B. No

---

### Question 42

Can sensitive values still exist in terraform.tfstate?

A. Yes

B. No

---

### Question 43

Which dependency type is preferred?

A. Explicit

B. Implicit

---

### Question 44

Which is generally preferred for unique resource instances?

A. count

B. for_each

---

### Question 45

Which block manages infrastructure lifecycle?

A. resource

B. data

---

### Question 46

Which block only retrieves information?

A. resource

B. data

---

### Question 47

What does for_each primarily iterate over?

A. Numbers

B. Collections

---

### Question 48

Which HashiCorp product is recommended for secret management?

A. Consul

B. Vault

C. Nomad

D. Packer

---

### Question 49

Which file commonly contains secrets?

A. main.tf

B. terraform.tfstate

C. outputs.tf

D. providers.tf

---

### Question 50

Which statement is TRUE?

A. Sensitive variables encrypt values.

B. State files never contain secrets.

C. Vault is a secrets-management platform.

D. Terraform automatically rotates all secrets.

---

# Domain 4 Coverage Matrix

| Objective                    | Questions                           |
| ---------------------------- | ----------------------------------- |
| 4a Resource vs Data Blocks   | 1,2,21,22,45,46                     |
| 4b References                | 3,23,37                             |
| 4c Variables and Outputs     | 4,5,24,25                           |
| 4d Complex Types             | 6,7,8,9,10,26,27,40                 |
| 4e Expressions and Functions | 11,12,13,14,15,16,28,29,30,32,44,47 |
| 4f Dependencies              | 37,38,39,43                         |
| 4g Validation                | 17,18,19,31,33,34                   |
| 4h Sensitive Data            | 20,35,36,41,42,48,49,50             |

---

## Self-Assessment

### 45-50 Correct

Excellent. Domain 4 is exam-ready.

### 40-44 Correct

Strong understanding. Review missed topics.

### 35-39 Correct

Good foundation. Revisit complex types, expressions, and validation.

### Below 35 Correct

Review Domain 4 notes completely before proceeding.

---

## Domain Completion Checklist

- [ ] Read 4a - Resource vs Data Blocks
- [ ] Read 4b - Resource References
- [ ] Read 4c - Variables and Outputs
- [ ] Read 4d - Complex Types
- [ ] Read 4e - Expressions and Functions
- [ ] Read 4f - Dependencies
- [ ] Read 4g - Custom Validation
- [ ] Read 4h - Sensitive Data
- [ ] Completed Domain 4 Practice Questions
- [ ] Scored 45+/50
- [ ] Reviewed Incorrect Answers
- [ ] Ready for Domain 5
