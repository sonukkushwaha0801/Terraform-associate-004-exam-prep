# Domain 7 Revision Sheet

## Maintain Infrastructure with Terraform

### Objectives Covered

- 7a Import Existing Infrastructure Into Your Terraform Workspace
- 7b Use the CLI to Inspect State
- 7c Describe When and How to Use Verbose Logging

---

# Domain Summary

This domain focuses on maintaining and troubleshooting Terraform-managed infrastructure.

Key topics:

- Import Existing Resources
- Inspect Terraform State
- Enable Verbose Logging
- Troubleshoot Terraform Issues

---

# Objective 7a

## Import Existing Infrastructure

### Purpose

Bring existing infrastructure under Terraform management.

---

## Command

```bash
terraform import ADDRESS ID
```

---

## Example

```bash
terraform import aws_instance.web i-123456789
```

---

## Required Inputs

### Resource Address

```text
aws_instance.web
```

### Resource ID

```text
i-123456789
```

---

## Import Workflow

```text
Existing Infrastructure
          │
          ▼
Terraform Configuration
          │
          ▼
terraform import
          │
          ▼
Terraform State Updated
          │
          ▼
Terraform Manages Resource
```

---

## What Import Does

✅ Updates State

✅ Adds Existing Resource To Terraform Management

---

## What Import Does NOT Do

❌ Create Infrastructure

❌ Modify Infrastructure

❌ Generate Terraform Configuration

---

## Most Important Exam Trap

Question:

What does terraform import modify?

Answer:

```text
Terraform State
```

---

# Objective 7b

## Inspect Terraform State

Terraform provides CLI commands for inspecting state.

---

# terraform state list

## Purpose

Lists all resources tracked by state.

---

## Command

```bash
terraform state list
```

---

## Example Output

```text
aws_vpc.main

aws_subnet.public

aws_instance.web
```

---

## Exam Memory

```text
LIST = List Resources
```

---

# terraform state show

## Purpose

Displays detailed information about one resource.

---

## Command

```bash
terraform state show RESOURCE
```

---

## Example

```bash
terraform state show aws_instance.web
```

---

## Exam Memory

```text
SHOW = Single Resource Details
```

---

# terraform show

## Purpose

Displays the complete Terraform state.

---

## Command

```bash
terraform show
```

---

## Exam Memory

```text
terraform show = Entire State
```

---

# State Inspection Comparison

| Command              | Purpose               |
| -------------------- | --------------------- |
| terraform state list | List Resources        |
| terraform state show | Show Resource Details |
| terraform show       | Show Entire State     |

---

# State Inspection Workflow

```text
terraform state list
          │
          ▼
Choose Resource
          │
          ▼
terraform state show
```

---

# Objective 7c

## Verbose Logging

Terraform supports detailed troubleshooting logs.

---

# TF_LOG

## Purpose

Enable Terraform logging.

---

## Linux/macOS

```bash
export TF_LOG=DEBUG
```

---

## PowerShell

```powershell
$env:TF_LOG="DEBUG"
```

---

# Logging Levels

## TRACE

Most verbose.

```text
Maximum Detail
```

---

## DEBUG

Most common troubleshooting level.

```text
Recommended Starting Point
```

---

## INFO

General operational information.

---

## WARN

Warnings only.

---

## ERROR

Errors only.

---

# Logging Hierarchy

```text
TRACE
 ↓
DEBUG
 ↓
INFO
 ↓
WARN
 ↓
ERROR
```

---

# TF_LOG_PATH

## Purpose

Write logs to a file.

---

## Example

```bash
export TF_LOG=DEBUG
```

```bash
export TF_LOG_PATH=terraform.log
```

---

## Result

```text
terraform.log
```

contains all log output.

---

# Common Logging Use Cases

## Authentication Problems

Example:

```text
AWS Access Denied
```

Use:

```bash
TF_LOG=DEBUG
```

---

## Backend Issues

Example:

```text
State Access Failure
```

Use:

```bash
TF_LOG=DEBUG
```

---

## Provider Problems

Example:

```text
API Request Failure
```

Use:

```bash
TF_LOG=TRACE
```

---

# Logging Best Practices

✅ Enable only when troubleshooting

✅ Start with DEBUG

✅ Use TRACE only when necessary

✅ Store logs in files for analysis

✅ Disable logging after troubleshooting

---

# Important Exam Facts

### terraform import updates state.

### Import does not create infrastructure.

### Import does not generate Terraform code.

### terraform state list lists resources.

### terraform state show displays resource details.

### terraform show displays entire state.

### TF_LOG enables logging.

### TRACE is the most verbose level.

### DEBUG is the most common troubleshooting level.

### TF_LOG_PATH writes logs to a file.

### Logs may contain sensitive information.

---

# Top 15 Domain 7 Exam Traps

### 1

Import updates:

```text
State
```

---

### 2

Import does not create resources.

---

### 3

Import does not generate Terraform code.

---

### 4

Import requires:

```text
Address + Resource ID
```

---

### 5

Verify imports using:

```bash
terraform state list
```

---

### 6

Inspect resources using:

```bash
terraform state show
```

---

### 7

Complete state:

```bash
terraform show
```

---

### 8

Logging variable:

```bash
TF_LOG
```

---

### 9

Most verbose logging:

```text
TRACE
```

---

### 10

Most common troubleshooting level:

```text
DEBUG
```

---

### 11

File logging variable:

```bash
TF_LOG_PATH
```

---

### 12

Logs can expose secrets.

---

### 13

Disable logging after troubleshooting.

---

### 14

State inspection commands are read-only.

---

### 15

Domain 7 is primarily about maintenance and troubleshooting.

---

# 60-Second Exam Revision

```bash
terraform import
```

↓

```text
Import Existing Infrastructure
```

---

```text
Import Updates State
```

---

```text
Import ≠ Create Resource
```

---

```text
Import ≠ Generate Code
```

---

```bash
terraform state list
```

↓

```text
List Resources
```

---

```bash
terraform state show
```

↓

```text
Single Resource Details
```

---

```bash
terraform show
```

↓

```text
Entire State
```

---

```bash
TF_LOG
```

↓

```text
Enable Logging
```

---

```text
TRACE
```

↓

```text
Most Verbose
```

---

```text
DEBUG
```

↓

```text
Most Common Troubleshooting Level
```

---

```bash
TF_LOG_PATH
```

↓

```text
Write Logs To File
```

---

# Domain Completion Checklist

- [ ] Completed 7a Import Existing Infrastructure
- [ ] Completed 7b Inspect State
- [ ] Completed 7c Verbose Logging
- [ ] Completed Practice Questions
- [ ] Scored 27+/30
- [ ] Reviewed Incorrect Answers
- [ ] Ready For Domain 8 (HCP Terraform)
