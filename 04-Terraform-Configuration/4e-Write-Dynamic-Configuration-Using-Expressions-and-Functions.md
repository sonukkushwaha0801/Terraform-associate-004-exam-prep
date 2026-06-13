# Objective: 4e - Write Dynamic Configuration Using Expressions and Functions

## Definition

Terraform expressions and functions allow configurations to become dynamic rather than static.

Instead of hardcoding values, Terraform can:

- Calculate values
- Transform data
- Loop through collections
- Conditionally create resources
- Generate infrastructure dynamically

This objective is one of the most heavily tested areas in the Terraform Associate (004) exam.

---

## Core Concepts

Terraform provides:

- Expressions
- Conditional Expressions
- for Expressions
- count
- for_each
- Built-in Functions

These features allow infrastructure to adapt based on inputs.

---

# Expressions

## Definition

An expression produces a value.

Example:

```hcl
instance_type = var.environment == "prod" ? "t3.large" : "t3.micro"
```

Terraform evaluates the expression and returns a value.

---

## Expression Examples

Reference Variable:

```hcl
var.region
```

Reference Resource:

```hcl
aws_vpc.main.id
```

Mathematical Expression:

```hcl
2 + 3
```

Result:

```text
5
```

String Expression:

```hcl
"${var.environment}-vpc"
```

Result:

```text
prod-vpc
```

---

# Conditional Expressions

## Definition

Terraform supports if/else style logic.

Syntax:

```hcl
condition ? true_value : false_value
```

---

## Example

```hcl
var.environment == "prod" ? "t3.large" : "t3.micro"
```

Result:

```text
prod → t3.large
dev  → t3.micro
```

---

## Real-World Example

```hcl
resource "aws_instance" "web" {
  instance_type = var.environment == "prod" ? "t3.large" : "t3.micro"
}
```

Production gets larger instances.

Development gets smaller instances.

---

# count Meta-Argument

## Definition

Creates multiple resource instances.

Syntax:

```hcl
count = <NUMBER>
```

---

## Example

```hcl
resource "aws_instance" "web" {
  count         = 3
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

Terraform creates:

```text
aws_instance.web[0]
aws_instance.web[1]
aws_instance.web[2]
```

---

## Conditional Resource Creation

```hcl
count = var.create_instance ? 1 : 0
```

Result:

```text
true  → Create Resource
false → Do Not Create Resource
```

---

## Characteristics

✅ Simple

✅ Numeric

❌ Not ideal for unique resource definitions

---

# for_each Meta-Argument

## Definition

Creates resources from collections.

Works with:

- map
- set

---

## Example

```hcl
resource "aws_s3_bucket" "bucket" {
  for_each = toset(["dev", "test", "prod"])

  bucket = each.key
}
```

Terraform creates:

```text
dev
test
prod
```

buckets.

---

## Map Example

```hcl
resource "aws_instance" "web" {
  for_each = {
    dev  = "t3.micro"
    prod = "t3.large"
  }

  instance_type = each.value
}
```

---

## each Object

### each.key

Current key.

Example:

```text
dev
```

---

### each.value

Current value.

Example:

```text
t3.micro
```

---

## Characteristics

✅ Preferred over count for unique resources

✅ More readable

✅ Stable resource addresses

---

# count vs for_each

| Feature                        | count | for_each |
| ------------------------------ | ----- | -------- |
| Uses Number                    | Yes   | No       |
| Uses Collection                | No    | Yes      |
| Stable Resource Names          | No    | Yes      |
| Preferred for Unique Resources | No    | Yes      |

---

## Example

count:

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

for_each:

```hcl
for_each = {
  dev  = "small"
  prod = "large"
}
```

Creates:

```text
resource["dev"]
resource["prod"]
```

---

# for Expressions

## Definition

Transform collections into new collections.

Syntax:

```hcl
[
  for item in list : expression
]
```

---

## Example

Input:

```hcl
["dev", "test", "prod"]
```

Expression:

```hcl
[
  for env in var.environments : upper(env)
]
```

Output:

```hcl
[
  "DEV",
  "TEST",
  "PROD"
]
```

---

## Map Example

```hcl
{
  for env in var.environments :
  env => upper(env)
}
```

Output:

```hcl
{
  dev  = "DEV"
  test = "TEST"
  prod = "PROD"
}
```

---

# Functions

## Definition

Terraform includes built-in functions for manipulating values.

Functions:

```hcl
function(arguments)
```

---

# Common Exam Functions

## upper()

Converts string to uppercase.

```hcl
upper("terraform")
```

Result:

```text
TERRAFORM
```

---

## lower()

Converts string to lowercase.

```hcl
lower("Terraform")
```

Result:

```text
terraform
```

---

## length()

Returns number of elements.

```hcl
length(["a","b","c"])
```

Result:

```text
3
```

---

## concat()

Combines lists.

```hcl
concat(["a"], ["b"])
```

Result:

```hcl
["a","b"]
```

---

## join()

Joins strings.

```hcl
join("-", ["dev","web"])
```

Result:

```text
dev-web
```

---

## split()

Splits strings.

```hcl
split("-", "dev-web")
```

Result:

```hcl
["dev","web"]
```

---

## lookup()

Retrieve value from map.

```hcl
lookup(var.instance_types, "prod")
```

---

## merge()

Merge maps.

```hcl
merge(map1, map2)
```

---

## contains()

Checks membership.

```hcl
contains(["dev","prod"], "prod")
```

Result:

```text
true
```

---

## toset()

Convert list to set.

```hcl
toset(["a","b","c"])
```

---

# How It Works

```text
Input Variables
       │
       ▼
Expressions
       │
       ▼
Functions
       │
       ▼
Terraform Evaluation
       │
       ▼
Infrastructure Configuration
```

---

# Terraform Perspective

Example:

```hcl
resource "aws_instance" "web" {
  count = var.environment == "prod" ? 3 : 1

  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

Result:

```text
Production → 3 Instances
Development → 1 Instance
```

Infrastructure becomes dynamic.

---

# Real-World Example

Environment-Based Deployment:

```hcl
variable "environment" {}
```

Conditional:

```hcl
instance_type =
var.environment == "prod"
? "t3.large"
: "t3.micro"
```

Terraform automatically adjusts infrastructure.

---

# Production Use Case

Enterprise Infrastructure frequently uses:

- count
- for_each
- conditional expressions
- lookup()
- merge()
- length()

Examples:

- Multi-environment deployments
- Dynamic subnet creation
- Dynamic tagging
- Environment-specific sizing

---

# Important Exam Points

- Expressions return values.
- Conditional syntax:

```hcl
condition ? true : false
```

- count creates multiple resources using numbers.
- for_each creates resources using collections.
- for_each is generally preferred for unique resources.
- each.key and each.value are used with for_each.
- for expressions transform collections.
- Functions manipulate values.

---

# Common Exam Traps

### Trap 1

Question:

Which syntax represents a conditional expression?

Correct:

```hcl
condition ? true_value : false_value
```

---

### Trap 2

Question:

Which meta-argument creates multiple resources?

Correct:

```hcl
count
```

and

```hcl
for_each
```

---

### Trap 3

Question:

Which is preferred for unique resources?

Correct:

```hcl
for_each
```

---

### Trap 4

Question:

What does each.key represent?

Correct:

Current collection key.

---

### Trap 5

Question:

What function returns collection size?

Correct:

```hcl
length()
```

---

### Trap 6

Question:

What function retrieves a value from a map?

Correct:

```hcl
lookup()
```

---

# Interview Questions

### What is a Terraform expression?

A construct that evaluates to a value.

### What is the syntax for a conditional expression?

```hcl
condition ? true_value : false_value
```

### Difference between count and for_each?

count uses numbers.

for_each uses collections and provides stable resource addresses.

### Why is for_each often preferred?

Because resources are identified by keys rather than indexes.

### What are Terraform functions?

Built-in helpers used to transform and manipulate data.

---

# Practice Questions

### Question 1

Which Terraform construct is used for if/else logic?

A. count

B. for_each

C. Conditional Expression

D. lookup

**Answer:** C

---

### Question 2

What does count = 3 create?

A. One Resource

B. Three Resources

C. Three Providers

D. Three Modules

**Answer:** B

---

### Question 3

Which meta-argument is preferred for unique resources?

A. count

B. for_each

C. depends_on

D. lifecycle

**Answer:** B

---

### Question 4

What does each.value represent?

A. Resource ID

B. Current Collection Value

C. Provider Name

D. Variable Name

**Answer:** B

---

### Question 5

Which function returns the number of elements in a collection?

A. lookup()

B. upper()

C. length()

D. concat()

**Answer:** C

---

## Related Objectives

- 4c Use Variables and Outputs
- 4d Understand and Use Complex Types
- 4f Define Resource Dependencies
- 5c Use Modules in Configuration

---

## Key Takeaways

- Expressions return values.
- Conditional expressions use ? : syntax.
- count creates multiple resources using numbers.
- for_each creates resources from collections.
- for_each is preferred for unique resources.
- each.key and each.value are heavily tested.
- for expressions transform collections.
- Functions manipulate data.
- Dynamic configuration is one of the highest-weighted topics in the Terraform Associate (004) exam.
