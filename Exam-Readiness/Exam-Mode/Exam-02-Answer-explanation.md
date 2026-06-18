# Terraform Associate (004) Exam 02 - Answer Explanations

## Q1. Which command imports existing resources into state?

**Answer:** `terraform import`

**Explanation:**
Imports existing infrastructure into Terraform state without recreating resources.

---

## Q2. Which Terraform feature enables shared variables across workspaces?

**Answer:** Variable Sets

**Explanation:**
Variable Sets in HCP Terraform allow variables to be reused across multiple workspaces.

---

## Q3. Which block explicitly defines resource dependencies?

**Answer:** `depends_on`

**Explanation:**
Ensures Terraform creates resources in a specific order when implicit dependencies are insufficient.

---

## Q4. Which command upgrades providers and modules?

**Answer:** `terraform init -upgrade`

**Explanation:**
Downloads newer provider and module versions that satisfy configured constraints.

---

## Q5. Which block calls reusable infrastructure code?

**Answer:** `module`

**Explanation:**
Modules package reusable Terraform configurations.

---

## Q6. Which argument defines a default variable value?

**Answer:** `default`

**Explanation:**
Provides a fallback value when no input is supplied.

```hcl
variable "region" {
  default = "us-east-1"
}
```

---

## Q7. Which lifecycle rule forces replacement when referenced resources change?

**Answer:** `replace_triggered_by`

**Explanation:**
Forces recreation when dependent resources change.

---

## Q8. Which block specifies provider version constraints?

**Answer:** `required_providers`

**Explanation:**
Defines provider source and version requirements.

---

## Q9. Which command displays Terraform and provider versions?

**Answer:** `terraform version`

**Explanation:**
Shows installed Terraform version and provider versions.

---

## Q10. Which block defines input variables?

**Answer:** `variable`

**Explanation:**
Input variables parameterize configurations.

---

## Q11. Which block invokes a reusable module?

**Answer:** `module`

**Explanation:**
References reusable infrastructure code.

---

## Q12. Which block exposes values after apply?

**Answer:** `output`

**Explanation:**
Outputs display useful values after deployment.

---

## Q13. Which block displays values to users?

**Answer:** `output`

**Explanation:**
Output blocks expose resource attributes.

---

## Q14. Which block defines local values?

**Answer:** `locals`

**Explanation:**
Stores reusable expressions within a configuration.

---

## Q15. Which command displays Terraform state information?

**Answer:** `terraform show`

**Explanation:**
Displays the current Terraform state in human-readable format.

---

## Q16. Which command validates Terraform configuration syntax?

**Answer:** `terraform validate`

**Explanation:**
Checks syntax and internal consistency without contacting providers.

---

## Q17. Which meta-argument creates multiple resource instances?

**Answer:** `count`

**Explanation:**
Creates multiple copies of the same resource.

---

## Q18. Which block stores reusable expressions?

**Answer:** `locals`

**Explanation:**
Locals reduce duplication and improve readability.

---

## Q19. Which block configures API access?

**Answer:** `provider`

**Explanation:**
Provider blocks configure cloud and service APIs.

---

## Q20. Which command shows providers used by configuration?

**Answer:** `terraform providers`

**Explanation:**
Displays provider dependencies used by configuration and state.

---

## Q21. Which command formats Terraform configuration files?

**Answer:** `terraform fmt`

**Explanation:**
Automatically formats Terraform files according to HashiCorp standards.

---

## Q22. Which block creates nested blocks dynamically?

**Answer:** `dynamic`

**Explanation:**
Generates repeated nested configuration blocks programmatically.

---

## Q23. Which command upgrades existing provider plugins?

**Answer:** `terraform init -upgrade`

**Explanation:**
Fetches newer provider versions matching constraints.

---

## Q24. Which command shows detailed information about a resource in state?

**Answer:** `terraform state show`

**Explanation:**
Displays detailed attributes for a specific resource.

---

## Q25. Which command acquires a state lock before making changes?

**Answer:** `terraform apply` *(Mock Answer)*

**Explanation:**
Terraform automatically acquires a lock during apply operations when supported by the backend.

---

## Q26. Which command validates configuration files?

**Answer:** `terraform validate`

**Explanation:**
Ensures Terraform configuration is syntactically correct.

---

## Q27. Which feature allows multiple state files from the same configuration?

**Answer:** Workspaces

**Explanation:**
Each workspace maintains its own state file.

---

## Q28. Which meta-argument creates multiple resource instances?

**Answer:** `count`

**Explanation:**
Creates multiple resources using a numeric value.

---

## Q29. Which file commonly stores variable values?

**Answer:** `terraform.tfvars`

**Explanation:**
Common location for supplying variable values.

---

## Q30. Which command destroys managed infrastructure?

**Answer:** `terraform destroy`

**Explanation:**
Removes all Terraform-managed resources.

---

## Q31. Which meta-argument iterates over maps and sets?

**Answer:** `for_each`

**Explanation:**
Creates resources from maps and sets.

---

## Q32. Which command displays Terraform outputs?

**Answer:** `terraform output`

**Explanation:**
Prints output values defined in configuration.

---

## Q33. Which block configures cloud platform access?

**Answer:** `provider`

**Explanation:**
Provider blocks define credentials and regions.

---

## Q34. Which block defines user-supplied values?

**Answer:** `variable`

**Explanation:**
Variables make configurations reusable.

---

## Q35. Which block retrieves existing infrastructure information?

**Answer:** `data`

**Explanation:**
Data sources query existing resources.

---

## Q36. Which command executes infrastructure changes?

**Answer:** `terraform apply`

**Explanation:**
Applies planned changes to infrastructure.

---

## Q37. Which command displays required providers?

**Answer:** `terraform providers`

**Explanation:**
Lists providers used by configuration and state.

---

## Q38. Which command previews infrastructure changes?

**Answer:** `terraform plan`

**Explanation:**
Shows proposed changes before execution.

---

## Q39. Which command removes a resource from state without destroying it?

**Answer:** `terraform state rm`

**Explanation:**
Stops Terraform from tracking a resource.

---

## Q40. Which command generates an execution plan?

**Answer:** `terraform plan`

**Explanation:**
Creates an action plan without applying changes.

---
## Q41. Which block explicitly defines resource dependencies?

**Answer:** `depends_on`

**Explanation:**
`depends_on` creates an explicit dependency between resources when Terraform cannot automatically infer the relationship.

```hcl
resource "aws_instance" "web" {
  depends_on = [aws_vpc.main]
}
```

---

## Q42. Which block stores reusable local expressions?

**Answer:** `locals`

**Explanation:**
The `locals` block defines values that can be reused throughout a Terraform configuration.

```hcl
locals {
  environment = "production"
}
```

---

## Q43. Which file commonly stores backend configuration?

**Answer:** `backend.tf`

**Explanation:**
Backend configuration is often placed in `backend.tf` for organization purposes. Terraform does not require a specific filename.

```hcl
terraform {
  backend "s3" {
    bucket = "terraform-state"
  }
}
```

---

## Q44. Which command imports existing resources?

**Answer:** `terraform import`

**Explanation:**
Imports existing infrastructure into Terraform state without recreating resources.

```bash
terraform import aws_instance.web i-1234567890abcdef0
```

---

## Q45. Which Terraform feature isolates environments?

**Answer:** Workspaces

**Explanation:**
Workspaces allow a single configuration to manage multiple state files.

Examples:

* dev
* staging
* production

---

## Q46. Which lifecycle rule prevents accidental deletion?

**Answer:** `prevent_destroy`

**Explanation:**
Protects important resources from being deleted accidentally.

```hcl
lifecycle {
  prevent_destroy = true
}
```

---

## Q47. Which command initializes a working directory?

**Answer:** `terraform init`

**Explanation:**
Initializes Terraform configuration by:

* Downloading providers
* Downloading modules
* Configuring backends

---

## Q48. Which block retrieves information from existing infrastructure?

**Answer:** `data`

**Explanation:**
Data sources read existing infrastructure without creating resources.

```hcl
data "aws_ami" "latest" {}
```

---

## Q49. Which block defines configurable input values?

**Answer:** `variable`

**Explanation:**
Variables make Terraform configurations reusable and flexible.

```hcl
variable "region" {
  type = string
}
```

---

## Q50. Which command outputs a plan in JSON format?

**Answer:** `terraform plan -json`

**Explanation:**
Produces machine-readable JSON output for automation and CI/CD pipelines.

---

## Q51. Which command lists resources tracked in state?

**Answer:** `terraform state list`

**Explanation:**
Displays all resources currently managed in Terraform state.

```bash
terraform state list
```

---

## Q52. Which lifecycle rule triggers replacement when dependencies change?

**Answer:** `replace_triggered_by`

**Explanation:**
Forces resource replacement when referenced objects change.

```hcl
lifecycle {
  replace_triggered_by = [
    aws_security_group.main
  ]
}
```

---

## Q53. Which command removes resources from Terraform state?

**Answer:** `terraform state rm`

**Explanation:**
Removes resources from state without destroying the actual infrastructure.

```bash
terraform state rm aws_instance.web
```

---

## Q54. Which command generates a dependency graph?

**Answer:** `terraform graph`

**Explanation:**
Creates a visual dependency graph of Terraform resources.

```bash
terraform graph
```

Often used with Graphviz:

```bash
terraform graph | dot -Tpng > graph.png
```

---

## Q55. Which command stops Terraform from tracking a resource?

**Answer:** `terraform state rm`

**Explanation:**
Removes the resource from Terraform state while leaving the resource intact.

---

## Q56. Which lifecycle rule protects critical resources?

**Answer:** `prevent_destroy`

**Explanation:**
Prevents deletion of critical infrastructure such as:

* Databases
* Production VPCs
* Stateful storage

---

## Q57. Which command displays all resources in state?

**Answer:** `terraform state list`

**Explanation:**
Lists every resource tracked in the current state file.

Example:

```bash
terraform state list
```

Output:

```text
aws_vpc.main
aws_subnet.public
aws_instance.web
```

---

## Q58. Which block exposes values after apply?

**Answer:** `output`

**Explanation:**
Outputs provide useful information after deployment.

```hcl
output "public_ip" {
  value = aws_instance.web.public_ip
}
```

---

## Q59. Which command updates state based on real infrastructure?

**Answer:** `terraform refresh`

**Explanation:**
Synchronizes Terraform state with actual infrastructure.

> Note: Modern Terraform versions perform refresh automatically during planning. This command is retained mainly for exam purposes.

---

## Q60. Which block returns values from a Terraform configuration?

**Answer:** `output`

**Explanation:**
Outputs return values from a Terraform configuration for users, modules, and automation tools.

```hcl
output "vpc_id" {
  value = aws_vpc.main.id
}
```

---
