# Domain 2 Practice Questions - Answers

## Domain Statistics

* Objectives Covered: 4
* Total Questions: 30
* Conceptual Questions: 10
* Scenario-Based Questions: 10
* Exam-Trap Questions: 10
* Domain Coverage: 100%

---

## Objective Coverage

| Objective                                                   | Questions                        |
| ----------------------------------------------------------- | -------------------------------- |
| 2a - Install and Version Terraform Providers                | 1, 2, 3, 4, 5, 12, 19, 23, 29    |
| 2b - Describe How Terraform Uses Providers                  | 6, 7, 15, 21, 22                 |
| 2c - Write Terraform Configuration Using Multiple Providers | 13, 14, 18, 20, 26, 30           |
| 2d - Explain How Terraform Uses and Manages State           | 8, 9, 10, 16, 17, 24, 25, 27, 28 |

---

# Answer Key

| Question | Answer |
| -------- | ------ |
| 1        | B      |
| 2        | C      |
| 3        | C      |
| 4        | B      |
| 5        | C      |
| 6        | B      |
| 7        | A      |
| 8        | C      |
| 9        | B      |
| 10       | C      |
| 11       | B      |
| 12       | C      |
| 13       | B      |
| 14       | C      |
| 15       | C      |
| 16       | C      |
| 17       | C      |
| 18       | C      |
| 19       | C      |
| 20       | B      |
| 21       | B      |
| 22       | B      |
| 23       | C      |
| 24       | B      |
| 25       | C      |
| 26       | B      |
| 27       | C      |
| 28       | B      |
| 29       | C      |
| 30       | C      |

---

# Detailed Explanations

### Question 1

**Answer:** B

**Objective:** 2a - Install and Version Terraform Providers

**Explanation:**

Providers are plugins that enable Terraform to communicate with APIs and manage infrastructure resources.

Examples:

* AWS Provider
* AzureRM Provider
* Google Provider
* Kubernetes Provider

---

### Question 2

**Answer:** C

**Objective:** 2a - Install and Version Terraform Providers

**Explanation:**

```bash
terraform init
```

downloads and installs required providers, initializes modules, and configures backends.

This is usually the first Terraform command executed in a project.

---

### Question 3

**Answer:** C

**Objective:** 2a - Install and Version Terraform Providers

**Explanation:**

The `required_providers` block specifies:

* Provider source address
* Provider version constraints

Example:

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```

---

### Question 4

**Answer:** B

**Objective:** 2a - Install and Version Terraform Providers

**Explanation:**

The `source` argument tells Terraform where the provider should be downloaded from.

Example:

```hcl
source = "hashicorp/aws"
```

---

### Question 5

**Answer:** C

**Objective:** 2a - Install and Version Terraform Providers

**Explanation:**

Version constraints ensure consistent provider versions across environments and deployments.

Example:

```hcl
version = "~> 5.0"
```

---

### Question 6

**Answer:** B

**Objective:** 2b - Describe How Terraform Uses Providers

**Explanation:**

Providers perform API operations.

Terraform Core determines what should happen.

Providers perform the actual interactions with external systems.

---

### Question 7

**Answer:** A

**Objective:** 2b - Describe How Terraform Uses Providers

**Explanation:**

Resource types are defined by providers.

Example:

```hcl
aws_instance
aws_s3_bucket
azurerm_resource_group
```

These resource types exist because providers define them.

---

### Question 8

**Answer:** C

**Objective:** 2d - Explain How Terraform Uses and Manages State

**Explanation:**

Terraform stores state in:

```text
terraform.tfstate
```

by default.

---

### Question 9

**Answer:** B

**Objective:** 2d - Explain How Terraform Uses and Manages State

**Explanation:**

Terraform state stores information about managed infrastructure resources and their attributes.

---

### Question 10

**Answer:** C

**Objective:** 2d - Explain How Terraform Uses and Manages State

**Explanation:**

Terraform compares:

```text
Current State
       vs
Desired State
```

to determine required infrastructure changes.

---

### Question 11

**Answer:** B

**Objective:** 2a

**Explanation:**

terraform init:

* Downloads providers
* Downloads modules
* Configures backend
* Initializes working directory

It does not create resources.

---

### Question 12

**Answer:** C

**Objective:** 2a

**Explanation:**

Version constraints ensure all engineers use compatible provider versions.

This prevents unexpected behavior.

---

### Question 13

**Answer:** B

**Objective:** 2c

**Explanation:**

Terraform supports multiple providers in a single configuration.

Example:

* AWS Provider
* AzureRM Provider

used simultaneously.

---

### Question 14

**Answer:** C

**Objective:** 2c

**Explanation:**

Provider aliases allow multiple configurations of the same provider.

Common use case:

```text
AWS East Region
AWS West Region
```

within the same configuration.

---

### Question 15

**Answer:** C

**Objective:** 2b

**Explanation:**

Resources require an associated provider.

Without provider configuration Terraform cannot communicate with the platform API.

---

### Question 16

**Answer:** C

**Objective:** 2d

**Explanation:**

Terraform compares current state with desired state and detects infrastructure differences.

---

### Question 17

**Answer:** C

**Objective:** 2d

**Explanation:**

State provides efficient infrastructure tracking and change detection for large environments.

---

### Question 18

**Answer:** C

**Objective:** 2c

**Explanation:**

```hcl
provider = aws.west
```

references a provider alias configuration.

---

### Question 19

**Answer:** C

**Objective:** 2a

**Explanation:**

```bash
terraform init -upgrade
```

upgrades installed providers when newer versions satisfy version constraints.

---

### Question 20

**Answer:** B

**Objective:** 2c

**Explanation:**

Terraform managing AWS and GitHub demonstrates service-agnostic infrastructure management.

Terraform is not limited to cloud platforms.

---

### Question 21

**Answer:** B

**Objective:** 2b

**Explanation:**

Providers communicate with APIs.

Terraform Core does not directly interact with cloud APIs.

---

### Question 22

**Answer:** B

**Objective:** 2b

**Explanation:**

A provider is a plugin that extends Terraform's functionality.

---

### Question 23

**Answer:** C

**Objective:** 2a

**Explanation:**

Providers are installed during:

```bash
terraform init
```

---

### Question 24

**Answer:** B

**Objective:** 2d

**Explanation:**

State represents Terraform's recorded snapshot of infrastructure.

---

### Question 25

**Answer:** C

**Objective:** 2d

**Explanation:**

State acts as Terraform's infrastructure tracking mechanism.

Without state Terraform cannot properly manage resources.

---

### Question 26

**Answer:** B

**Objective:** 2c

**Explanation:**

Aliases create multiple configurations of the same provider.

---

### Question 27

**Answer:** C

**Objective:** 2d

**Explanation:**

Terraform cannot operate correctly without state.

State is a fundamental Terraform component.

---

### Question 28

**Answer:** B

**Objective:** 2d

**Explanation:**

State maps Terraform configuration to real infrastructure resources.

---

### Question 29

**Answer:** C

**Objective:** 2a

**Explanation:**

The source argument identifies the provider location.

Example:

```hcl
source = "hashicorp/aws"
```

---

### Question 30

**Answer:** C

**Objective:** 2c

**Explanation:**

```hcl
provider "aws" {
  alias = "west"
}
```

creates a provider alias named west.

---
