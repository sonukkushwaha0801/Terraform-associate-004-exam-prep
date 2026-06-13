# Domain 7 Practice Questions

## Maintain Infrastructure with Terraform

### Domain Statistics

- Objectives Covered: 3
- Total Questions: 30
- Conceptual Questions: 10
- Scenario-Based Questions: 10
- HashiCorp Exam-Trap Questions: 10

---

# Instructions

Attempt all questions before checking answers.

✅ Record answers separately.

✅ Complete all questions before reviewing explanations.

✅ Passing Target: 27+/30

---

# Conceptual Questions

### Question 1

What is the primary purpose of `terraform import`?

A. Create Infrastructure

B. Import Existing Infrastructure Into Terraform State

C. Delete Infrastructure

D. Upgrade Providers

---

### Question 2

What does `terraform import` primarily modify?

A. Infrastructure

B. Providers

C. Terraform State

D. Modules

---

### Question 3

Which command lists all resources tracked in Terraform state?

A. terraform show

B. terraform state show

C. terraform state list

D. terraform inspect

---

### Question 4

Which command displays detailed information about a specific resource?

A. terraform state show

B. terraform state list

C. terraform show

D. terraform output

---

### Question 5

Which command displays the complete Terraform state?

A. terraform graph

B. terraform show

C. terraform inspect

D. terraform output

---

### Question 6

Which environment variable enables Terraform verbose logging?

A. TF_DEBUG

B. TF_TRACE

C. TF_LOG

D. TF_LOGGING

---

### Question 7

Which logging level provides the most detailed output?

A. INFO

B. DEBUG

C. WARN

D. TRACE

---

### Question 8

Which environment variable writes Terraform logs to a file?

A. TF_LOG_FILE

B. TF_FILE

C. TF_LOG_PATH

D. TF_OUTPUT_PATH

---

### Question 9

What logging level is most commonly used for troubleshooting?

A. TRACE

B. DEBUG

C. WARN

D. ERROR

---

### Question 10

Can Terraform logs contain sensitive information?

A. No

B. Yes

---

# Scenario-Based Questions

### Question 11

A company adopts Terraform after manually creating infrastructure for several years.

Which Terraform feature should be used first?

A. terraform destroy

B. terraform import

C. terraform fmt

D. terraform validate

---

### Question 12

An engineer wants Terraform to manage an existing EC2 instance.

Which command should be used?

A. terraform apply

B. terraform init

C. terraform import

D. terraform show

---

### Question 13

An engineer imports:

```bash
terraform import aws_instance.web i-123456
```

How can they verify the resource exists in state?

A.

```bash
terraform validate
```

B.

```bash
terraform state list
```

C.

```bash
terraform graph
```

D.

```bash
terraform fmt
```

---

### Question 14

An engineer wants to view all attributes of:

```text
aws_instance.web
```

Which command should be used?

A.

```bash
terraform show
```

B.

```bash
terraform state list
```

C.

```bash
terraform state show aws_instance.web
```

D.

```bash
terraform output
```

---

### Question 15

An engineer wants a complete view of the current Terraform state.

Which command should be used?

A.

```bash
terraform state show
```

B.

```bash
terraform output
```

C.

```bash
terraform show
```

D.

```bash
terraform graph
```

---

### Question 16

Terraform returns an authentication error from AWS.

Which logging level is typically enabled first?

A. ERROR

B. WARN

C. DEBUG

D. NONE

---

### Question 17

Terraform logs should be written to a file for investigation.

Which variable should be configured?

A. TF_FILE

B. TF_LOG_PATH

C. TF_OUTPUT

D. TF_LOG_FILE

---

### Question 18

A support engineer requests maximum logging detail.

Which level should be enabled?

A. INFO

B. DEBUG

C. WARN

D. TRACE

---

### Question 19

A team wants to troubleshoot provider API requests.

Which Terraform feature should be used?

A. Outputs

B. Verbose Logging

C. Modules

D. Workspaces

---

### Question 20

An imported resource appears incorrect.

Which command should be used to inspect its state details?

A.

```bash
terraform state show
```

B.

```bash
terraform validate
```

C.

```bash
terraform graph
```

D.

```bash
terraform fmt
```

---

# HashiCorp Exam-Trap Questions

### Question 21

Does `terraform import` create infrastructure?

A. Yes

B. No

---

### Question 22

Does `terraform import` generate Terraform configuration?

A. Yes

B. No

---

### Question 23

What information is required for `terraform import`?

A. Provider Name Only

B. Resource Address and Resource ID

C. Module Name

D. Output Name

---

### Question 24

What does `terraform state list` display?

A. Resource Details

B. Provider Versions

C. Resources Tracked In State

D. Variables

---

### Question 25

What does `terraform state show` display?

A. Resource Details

B. Entire State

C. Provider Configuration

D. Variables

---

### Question 26

What does `terraform show` display?

A. Single Resource

B. Entire Terraform State

C. Provider Information

D. Variables Only

---

### Question 27

Which variable enables Terraform logging?

A. TF_DEBUG

B. TF_LOG

C. TF_TRACE

D. TF_VERBOSE

---

### Question 28

Which logging level is most verbose?

A. INFO

B. DEBUG

C. TRACE

D. WARN

---

### Question 29

Should verbose logging remain permanently enabled in production?

A. Yes

B. No

---

### Question 30

Which statement is TRUE?

A. terraform import creates infrastructure.

B. terraform state list displays resource details.

C. terraform state show displays detailed resource information.

D. TF_LOG_PATH enables logging.

---

# Domain 7 Coverage Matrix

| Objective                | Questions                          |
| ------------------------ | ---------------------------------- |
| 7a Import Infrastructure | 1,2,11,12,13,21,22,23              |
| 7b Inspect State         | 3,4,5,14,15,20,24,25,26            |
| 7c Verbose Logging       | 6,7,8,9,10,16,17,18,19,27,28,29,30 |

---

# Self-Assessment

### 27-30 Correct

Excellent. Domain 7 is exam-ready.

### 23-26 Correct

Strong understanding. Review missed explanations.

### 18-22 Correct

Good foundation. Review import and logging concepts.

### Below 18 Correct

Re-read Domain 7 notes before moving forward.

---

# Domain Completion Checklist

- [ ] Read 7a - Import Existing Infrastructure
- [ ] Read 7b - Inspect State
- [ ] Read 7c - Verbose Logging
- [ ] Completed Domain 7 Practice Questions
- [ ] Scored 27+/30
- [ ] Reviewed Incorrect Answers
- [ ] Ready for Domain 8
