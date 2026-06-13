# Domain 7 Practice Questions - Answers

## Domain Statistics

- Objectives Covered: 3
- Total Questions: 30

---

# Objective Coverage

| Objective                | Questions                          |
| ------------------------ | ---------------------------------- |
| 7a Import Infrastructure | 1,2,11,12,13,21,22,23              |
| 7b Inspect State         | 3,4,5,14,15,20,24,25,26            |
| 7c Verbose Logging       | 6,7,8,9,10,16,17,18,19,27,28,29,30 |

---

# Answer Key

| Q   | Ans | Q   | Ans | Q   | Ans |
| --- | --- | --- | --- | --- | --- |
| 1   | B   | 11  | B   | 21  | B   |
| 2   | C   | 12  | C   | 22  | B   |
| 3   | C   | 13  | B   | 23  | B   |
| 4   | A   | 14  | C   | 24  | C   |
| 5   | B   | 15  | C   | 25  | A   |
| 6   | C   | 16  | C   | 26  | B   |
| 7   | D   | 17  | B   | 27  | B   |
| 8   | C   | 18  | D   | 28  | C   |
| 9   | B   | 19  | B   | 29  | B   |
| 10  | B   | 20  | A   | 30  | C   |

---

# Detailed Explanations

## Question 1

**Answer:** B

Terraform import is used to bring existing infrastructure under Terraform management.

Example:

```bash
terraform import aws_instance.web i-123456
```

---

## Question 2

**Answer:** C

Import modifies:

```text
Terraform State
```

It does not modify infrastructure.

---

## Question 3

**Answer:** C

Lists resources tracked by state:

```bash
terraform state list
```

---

## Question 4

**Answer:** A

Displays detailed information about a resource:

```bash
terraform state show
```

---

## Question 5

**Answer:** B

Displays complete Terraform state:

```bash
terraform show
```

---

## Question 6

**Answer:** C

Terraform logging variable:

```bash
TF_LOG
```

---

## Question 7

**Answer:** D

Most verbose logging level:

```text
TRACE
```

---

## Question 8

**Answer:** C

Write logs to file:

```bash
TF_LOG_PATH
```

---

## Question 9

**Answer:** B

Most troubleshooting begins with:

```text
DEBUG
```

---

## Question 10

**Answer:** B

Logs may contain:

- Secrets
- Tokens
- Credentials
- API Responses

---

## Question 11

**Answer:** B

Existing infrastructure should first be imported into Terraform state.

---

## Question 12

**Answer:** C

Command:

```bash
terraform import
```

brings existing infrastructure under Terraform management.

---

## Question 13

**Answer:** B

Verify imported resources using:

```bash
terraform state list
```

---

## Question 14

**Answer:** C

Inspect imported resource:

```bash
terraform state show aws_instance.web
```

---

## Question 15

**Answer:** C

Entire state:

```bash
terraform show
```

---

## Question 16

**Answer:** C

Recommended first troubleshooting level:

```text
DEBUG
```

---

## Question 17

**Answer:** B

Log file location:

```bash
TF_LOG_PATH
```

---

## Question 18

**Answer:** D

Maximum logging:

```text
TRACE
```

---

## Question 19

**Answer:** B

Verbose logging helps troubleshoot:

- Providers
- APIs
- Authentication
- Backends

---

## Question 20

**Answer:** A

Inspect imported resource:

```bash
terraform state show
```

---

## Question 21

**Answer:** B

Import does NOT create infrastructure.

Resource already exists.

---

## Question 22

**Answer:** B

Import does NOT generate Terraform configuration.

Most common exam trap.

---

## Question 23

**Answer:** B

Required:

```text
Resource Address
+
Resource ID
```

---

## Question 24

**Answer:** C

Lists tracked resources.

Example:

```text
aws_vpc.main
aws_instance.web
```

---

## Question 25

**Answer:** A

Displays resource attributes:

```bash
terraform state show
```

---

## Question 26

**Answer:** B

Displays complete state information.

Command:

```bash
terraform show
```

---

## Question 27

**Answer:** B

Logging enabled by:

```bash
TF_LOG
```

---

## Question 28

**Answer:** C

Highest verbosity:

```text
TRACE
```

---

## Question 29

**Answer:** B

Disable verbose logging after troubleshooting.

Reason:

- Noise
- Large Logs
- Sensitive Data Exposure

---

## Question 30

**Answer:** C

Correct statement:

```text
terraform state show
```

displays detailed resource information.

---

# Exam Readiness Score

### 27-30 Correct

Domain 7 Exam Ready

### 23-26 Correct

Strong Understanding

### 18-22 Correct

Review Import and Logging Concepts

### Below 18 Correct

Re-read Domain 7 Theory and Retake Questions
