# Objective: 7c - Describe When and How to Use Verbose Logging

## Definition

Terraform provides verbose logging capabilities that help troubleshoot:

- Terraform Errors
- Provider Issues
- API Failures
- Authentication Problems
- State Issues
- Backend Problems

Verbose logging is controlled using environment variables.

The most important variable is:

```bash
TF_LOG
```

This objective focuses on understanding:

- Logging Levels
- Debugging Workflows
- Log Files
- Troubleshooting Best Practices

---

## Core Concepts

### Why Logging Exists

Normally Terraform outputs:

```bash
terraform plan
```

Example:

```text
Plan: 2 to add, 0 to change, 0 to destroy
```

This is human-friendly output.

However, it does not show:

- API Requests
- Provider Communication
- Internal Terraform Operations

Verbose logging exposes these details.

---

# TF_LOG

## Definition

Enables Terraform logging.

---

## Syntax

Linux/macOS:

```bash
export TF_LOG=LEVEL
```

Windows PowerShell:

```powershell
$env:TF_LOG="LEVEL"
```

---

## Example

```bash
export TF_LOG=DEBUG
```

Run:

```bash
terraform plan
```

Terraform outputs detailed logs.

---

# Logging Levels

Terraform supports multiple log levels.

---

## TRACE

Highest verbosity.

```bash
export TF_LOG=TRACE
```

Shows:

- Everything
- Internal Operations
- Provider Calls
- API Requests
- State Operations

---

### Use Case

Deep troubleshooting.

---

## DEBUG

Very detailed.

```bash
export TF_LOG=DEBUG
```

Shows:

- Provider Activity
- API Requests
- Internal Execution Flow

---

### Use Case

Most common troubleshooting level.

---

## INFO

General operational information.

```bash
export TF_LOG=INFO
```

Shows:

- Major Events
- Backend Operations
- Resource Processing

---

### Use Case

General diagnostics.

---

## WARN

Warnings only.

```bash
export TF_LOG=WARN
```

Shows:

- Potential Problems
- Warning Messages

---

## ERROR

Errors only.

```bash
export TF_LOG=ERROR
```

Shows:

- Failures
- Critical Issues

---

# Logging Level Hierarchy

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

Higher levels provide more information.

---

# TF_LOG_PATH

## Definition

Stores logs in a file instead of the terminal.

---

## Syntax

Linux/macOS:

```bash
export TF_LOG_PATH=terraform.log
```

---

Example:

```bash
export TF_LOG=DEBUG
```

```bash
export TF_LOG_PATH=terraform.log
```

```bash
terraform apply
```

Logs written to:

```text
terraform.log
```

---

# Logging Workflow

```text
Enable TF_LOG
        │
        ▼
Run Terraform Command
        │
        ▼
Collect Logs
        │
        ▼
Analyze Problem
```

---

# Example Debug Session

Set Logging:

```bash
export TF_LOG=DEBUG
```

Run:

```bash
terraform apply
```

Terraform displays:

```text
Provider Requests
API Calls
Authentication Details
State Operations
```

---

# Troubleshooting Authentication Issues

Example:

```text
AWS Access Denied
```

Enable:

```bash
export TF_LOG=DEBUG
```

Review:

```text
Provider Authentication Flow
```

---

# Troubleshooting Backend Problems

Example:

```text
Failed To Access State
```

Enable:

```bash
export TF_LOG=DEBUG
```

Review:

```text
Backend Operations
```

---

# Troubleshooting Provider Errors

Example:

```text
Provider Returned Error
```

Enable:

```bash
export TF_LOG=TRACE
```

Inspect:

```text
API Requests
API Responses
```

---

# Production Use Cases

Verbose logging is commonly used when:

- Provider Errors Occur
- Backend Issues Occur
- Authentication Fails
- State Problems Exist
- Support Tickets Are Opened

---

# Logging Best Practices

## Enable Only When Needed

Verbose logs generate large amounts of output.

---

## Prefer DEBUG First

Most troubleshooting starts with:

```bash
TF_LOG=DEBUG
```

---

## Use TRACE Carefully

TRACE can generate massive logs.

---

## Disable After Troubleshooting

Example:

Linux/macOS:

```bash
unset TF_LOG
```

Windows PowerShell:

```powershell
Remove-Item Env:TF_LOG
```

---

# Terraform Perspective

Without Logging:

```text
High-Level Output
```

With Logging:

```text
Internal Terraform Operations
```

become visible.

---

# Real-World Example

Engineer receives:

```text
Error Creating VPC
```

Terraform output:

```text
API Error
```

Insufficient information.

Enable:

```bash
TF_LOG=DEBUG
```

Review logs.

Identify:

```text
IAM Permission Failure
```

Resolve issue.

---

# Important Exam Points

- TF_LOG enables Terraform logging.
- TRACE is the most verbose level.
- DEBUG is commonly used for troubleshooting.
- TF_LOG_PATH writes logs to a file.
- Logging helps troubleshoot providers, APIs, authentication, and backends.
- Logging is typically temporary.
- Verbose logging may expose sensitive information.

---

# Common Exam Traps

### Trap 1

Question:

Which variable enables logging?

Correct:

```bash
TF_LOG
```

---

### Trap 2

Question:

Which level is most verbose?

Correct:

```text
TRACE
```

---

### Trap 3

Question:

Which variable writes logs to a file?

Correct:

```bash
TF_LOG_PATH
```

---

### Trap 4

Question:

Which level is commonly used for troubleshooting?

Correct:

```text
DEBUG
```

---

### Trap 5

Question:

Should verbose logging remain enabled permanently?

Correct:

```text
No
```

---

### Trap 6

Question:

Can logs contain sensitive information?

Correct:

```text
Yes
```

---

# Interview Questions

### What does TF_LOG do?

Enables Terraform logging.

### What is the most verbose logging level?

TRACE.

### What logging level is commonly used for troubleshooting?

DEBUG.

### What does TF_LOG_PATH do?

Writes logs to a file.

### Why should logging be disabled after troubleshooting?

To reduce noise and avoid exposing sensitive information.

---

# Practice Questions

### Question 1

Which environment variable enables Terraform logging?

A. TF_DEBUG

B. TF_TRACE

C. TF_LOG

D. TF_OUTPUT

**Answer:** C

---

### Question 2

Which logging level is the most verbose?

A. INFO

B. DEBUG

C. WARN

D. TRACE

**Answer:** D

---

### Question 3

Which environment variable writes logs to a file?

A. TF_FILE

B. TF_LOG_FILE

C. TF_LOG_PATH

D. TF_OUTPUT_PATH

**Answer:** C

---

### Question 4

Which logging level is commonly used during troubleshooting?

A. DEBUG

B. ERROR

C. WARN

D. NONE

**Answer:** A

---

### Question 5

Can Terraform logs contain sensitive information?

A. No

B. Yes

**Answer:** B

---

## Related Objectives

- 6a Local Backend
- 6b State Locking
- 6d State Management
- 7a Import Existing Infrastructure
- 7b State Inspection

---

## Key Takeaways

- `TF_LOG` enables Terraform logging.
- `TRACE` is the most verbose logging level.
- `DEBUG` is the most commonly used troubleshooting level.
- `TF_LOG_PATH` stores logs in a file.
- Logging helps diagnose provider, backend, authentication, and API issues.
- Logs may contain sensitive information.
- Disable verbose logging after troubleshooting.
- Logging concepts are frequently tested in Terraform Associate (004).
