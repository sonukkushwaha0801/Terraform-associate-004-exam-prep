# Domain 6 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 4
- Total Questions: 40

---

# Objective Coverage

| Objective                   | Questions                                       |
| --------------------------- | ----------------------------------------------- |
| 6a Local Backend            | 1,2,3,4,5,6,16,31                               |
| 6b State Locking            | 8,9,10,17,27,28,38,40                           |
| 6c Remote State             | 7,18,19,26,29,32,37,39                          |
| 6d Drift & State Management | 11,12,13,14,15,20,21,22,23,24,25,30,33,34,35,36 |

---

# Answer Key

| Q   | Ans | Q   | Ans | Q   | Ans | Q   | Ans |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | B   | 11  | B   | 21  | C   | 31  | B   |
| 2   | C   | 12  | C   | 22  | A   | 32  | B   |
| 3   | C   | 13  | C   | 23  | B   | 33  | B   |
| 4   | B   | 14  | A   | 24  | B   | 34  | B   |
| 5   | C   | 15  | B   | 25  | C   | 35  | B   |
| 6   | B   | 16  | C   | 26  | B   | 36  | A   |
| 7   | A   | 17  | C   | 27  | B   | 37  | C   |
| 8   | B   | 18  | B   | 28  | B   | 38  | B   |
| 9   | B   | 19  | B   | 29  | B   | 39  | B   |
| 10  | C   | 20  | B   | 30  | B   | 40  | B   |

---

# Detailed Explanations

## Question 1

**Answer:** B

Terraform state tracks infrastructure resources managed by Terraform.

Without state, Terraform cannot determine:

- Existing Resources
- Resource IDs
- Infrastructure Changes

---

## Question 2

**Answer:** C

Terraform automatically uses:

```text
Local Backend
```

when no backend is configured.

---

## Question 3

**Answer:** C

State is stored in:

```text
terraform.tfstate
```

---

## Question 4

**Answer:** B

Backup state file:

```text
terraform.tfstate.backup
```

contains the previous version of state.

---

## Question 5

**Answer:** C

Backends determine:

```text
Where State Is Stored
```

---

## Question 6

**Answer:** B

Terraform needs state to track infrastructure and compare:

```text
Desired State
vs
Current State
```

---

## Question 7

**Answer:** A

Remote backends store state outside the local machine.

Examples:

- S3
- AzureRM
- GCS
- HCP Terraform

---

## Question 8

**Answer:** B

State locking prevents:

```text
Concurrent State Modifications
```

---

## Question 9

**Answer:** B

Terraform acquires locks before modifying state.

---

## Question 10

**Answer:** C

Terraform releases locks after operation completion.

---

## Question 11

**Answer:** B

Resource drift occurs when infrastructure changes outside Terraform.

Examples:

- AWS Console
- Azure Portal
- Manual CLI Changes

---

## Question 12

**Answer:** C

Drift is commonly detected using:

```bash
terraform plan
```

---

## Question 13

**Answer:** C

Lists resources tracked by state:

```bash
terraform state list
```

---

## Question 14

**Answer:** A

Displays resource details:

```bash
terraform state show
```

---

## Question 15

**Answer:** B

Imports existing infrastructure:

```bash
terraform import
```

---

## Question 16

**Answer:** C

State stored on a laptop indicates:

```text
Local Backend
```

---

## Question 17

**Answer:** C

State locking prevents simultaneous updates to the same state.

---

## Question 18

**Answer:** B

Team collaboration requires:

```text
Remote Backend
```

---

## Question 19

**Answer:** B

S3 is a remote backend.

---

## Question 20

**Answer:** B

Manual console modification causes:

```text
Resource Drift
```

---

## Question 21

**Answer:** C

Command:

```bash
terraform state list
```

lists tracked resources.

---

## Question 22

**Answer:** A

Command:

```bash
terraform state show
```

shows resource details.

---

## Question 23

**Answer:** B

Command:

```bash
terraform state mv
```

moves resources within state.

---

## Question 24

**Answer:** B

Command:

```bash
terraform state rm
```

removes tracking only.

Infrastructure remains untouched.

---

## Question 25

**Answer:** C

Existing resources are brought under Terraform using:

```bash
terraform import
```

---

## Question 26

**Answer:** B

Backend initialization and migration:

```bash
terraform init
```

---

## Question 27

**Answer:** B

Another Terraform operation is likely holding the lock.

---

## Question 28

**Answer:** B

Stale lock removal:

```bash
terraform force-unlock
```

---

## Question 29

**Answer:** B

Remote backend provides:

- Centralization
- Collaboration
- Locking

---

## Question 30

**Answer:** B

Terraform is detecting:

```text
Resource Drift
```

---

## Question 31

**Answer:** B

Default backend:

```text
Local Backend
```

---

## Question 32

**Answer:** B

Terraform supports only:

```text
One Backend
```

per configuration.

---

## Question 33

**Answer:** B

```bash
terraform state rm
```

does NOT delete infrastructure.

Only state changes.

---

## Question 34

**Answer:** B

Import updates state.

It does NOT generate Terraform configuration files.

---

## Question 35

**Answer:** B

Import primarily updates:

```text
Terraform State
```

---

## Question 36

**Answer:** A

State files may contain:

- Secrets
- Passwords
- Tokens
- Metadata

Protect state files carefully.

---

## Question 37

**Answer:** C

After backend configuration changes:

```bash
terraform init
```

must be executed again.

---

## Question 38

**Answer:** B

Correct command:

```bash
terraform force-unlock
```

---

## Question 39

**Answer:** B

Most important remote-state benefit:

```text
Team Collaboration
```

---

## Question 40

**Answer:** B

State locking prevents concurrent modifications.

---

# State Commands Cheat Sheet

## List Resources

```bash
terraform state list
```

---

## Show Resource Details

```bash
terraform state show RESOURCE
```

Example:

```bash
terraform state show aws_instance.web
```

---

## Move State Entry

```bash
terraform state mv SOURCE DESTINATION
```

Example:

```bash
terraform state mv aws_instance.web aws_instance.app
```

---

## Remove Resource From State

```bash
terraform state rm RESOURCE
```

Example:

```bash
terraform state rm aws_instance.web
```

---

## Import Existing Infrastructure

```bash
terraform import ADDRESS ID
```

Example:

```bash
terraform import aws_instance.web i-123456
```

---

## Remove Stale Lock

```bash
terraform force-unlock LOCK_ID
```

---

# Drift Detection Summary

## Drift Definition

Infrastructure differs from:

```text
Terraform Configuration
```

or

```text
Terraform State
```

---

## Common Causes

- Console Changes
- Manual CLI Changes
- Third-Party Automation
- Resource Deletion

---

## Detection Command

```bash
terraform plan
```

---

## Correction

```bash
terraform apply
```

or update configuration.

---

# Local vs Remote Backend

| Feature               | Local   | Remote |
| --------------------- | ------- | ------ |
| Shared State          | ❌       | ✅      |
| Team Collaboration    | ❌       | ✅      |
| Centralized Storage   | ❌       | ✅      |
| State Locking         | Limited | ✅      |
| Production Ready      | ❌       | ✅      |
| Disaster Recovery     | Weak    | Strong |
| Recommended For Teams | ❌       | ✅      |


# Exam Readiness Score

### 35-40 Correct

Domain 6 Exam Ready

### 30-34 Correct

Strong Understanding

### 24-29 Correct

Review State Commands and Drift Concepts

### Below 24 Correct

Re-read Domain 6 Theory and Retake Questions
