# Core Terraform Workflow

This domain covers the day-to-day Terraform workflow used to provision, modify, validate, and destroy infrastructure.

Understanding this workflow is critical because nearly every Terraform deployment follows the same lifecycle:

```text
Write → Init → Validate → Plan → Apply
```

HashiCorp heavily tests workflow commands, their purpose, execution order, and expected outcomes.

---

## Objectives

### 3a - Describe the Terraform Workflow

Understand the complete Terraform workflow from configuration creation to infrastructure deployment and management.

### 3b - Initialize a Terraform Working Directory

Learn how Terraform initializes a project, downloads providers, installs modules, and configures backends.

### 3c - Validate a Terraform Configuration

Understand how Terraform validates configuration syntax and internal consistency.

### 3d - Generate and Review an Execution Plan for Terraform

Learn how Terraform compares current state and desired state to generate an execution plan.

### 3e - Apply Changes to Infrastructure with Terraform

Understand how Terraform creates, updates, and manages infrastructure resources.

### 3f - Destroy Terraform-Managed Infrastructure

Learn how Terraform safely removes managed resources.

### 3g - Apply Formatting and Style Adjustments to a Configuration

Understand Terraform formatting standards and automated code formatting.

---

## Learning Outcomes

After completing this domain, you should be able to:

* Explain the Terraform workflow
* Initialize a Terraform project
* Validate Terraform configurations
* Generate execution plans
* Review planned infrastructure changes
* Apply infrastructure changes
* Destroy infrastructure safely
* Format Terraform code consistently
* Understand command sequencing
* Troubleshoot common workflow issues

---

## Objectives Covered

| Objective                                     | Status |
| --------------------------------------------- | ------ |
| 3a - Describe the Terraform Workflow          | ⬜      |
| 3b - Initialize a Terraform Working Directory | ⬜      |
| 3c - Validate a Terraform Configuration       | ⬜      |
| 3d - Generate and Review an Execution Plan    | ⬜      |
| 3e - Apply Changes to Infrastructure          | ⬜      |
| 3f - Destroy Terraform-Managed Infrastructure | ⬜      |
| 3g - Apply Formatting and Style Adjustments   | ⬜      |

---

## Recommended Study Order

1. Terraform Workflow Overview
2. terraform init
3. terraform validate
4. terraform plan
5. terraform apply
6. terraform destroy
7. terraform fmt

---

## Terraform Workflow Diagram

```text
Write Configuration
        │
        ▼
terraform init
        │
        ▼
terraform validate
        │
        ▼
terraform plan
        │
        ▼
terraform apply
        │
        ▼
Infrastructure Running
        │
        ▼
terraform destroy
```

---

## Exam Focus Areas

Pay special attention to:

* terraform init
* terraform validate
* terraform plan
* terraform apply
* terraform destroy
* terraform fmt
* Command order
* Plan vs Apply
* Validation vs Formatting
* Infrastructure lifecycle

---

## High-Probability Exam Questions

HashiCorp frequently tests:

* Which command downloads providers?
* Which command generates an execution plan?
* Which command applies infrastructure changes?
* Which command validates configuration?
* Which command formats configuration?
* Which command destroys infrastructure?
* Correct Terraform workflow order

---

## Completion Checklist

* [ ] Completed 3a
* [ ] Completed 3b
* [ ] Completed 3c
* [ ] Completed 3d
* [ ] Completed 3e
* [ ] Completed 3f
* [ ] Completed 3g
* [ ] Reviewed practice questions
* [ ] Completed hands-on examples
* [ ] Completed domain revision sheet
* [ ] Ready for Domain 4
