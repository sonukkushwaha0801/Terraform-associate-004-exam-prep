# Terraform Associate (004) Exam Test 01 - Answer Explanations

## Q1. Which command formats Terraform files?

**Answer:** `terraform fmt`

**Explanation:**
`terraform fmt` automatically formats Terraform configuration files according to HashiCorp's recommended style conventions.

---

## Q2. What is a Terraform module?

**Answer:** Reusable Terraform code

**Explanation:**
A module is a container for multiple Terraform resources that can be reused across projects.

---

## Q3. Which Terraform concept represents reusable infrastructure code?

**Answer:** Modules

**Explanation:**
Modules allow infrastructure definitions to be packaged and reused across environments.

---

## Q4. Which feature allows sharing variables across multiple workspaces?

**Answer:** Variable Sets

**Explanation:**
Variable Sets in HCP Terraform allow the same variables to be shared across multiple workspaces.

---

## Q5. What is the main purpose of Terraform state?

**Answer:** Track infrastructure resources

**Explanation:**
Terraform state maps configuration resources to real-world infrastructure resources.

---

## Q6. Which Terraform command shows graph of resources?

**Answer:** `terraform graph`

**Explanation:**
Generates a dependency graph that can be visualized using Graphviz.

---

## Q7. Which block prevents resource destruction?

**Answer:** `prevent_destroy`

**Explanation:**
A lifecycle meta-argument that prevents accidental deletion of critical resources.

---

## Q8. Which command previews changes before applying them?

**Answer:** `terraform plan`

**Explanation:**
Shows the execution plan without making any infrastructure changes.

---

## Q9. Which command generates a JSON representation of a plan?

**Answer:** `terraform plan -json`

**Explanation:**
Outputs plan data in JSON format for automation and integrations.

---

## Q10. Which block specifies provider version constraints?

**Answer:** `required_providers`

**Explanation:**
Defines provider source and version requirements within the Terraform configuration.

---

## Q11. Which command imports existing infrastructure?

**Answer:** `terraform import`

**Explanation:**
Imports existing resources into Terraform state management.

---

## Q12. Which platform provides remote Terraform runs and collaboration?

**Answer:** HCP Terraform

**Explanation:**
Provides remote execution, state management, policy enforcement, and collaboration features.

---

## Q13. Which block defines input variables?

**Answer:** `variable`

**Explanation:**
Input variables allow users to parameterize Terraform configurations.

---

## Q14. Which block defines infrastructure resources?

**Answer:** `resource`

**Explanation:**
Resource blocks define actual infrastructure objects managed by Terraform.

---

## Q15. Which block retrieves data from external sources?

**Answer:** `data`

**Explanation:**
Data sources retrieve information from existing infrastructure without creating resources.

---

## Q16. Which lifecycle rule creates resource before destroying old one?

**Answer:** `create_before_destroy`

**Explanation:**
Ensures replacement resources are created before old ones are removed.

---

## Q17. Which feature prevents concurrent state changes by multiple users?

**Answer:** State Locking

**Explanation:**
Prevents multiple users from modifying the same state file simultaneously.

---

## Q18. Which block defines output values?

**Answer:** `output`

**Explanation:**
Outputs expose values after Terraform apply completes.

---

## Q19. Which lifecycle rule prevents accidental deletion?

**Answer:** `prevent_destroy`

**Explanation:**
Adds protection against resource destruction.

---

## Q20. Which Terraform command initializes a working directory?

**Answer:** `terraform init`

**Explanation:**
Downloads providers, modules, and initializes backend configuration.

---

## Q21. Which lifecycle rule ignores attribute changes?

**Answer:** `ignore_changes`

**Explanation:**
Prevents Terraform from managing specific attribute updates.

---

## Q22. Which command locks state during operations?

**Answer:** `terraform state lock` *(Udemy Answer)*

**Explanation:**
The mock exam expects this answer. In actual Terraform, state locking is handled automatically by supported backends.

---

## Q23. Which file stores Terraform backend configuration?

**Answer:** `backend.tf`

**Explanation:**
Common convention for backend configuration. Terraform does not require a specific filename.

---

## Q24. Which block iterates over multiple values?

**Answer:** `for_each`

**Explanation:**
Creates resources for each item in a map or set.

---

## Q25. Which command lists resources in Terraform state?

**Answer:** `terraform state list`

**Explanation:**
Displays all resources currently tracked in state.

---

## Q26. Which language is used in Terraform configuration files?

**Answer:** HCL

**Explanation:**
Terraform uses HashiCorp Configuration Language (HCL), a human-readable language designed for infrastructure provisioning.

---

## Q27. Which command checks Terraform and provider versions?

**Answer:** `terraform version`

**Explanation:**
Displays the installed Terraform version and provider versions currently in use.

---

## Q28. Which block defines default variable values?

**Answer:** `default`

**Explanation:**
The `default` argument inside a variable block provides a fallback value when none is supplied.

```hcl
variable "region" {
  default = "us-east-1"
}
```

---

## Q29. Which configuration stores Terraform state remotely?

**Answer:** Backend Configuration

**Explanation:**
Backend configuration determines where Terraform state is stored, such as S3, Azure Storage, or HCP Terraform.

---

## Q30. Which command generates an execution plan?

**Answer:** `terraform plan`

**Explanation:**
Creates an execution plan showing what actions Terraform will perform.

---

## Q31. Which block defines explicit dependencies?

**Answer:** `depends_on`

**Explanation:**
Forces Terraform to create resources in a specific order.

```hcl
depends_on = [aws_vpc.main]
```

---

## Q32. Which file extension is used for Terraform configuration files?

**Answer:** `.tf`

**Explanation:**
Terraform configuration files typically use the `.tf` extension.

---

## Q33. Which block defines a module call?

**Answer:** `module`

**Explanation:**
The module block references reusable Terraform code.

```hcl
module "network" {
  source = "./modules/network"
}
```

---

## Q34. Which block defines dynamic resource blocks?

**Answer:** `dynamic`

**Explanation:**
Dynamic blocks generate nested configuration blocks programmatically.

---

## Q35. Which block iterates over map objects?

**Answer:** `for_each`

**Explanation:**
`for_each` creates resources for every element in a map or set.

---

## Q36. Which block manages resource dependencies?

**Answer:** `depends_on`

**Explanation:**
Explicitly specifies dependencies between resources.

---

## Q37. Which provider manages AWS infrastructure?

**Answer:** `aws`

**Explanation:**
The AWS provider enables Terraform to provision AWS resources.

```hcl
provider "aws" {
  region = "us-east-1"
}
```

---

## Q38. Which block is used to output sensitive information?

**Answer:** `output`

**Explanation:**
Output blocks can expose values and optionally mark them as sensitive.

```hcl
output "db_password" {
  value     = var.password
  sensitive = true
}
```

---

## Q39. What is a Terraform provider?

**Answer:** A plugin interacting with APIs

**Explanation:**
Providers allow Terraform to communicate with cloud platforms and services.

---

## Q40. Which command upgrades modules and providers?

**Answer:** `terraform init -upgrade`

**Explanation:**
Downloads newer provider and module versions matching version constraints.

---

## Q41. Which command validates Terraform configuration syntax?

**Answer:** `terraform validate`

**Explanation:**
Checks configuration syntax and internal consistency.

---

## Q42. Which command destroys Terraform-managed resources?

**Answer:** `terraform destroy`

**Explanation:**
Removes all infrastructure managed by the current Terraform configuration.

---

## Q43. What is the purpose of Terraform variables?

**Answer:** Parameterize configurations

**Explanation:**
Variables make configurations reusable and environment-independent.

---

## Q44. Which feature marks sensitive variables?

**Answer:** `sensitive = true`

**Explanation:**
Prevents secrets from appearing in CLI output and logs.

```hcl
variable "password" {
  sensitive = true
}
```

---

## Q45. Where can public Terraform modules be found?

**Answer:** Terraform Registry

**Explanation:**
The Terraform Registry contains official and community-maintained modules.

---

## Q46. Which block configures providers?

**Answer:** `provider`

**Explanation:**
Provider blocks define how Terraform connects to external services.

---

## Q47. Which command removes resources from state without destroying them?

**Answer:** `terraform state rm`

**Explanation:**
Removes a resource from state while leaving the actual infrastructure intact.

---

## Q48. Which lifecycle rule ignores changes to specific attributes?

**Answer:** `ignore_changes`

**Explanation:**
Prevents Terraform from updating selected attributes.

```hcl
lifecycle {
  ignore_changes = [tags]
}
```

---

## Q49. Which command validates provider installation?

**Answer:** `terraform providers`

**Explanation:**
Displays providers required by the configuration and state.

---

## Q50. Which block allows resource replacement before destruction?

**Answer:** `create_before_destroy`

**Explanation:**
Ensures a new resource is created before the old one is removed.

---

## Q51. Which command downloads required providers and modules?

**Answer:** `terraform init`

**Explanation:**
Initializes the working directory and downloads dependencies.

---

## Q52. Which command applies configuration changes to reach the desired state?

**Answer:** `terraform apply`

**Explanation:**
Executes the planned infrastructure changes.

---

## Q53. Which block defines Terraform local values?

**Answer:** `locals`

**Explanation:**
Locals store reusable expressions within a Terraform configuration.

```hcl
locals {
  environment = "prod"
}
```

---

## Q54. Which block allows multiple instances of a resource?

**Answer:** `count`

**Explanation:**
Creates multiple instances of the same resource.

```hcl
count = 3
```

---

## Q55. Which command shows the state of resources?

**Answer:** `terraform show`

**Explanation:**
Displays the current Terraform state in a human-readable format.

---

## Q56. Which command shows detailed resource outputs?

**Answer:** `terraform show`

**Explanation:**
Shows detailed information about resources stored in state.

---

## Q57. Which block allows conditional resource creation?

**Answer:** `count`

**Explanation:**
Conditional creation can be achieved by setting count to 0 or 1.

```hcl
count = var.create_instance ? 1 : 0
```

---

## Q58. Which Terraform feature stores reusable variables globally?

**Answer:** Variable Sets

**Explanation:**
Variable Sets in HCP Terraform allow sharing variables across multiple workspaces.

---

## Q59. Which block fetches external data?

**Answer:** `data`

**Explanation:**
Data sources retrieve information from existing infrastructure.

```hcl
data "aws_ami" "latest" {}
```

---

## Q60. Which command refreshes state with real infrastructure?

**Answer:** `terraform refresh`

**Explanation:**
Updates Terraform state to reflect the actual infrastructure state.
