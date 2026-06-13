# Objective: 4d - Understand and Use Complex Types

## Definition

Terraform supports both primitive types and complex types.

Primitive types:

- string
- number
- bool

Complex types:

- list
- tuple
- set
- map
- object

Complex types allow Terraform configurations to store collections of values and structured data.

They are commonly used with:

- Variables
- Outputs
- for_each
- Dynamic Expressions
- Modules

Terraform Associate (004) frequently includes direct questions about identifying and choosing the correct type.

---

## Core Concepts

### Primitive vs Complex Types

Primitive Types:

```hcl
string
number
bool
```

Complex Types:

```hcl
list(...)
set(...)
map(...)
object(...)
tuple(...)
```

---

# List Type

## Definition

An ordered collection of values of the same type.

Example:

```hcl
variable "availability_zones" {
  type = list(string)
}
```

Value:

```hcl
[
  "us-east-1a",
  "us-east-1b",
  "us-east-1c"
]
```

---

## Characteristics

✅ Ordered

✅ Same Data Type

✅ Allows Duplicate Values

---

## Access Elements

```hcl
var.availability_zones[0]
```

Result:

```text
us-east-1a
```

---

## Real-World Example

```hcl
variable "subnet_ids" {
  type = list(string)
}
```

---

# Tuple Type

## Definition

An ordered collection of values with potentially different types.

Example:

```hcl
variable "server_info" {
  type = tuple([
    string,
    number,
    bool
  ])
}
```

Value:

```hcl
[
  "web-server",
  4,
  true
]
```

---

## Characteristics

✅ Ordered

✅ Different Types Allowed

❌ Type Order Must Match Definition

---

## Access Elements

```hcl
var.server_info[0]
```

Result:

```text
web-server
```

---

## Real-World Example

```hcl
[
  "production",
  3,
  true
]
```

---

# Set Type

## Definition

An unordered collection of unique values.

Example:

```hcl
variable "regions" {
  type = set(string)
}
```

Value:

```hcl
[
  "us-east-1",
  "us-west-2",
  "eu-west-1"
]
```

---

## Characteristics

❌ Unordered

❌ Duplicate Values Not Allowed

✅ Same Data Type

---

Example:

Input:

```hcl
[
  "us-east-1",
  "us-east-1",
  "us-west-2"
]
```

Stored:

```hcl
[
  "us-east-1",
  "us-west-2"
]
```

Duplicates removed automatically.

---

## Real-World Example

Unique Regions:

```hcl
variable "allowed_regions" {
  type = set(string)
}
```

---

# Map Type

## Definition

A collection of key-value pairs.

Example:

```hcl
variable "instance_types" {
  type = map(string)
}
```

Value:

```hcl
{
  dev  = "t3.micro"
  test = "t3.small"
  prod = "t3.large"
}
```

---

## Characteristics

✅ Key-Value Structure

✅ Same Value Type

✅ Fast Lookup

---

## Access Values

```hcl
var.instance_types["prod"]
```

Result:

```text
t3.large
```

---

## Real-World Example

Environment Configuration:

```hcl
{
  dev  = "small"
  prod = "large"
}
```

---

# Object Type

## Definition

A structured collection of named attributes.

Each attribute has its own type.

Example:

```hcl
variable "server" {
  type = object({
    name     = string
    cpu      = number
    enabled  = bool
  })
}
```

Value:

```hcl
{
  name    = "web-server"
  cpu     = 4
  enabled = true
}
```

---

## Characteristics

✅ Named Attributes

✅ Different Types Supported

✅ Structured Data

---

## Access Attributes

```hcl
var.server.name
```

Result:

```text
web-server
```

---

## Real-World Example

Application Configuration:

```hcl
{
  name        = "frontend"
  replicas    = 3
  monitoring  = true
}
```

---

# Type Comparison

| Type   | Ordered          | Duplicate Values | Mixed Types |
| ------ | ---------------- | ---------------- | ----------- |
| list   | Yes              | Yes              | No          |
| tuple  | Yes              | Yes              | Yes         |
| set    | No               | No               | No          |
| map    | Key-Value        | N/A              | No          |
| object | Named Attributes | N/A              | Yes         |

---

# How It Works

Terraform validates input against declared types.

Example:

Variable:

```hcl
variable "instance_count" {
  type = number
}
```

Valid:

```hcl
instance_count = 3
```

Invalid:

```hcl
instance_count = "three"
```

Terraform returns an error.

---

# Terraform Perspective

Example:

```hcl
variable "tags" {
  type = map(string)
}
```

Input:

```hcl
{
  Environment = "Production"
  Owner       = "Platform-Team"
}
```

Terraform validates:

- Correct Type
- Correct Structure
- Correct Value Format

---

# Production Use Case

Enterprise Modules commonly use:

```hcl
list(string)
map(string)
object({...})
```

Examples:

- Subnet Lists
- Tag Maps
- Application Configuration Objects
- Security Policies
- Environment Metadata

---

# Important Exam Points

- list = Ordered collection.
- tuple = Ordered collection with mixed types.
- set = Unordered collection with unique values.
- map = Key-value pairs.
- object = Structured named attributes.
- list and tuple use indexes.
- map uses keys.
- object uses attribute names.
- Terraform validates type constraints.

---

# Common Exam Traps

### Trap 1

Question:

Which type allows duplicate values?

Correct:

```text
list
```

---

### Trap 2

Question:

Which type removes duplicates?

Correct:

```text
set
```

---

### Trap 3

Question:

Which type supports mixed data types?

Correct:

```text
tuple
```

and

```text
object
```

---

### Trap 4

Question:

Which type uses key-value pairs?

Correct:

```text
map
```

---

### Trap 5

Question:

Which type uses named attributes?

Correct:

```text
object
```

---

# Interview Questions

### What is the difference between list and set?

List is ordered and allows duplicates.

Set is unordered and removes duplicates.

### When would you use a map?

When values should be accessed by keys.

### What is an object?

A structured collection of named attributes.

### What is the difference between tuple and list?

Tuple supports multiple data types.
List requires a single data type.

### Which complex type is most commonly used in Terraform modules?

map and object.

---

# Practice Questions

### Question 1

Which Terraform type stores an ordered collection of values of the same type?

A. set

B. tuple

C. list

D. object

**Answer:** C

---

### Question 2

Which Terraform type removes duplicate values?

A. list

B. tuple

C. set

D. map

**Answer:** C

---

### Question 3

Which Terraform type stores key-value pairs?

A. object

B. tuple

C. map

D. list

**Answer:** C

---

### Question 4

Which Terraform type supports named attributes?

A. list

B. set

C. object

D. tuple

**Answer:** C

---

### Question 5

Which Terraform type allows mixed data types in a fixed order?

A. tuple

B. set

C. map

D. list

**Answer:** A

---

## Related Objectives

- 4c Use Variables and Outputs
- 4e Write Dynamic Configuration Using Expressions and Functions
- 5b Describe Variable Scope Within Modules

---

## Key Takeaways

- list = ordered, duplicates allowed.
- tuple = ordered, mixed types allowed.
- set = unordered, duplicates removed.
- map = key-value pairs.
- object = named attributes.
- list and tuple use indexes.
- map uses keys.
- object uses attribute names.
- Complex types are heavily used in variables, modules, and dynamic configurations.
