# Domain 2 Practice Questions

## Terraform Fundamentals

### Domain Statistics

* Objectives Covered: 4
* Total Questions: 30
* Conceptual Questions: 10
* Scenario-Based Questions: 10
* Exam-Trap Questions: 10
* Domain Coverage: 100%

---

## Instructions

Attempt all questions before checking the answers.

✅ Do not scroll to the answer section until you have completed all questions.

✅ Record your answers separately (for example: 1-B, 2-C, 3-A).

✅ After completing all questions, verify your responses using the Answer Key.

---

# Conceptual Questions

### Question 1

Which Terraform component enables communication with external APIs?

A. Modules

B. Providers

C. Outputs

D. Variables

---

### Question 2

Which command downloads and installs required providers?

A. terraform apply

B. terraform validate

C. terraform init

D. terraform plan

---

### Question 3

What is the primary purpose of the required_providers block?

A. Define resources

B. Define variables

C. Define provider requirements

D. Define outputs

---

### Question 4

Which argument specifies where Terraform should download a provider?

A. provider

B. source

C. version

D. alias

---

### Question 5

What is the primary purpose of a provider version constraint?

A. Configure regions

B. Configure authentication

C. Control provider versions

D. Manage state

---

### Question 6

Which Terraform component performs API operations?

A. Terraform Core

B. Providers

C. State File

D. Modules

---

### Question 7

Which Terraform component defines resource types such as aws_instance?

A. Providers

B. State

C. Variables

D. Outputs

---

### Question 8

What is the default Terraform state file name?

A. terraform.state

B. terraform.tf

C. terraform.tfstate

D. terraform.json

---

### Question 9

Terraform state primarily stores:

A. Terraform source code

B. Managed infrastructure information

C. Module documentation

D. Variable definitions

---

### Question 10

Terraform determines required infrastructure changes by comparing:

A. Variables and Outputs

B. Modules and Providers

C. Current State and Desired State

D. Providers and Resources

---

# Scenario-Based Questions

### Question 11

A DevOps engineer executes terraform init for the first time in a new project.

What is Terraform primarily doing?

A. Creating resources

B. Downloading providers and initializing the directory

C. Destroying resources

D. Updating state

---

### Question 12

A company wants all engineers to use the same AWS provider version.

Which Terraform feature should be used?

A. Variables

B. Outputs

C. Version Constraints

D. Workspaces

---

### Question 13

A team manages infrastructure in both AWS and Azure from a single Terraform configuration.

Which Terraform capability makes this possible?

A. State Locking

B. Multiple Providers

C. Variables

D. Outputs

---

### Question 14

A company manages resources in two AWS regions.

Which Terraform feature is most appropriate?

A. Outputs

B. Variables

C. Provider Aliases

D. State Locking

---

### Question 15

A Terraform configuration defines an EC2 instance, but Terraform does not know which provider to use.

What is most likely missing?

A. State File

B. Output Block

C. Provider Configuration

D. Variable Definition

---

### Question 16

A Terraform plan shows an EC2 instance changing from t2.micro to t3.micro.

What enabled Terraform to detect this difference?

A. Outputs

B. Variables

C. State Comparison

D. Provider Alias

---

### Question 17

A platform team manages 1,000 cloud resources.

Why is Terraform state important?

A. It stores modules

B. It stores outputs

C. It efficiently tracks managed infrastructure

D. It stores documentation

---

### Question 18

A resource contains:

```hcl
provider = aws.west
```

What does this indicate?

A. State Backend

B. Variable Reference

C. Provider Alias Usage

D. Module Source

---

### Question 19

A company upgrades provider versions regularly.

Which command is commonly used to upgrade installed providers?

A. terraform validate

B. terraform fmt

C. terraform init -upgrade

D. terraform output

---

### Question 20

A Terraform configuration manages AWS infrastructure and GitHub repositories.

This demonstrates:

A. Multi-Cloud

B. Service-Agnostic Infrastructure Management

C. State Locking

D. Resource Drift

---

# HashiCorp Exam-Trap Questions

### Question 21

Which statement is TRUE?

A. Terraform Core directly creates cloud resources

B. Providers communicate with APIs

C. State files communicate with APIs

D. Modules communicate with APIs

---

### Question 22

What is a provider?

A. State File

B. Plugin

C. Workspace

D. Module

---

### Question 23

Which command installs providers?

A. terraform plan

B. terraform apply

C. terraform init

D. terraform destroy

---

### Question 24

What does Terraform state represent?

A. Desired State Only

B. Current Infrastructure Snapshot

C. Provider Configuration

D. Variable Definitions

---

### Question 25

Which statement BEST describes Terraform state?

A. Optional Feature

B. Documentation File

C. Resource Tracking Mechanism

D. Provider Registry

---

### Question 26

Provider aliases are primarily used to:

A. Store Variables

B. Create Multiple Provider Configurations

C. Store Outputs

D. Manage State

---

### Question 27

Which statement is FALSE?

A. Providers are plugins

B. Terraform downloads providers during init

C. Terraform can operate without state

D. Providers communicate with APIs

---

### Question 28

Which Terraform component maps configuration to real infrastructure?

A. Provider Alias

B. State

C. Variable

D. Module

---

### Question 29

What is the purpose of source = "hashicorp/aws"?

A. Define Resource Type

B. Define State Backend

C. Define Provider Location

D. Define Region

---

### Question 30

A Terraform configuration uses:

```hcl
provider "aws" {
  alias = "west"
}
```

What has been configured?

A. Backend

B. Output

C. Provider Alias

D. State Locking

---

## Domain 2 Coverage Matrix

| Objective                                    | Questions                        |
| -------------------------------------------- | -------------------------------- |
| 2a - Install and Version Terraform Providers | 1, 2, 3, 4, 5, 12, 19, 23, 29    |
| 2b - Describe How Terraform Uses Providers   | 6, 7, 15, 21, 22                 |
| 2c - Multiple Provider Configurations        | 13, 14, 18, 20, 26, 30           |
| 2d - Terraform State Fundamentals            | 8, 9, 10, 16, 17, 24, 25, 27, 28 |

---

## High-Probability Exam Topics

* Providers
* Provider Plugins
* Provider Source Addresses
* Version Constraints
* terraform init
* terraform init -upgrade
* Provider Aliases
* Multiple Providers
* Terraform State
* Current State vs Desired State
* terraform.tfstate
* State Tracking

---

## Self-Assessment

### 27-30 Correct

Excellent. Domain 2 is exam-ready.

### 23-26 Correct

Strong understanding. Review missed questions.

### 18-22 Correct

Good understanding. Revisit Objectives 2a-2d.

### Below 18 Correct

Review Domain 2 notes completely before proceeding.

---

## Domain Completion Checklist

* [ ] Read 2a - Install and Version Terraform Providers
* [ ] Read 2b - Describe How Terraform Uses Providers
* [ ] Read 2c - Multiple Provider Configurations
* [ ] Read 2d - Terraform State Fundamentals
* [ ] Completed Domain 2 Practice Questions
* [ ] Scored 27+/30
* [ ] Reviewed Incorrect Answers
* [ ] Ready for Domain 3
