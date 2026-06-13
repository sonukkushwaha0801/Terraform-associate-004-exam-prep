# Domain 4 Revision Sheet

## Terraform Configuration

### Objectives Covered

- 4a Resource and Data Blocks
- 4b Resource References
- 4c Variables and Outputs
- 4d Complex Types
- 4e Expressions and Functions
- 4f Resource Dependencies
- 4g Custom Validation
- 4h Sensitive Data Management

---

# 4a Resource vs Data Blocks

## Resource Block

Purpose:

```text
Create and Manage Infrastructure
```

Syntax:

```hcl
resource "<TYPE>" "<NAME>" {

}
```

Example:

```hcl
resource "aws_instance" "web" {
  instance_type = "t3.micro"
}
```

Terraform:

✅ Creates

✅ Updates

✅ Destroys

✅ Tracks in State

---

## Data Block

Purpose:

```text
Read Existing Infrastructure
```

Syntax:

```hcl
data "<TYPE>" "<NAME>" {

}
```

Example:

```hcl
data "aws_ami" "latest" {

}
```

Terraform:

✅ Reads

❌ Creates

❌ Modifies

❌ Destroys

---

## Exam Memory Trick

```text
Resource = Create
Data     = Read
```

---

# 4b Resource References

## Syntax

```text
resource_type.resource_name.attribute
```

Example:

```hcl
aws_vpc.main.id
```

---

## Data Source Syntax

```text
data.type.name.attribute
```

Example:

```hcl
data.aws_ami.latest.id
```

---

## Important Fact

References create:

```text
Implicit Dependencies
```

automatically.

---

# 4c Variables and Outputs

## Variable

Purpose:

```text
Input Values
```

Syntax:

```hcl
variable "region" {

}
```

Reference:

```hcl
var.region
```

---

## Output

Purpose:

```text
Expose Values
```

Syntax:

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---

## Variable Loading Order (Exam Favorite)

Highest Precedence:

```text
CLI -var
```

↓

```text
*.auto.tfvars
```

↓

```text
terraform.tfvars
```

↓

```text
Environment Variables
```

↓

```text
Default Values
```

---

## Auto Loaded Files

```text
terraform.tfvars
```

```text
*.auto.tfvars
```

---

# 4d Complex Types

## List

```hcl
list(string)
```

Properties:

✅ Ordered

✅ Duplicates Allowed

❌ Mixed Types

---

Example:

```hcl
["a","b","c"]
```

---

## Tuple

```hcl
tuple([
 string,
 number
])
```

Properties:

✅ Ordered

✅ Mixed Types

---

Example:

```hcl
[
 "web",
 3
]
```

---

## Set

```hcl
set(string)
```

Properties:

❌ Unordered

❌ Duplicates Removed

---

Example:

```hcl
[
 "a",
 "a",
 "b"
]
```

Stored As:

```hcl
[
 "a",
 "b"
]
```

---

## Map

```hcl
map(string)
```

Properties:

✅ Key-Value

Example:

```hcl
{
 dev = "small"
 prod = "large"
}
```

---

## Object

```hcl
object({
 name = string
 cpu  = number
})
```

Properties:

✅ Named Attributes

✅ Mixed Types

---

## Type Comparison

| Type   | Ordered   | Duplicate Values | Mixed Types |
| ------ | --------- | ---------------- | ----------- |
| list   | Yes       | Yes              | No          |
| tuple  | Yes       | Yes              | Yes         |
| set    | No        | No               | No          |
| map    | Key-Value | N/A              | No          |
| object | Named     | N/A              | Yes         |

---

# 4e Expressions and Functions

## Conditional Expression

Syntax:

```hcl
condition ? true_value : false_value
```

Example:

```hcl
var.environment == "prod"
? "t3.large"
: "t3.micro"
```

---

## count

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

## Conditional Creation

```hcl
count = var.enabled ? 1 : 0
```

---

## for_each

Example:

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

## each.key

Returns:

```text
Current Key
```

---

## each.value

Returns:

```text
Current Value
```

---

## count vs for_each

| Feature               | count | for_each |
| --------------------- | ----- | -------- |
| Number Based          | Yes   | No       |
| Collection Based      | No    | Yes      |
| Stable Resource Names | No    | Yes      |
| Preferred             | No    | Yes      |

---

# Most Tested Functions

## length()

```hcl
length(["a","b","c"])
```

Result:

```text
3
```

---

## lookup()

```hcl
lookup(map, key)
```

Retrieve map value.

---

## upper()

```hcl
upper("terraform")
```

Result:

```text
TERRAFORM
```

---

## lower()

```hcl
lower("Terraform")
```

Result:

```text
terraform
```

---

## join()

```hcl
join("-", ["dev","web"])
```

Result:

```text
dev-web
```

---

## split()

```hcl
split("-", "dev-web")
```

Result:

```hcl
["dev","web"]
```

---

## concat()

Merge Lists.

---

## merge()

Merge Maps.

---

## contains()

Membership Test.

---

## toset()

Convert List → Set.

---

# 4f Dependencies

## Implicit Dependency

Created automatically through references.

Example:

```hcl
vpc_id = aws_vpc.main.id
```

Terraform automatically creates:

```text
VPC
 ↓
Subnet
```

---

## Explicit Dependency

Syntax:

```hcl
depends_on = [
 aws_vpc.main
]
```

---

## Recommendation

Preferred:

```text
Implicit Dependency
```

Use:

```hcl
depends_on
```

only when necessary.

---

## Dependency Visualization

```bash
terraform graph
```

---

## Creation Order

```text
Dependency First
```

---

## Destruction Order

```text
Reverse Dependency Order
```

---

# 4g Validation

## Variable Validation

Syntax:

```hcl
validation {
 condition     = ...
 error_message = ...
}
```

---

## Example

```hcl
validation {
 condition = contains(
   ["dev","test","prod"],
   var.environment
 )

 error_message = "Invalid Environment"
}
```

---

## Preconditions

Executed:

```text
Before Resource Action
```

Syntax:

```hcl
precondition {
}
```

---

## Postconditions

Executed:

```text
After Resource Action
```

Syntax:

```hcl
postcondition {
}
```

---

## Exam Memory Trick

```text
Pre  = Before
Post = After
```

---

# 4h Sensitive Data

## Sensitive Variable

```hcl
variable "password" {
 sensitive = true
}
```

---

## Sensitive Output

```hcl
output "password" {
 sensitive = true
}
```

---

## Important Exam Fact

```hcl
sensitive = true
```

✅ Hides Output

❌ Does NOT Encrypt Data

---

# State File Security

## File

```text
terraform.tfstate
```

May contain:

- Passwords
- Tokens
- Secrets
- Credentials

---

## Exam Trap

Question:

Does Terraform State contain secrets?

Answer:

```text
YES
```

---

# Vault

## HashiCorp Secret Management Platform

Purpose:

- Store Secrets
- Rotate Secrets
- Dynamic Credentials
- Access Control
- Auditing

---

## Recommended Approach

❌ Hardcoded Passwords

```hcl
password = "Admin123"
```

---

✅ Vault

```text
Vault → Terraform → Resource
```

---

# Top 20 Exam Facts

### Resource creates infrastructure.

### Data reads infrastructure.

### Resource reference:

```hcl
aws_vpc.main.id
```

### Variable reference:

```hcl
var.region
```

### Outputs expose values.

### list = ordered.

### tuple = mixed types.

### set = unique values.

### map = key-value.

### object = named attributes.

### Conditional syntax:

```hcl
condition ? true : false
```

### count uses numbers.

### for_each uses collections.

### each.key returns key.

### each.value returns value.

### lookup() retrieves map values.

### Implicit dependencies are preferred.

### Precondition = before.

### Postcondition = after.

### sensitive hides values.

### Vault manages secrets.

---

# 30-Second Final Exam Revision

Remember:

```text
Resource = Create
Data     = Read
```

```text
var.name
```

```text
aws_vpc.main.id
```

```text
condition ? true : false
```

```text
count
```

```text
for_each
```

```text
depends_on
```

```text
validation
```

```text
precondition
```

```text
postcondition
```

```text
sensitive = true
```

```text
Vault
```

Most Common Exam Traps:

- Resource vs Data
- count vs for_each
- list vs set
- map vs object
- sensitive ≠ encryption
- Secrets can exist in state
- Implicit dependency preferred
- Precondition vs Postcondition

---

## Domain Completion Checklist

- [ ] Completed 4a Resource vs Data Blocks
- [ ] Completed 4b Resource References
- [ ] Completed 4c Variables and Outputs
- [ ] Completed 4d Complex Types
- [ ] Completed 4e Expressions and Functions
- [ ] Completed 4f Dependencies
- [ ] Completed 4g Validation
- [ ] Completed 4h Sensitive Data Management
- [ ] Completed Domain 4 Practice Questions
- [ ] Scored 45+/50
- [ ] Reviewed All Mistakes
- [ ] Ready For Domain 5 Modules
