# Terraform Architecture Questions

> Terraform Architecture Interview Preparation
>
> Purpose:
>
> * Senior DevOps Engineer Interviews
> * Cloud Engineer Interviews
> * Infrastructure Architect Interviews
> * Platform Engineer Interviews
> * Terraform Architecture Discussions
>
> Focus:
>
> * System Design
> * Terraform Platform Architecture
> * Governance
> * Security
> * Scalability
> * Multi-Account Design
> * Enterprise Operations
>
> Important:
>
> These questions are intentionally beyond Terraform Associate (004).
>
> They evaluate architectural thinking rather than command memorization.

---

# Section 1 — Environment Architecture

## Question 1

How would you design Terraform architecture for:

* Development
* Staging
* Production

while maintaining strict isolation?

---

## Question 2

Would you use:

* Separate repositories
* Separate directories
* Separate workspaces

for environment management?

Why?

---

## Question 3

How would you promote infrastructure changes from Development to Production?

---

## Question 4

How would you prevent Development engineers from affecting Production infrastructure?

---

## Question 5

How would you structure state files across environments?

---

## Question 6

How would you design Terraform architecture for a regulated environment requiring change approvals?

---

## Question 7

What governance controls would you implement around production deployments?

---

## Question 8

How would you manage environment-specific configuration without duplicating Terraform code?

---

## Question 9

How would you handle secrets differently across environments?

---

## Question 10

What architecture patterns reduce environment drift?

---

# Section 2 — State Architecture

## Question 11

Design a remote-state architecture for:

* Multiple Teams
* Multiple AWS Accounts
* Multiple Environments

---

## Question 12

What risks exist if multiple applications share the same state file?

---

## Question 13

How would you structure Terraform state for hundreds of applications?

---

## Question 14

How would you design state isolation boundaries?

---

## Question 15

How would you recover from state corruption?

---

## Question 16

What backup strategy would you implement for Terraform state?

---

## Question 17

How would you test Terraform state recovery?

---

## Question 18

How would you reduce state blast radius?

---

## Question 19

How would you design state management for a Platform Engineering team?

---

## Question 20

Would you prefer HCP Terraform or S3 + DynamoDB?

Explain trade-offs.

---

# Section 3 — Module Architecture

## Question 21

How would you design reusable Terraform modules for hundreds of teams?

---

## Question 22

How would you organize a module repository?

---

## Question 23

How would you version modules?

---

## Question 24

How would you prevent breaking changes from impacting production environments?

---

## Question 25

How many input variables are too many?

Why?

---

## Question 26

How would you balance flexibility versus standardization in module design?

---

## Question 27

What module anti-patterns have you encountered?

---

## Question 28

How would you design a module approval process?

---

## Question 29

How would you secure shared modules?

---

## Question 30

How would you distribute modules across an enterprise?

---

# Section 4 — Multi-Account AWS Architecture

## Question 31

Design Terraform architecture for:

* 50 AWS Accounts
* Multiple Regions
* Hundreds of Applications

---

## Question 32

How would you organize repositories?

---

## Question 33

How would you structure provider configurations?

---

## Question 34

How would you manage IAM roles for Terraform?

---

## Question 35

How would you implement account-level isolation?

---

## Question 36

How would you manage shared networking across accounts?

---

## Question 37

How would you implement governance consistently across all accounts?

---

## Question 38

How would you manage Terraform deployments across multiple regions?

---

## Question 39

How would you structure CI/CD pipelines for multi-account deployments?

---

## Question 40

How would you audit infrastructure changes across all accounts?

---

# Section 5 — Governance Architecture

## Question 41

How would you implement Policy-as-Code?

---

## Question 42

What Sentinel policies would you enforce organization-wide?

---

## Question 43

How would you enforce mandatory tagging?

---

## Question 44

How would you prevent insecure infrastructure from being deployed?

---

## Question 45

How would you enforce encryption requirements?

---

## Question 46

How would you integrate security scanning into Terraform workflows?

---

## Question 47

How would you design Terraform approval workflows?

---

## Question 48

How would you balance deployment velocity with governance?

---

## Question 49

How would you implement least privilege for Terraform users?

---

## Question 50

How would you design Terraform governance for regulated industries?

---

# Section 6 — Platform Engineering

## Question 51

How would you build an Internal Developer Platform using Terraform?

---

## Question 52

What Terraform abstractions should developers see?

---

## Question 53

What Terraform complexity should be hidden from developers?

---

## Question 54

How would developers request infrastructure?

---

## Question 55

How would you implement self-service infrastructure?

---

## Question 56

How would you maintain governance while enabling self-service?

---

## Question 57

How would you design Terraform products instead of Terraform projects?

---

## Question 58

How would you onboard hundreds of teams onto a Terraform platform?

---

## Question 59

What platform metrics would you track?

---

## Question 60

How would you evolve the platform over time?

---

# Section 7 — Security Architecture

## Question 61

How would you manage secrets in Terraform at enterprise scale?

---

## Question 62

Would you use Vault?

Why or why not?

---

## Question 63

How would you implement secret rotation?

---

## Question 64

How would you prevent secrets from entering Git repositories?

---

## Question 65

How would you secure Terraform state?

---

## Question 66

How would you audit access to Terraform infrastructure?

---

## Question 67

How would you secure Terraform pipelines?

---

## Question 68

How would you implement break-glass access procedures?

---

## Question 69

How would you respond to a secret exposure incident?

---

## Question 70

How would you design Terraform security controls for a large enterprise?

---

# Section 8 — Disaster Recovery & Operations

## Question 71

How would you design disaster recovery for Terraform state?

---

## Question 72

What is your recovery procedure if Terraform state is lost?

---

## Question 73

How would you recover from accidental resource deletion?

---

## Question 74

How would you recover from a failed production deployment?

---

## Question 75

How would you handle large-scale drift across environments?

---

## Question 76

How would you design rollback strategies for Terraform?

---

## Question 77

How would you audit six months of infrastructure changes?

---

## Question 78

How would you design operational runbooks for Terraform?

---

## Question 79

What Terraform metrics should operations teams monitor?

---

## Question 80

How would you improve Terraform operational maturity?

---

# Section 9 — Architecture Review Questions

## Question 81

Review a Terraform platform where every application uses a shared state file. What problems do you identify?

---

## Question 82

Review a Terraform architecture where all engineers have production apply permissions. What risks exist?

---

## Question 83

Review a Terraform platform with no module versioning strategy.

What could go wrong?

---

## Question 84

Review an architecture where Terraform state is stored locally.

Would you approve it?

Why or why not?

---

## Question 85

Review a Terraform environment where production changes bypass pull requests.

What governance issues exist?

---

## Question 86

Review a Terraform platform that uses copy-pasted infrastructure rather than modules.

What long-term problems emerge?

---

## Question 87

Review a Terraform deployment process with no policy enforcement.

What risks exist?

---

## Question 88

Review an environment where developers can directly modify cloud infrastructure.

How would you redesign it?

---

## Question 89

Review a Terraform organization with no disaster recovery strategy.

What improvements would you recommend?

---

## Question 90

Review a Terraform platform and identify its likely operational bottlenecks.

---

# Section 10 — Senior-Level Discussion Questions

## Question 91

What separates a Terraform user from a Terraform architect?

---

## Question 92

What Terraform design decisions scale well?

---

## Question 93

What Terraform design decisions fail at scale?

---

## Question 94

What would your ideal enterprise Terraform platform look like?

---

## Question 95

How would you design Terraform for a Fortune 500 organization?

---

## Question 96

How would Platform Engineering change Terraform adoption?

---

## Question 97

What Terraform governance controls provide the highest value?

---

## Question 98

How should Terraform evolve as organizations grow?

---

## Question 99

What lessons have you learned from Terraform architecture failures?

---

## Question 100

If starting from scratch today, how would you architect Terraform across an entire enterprise?

---

# Architecture Readiness Assessment

| Score  | Assessment                |
| ------ | ------------------------- |
| 0–20   | Terraform Fundamentals    |
| 21–40  | Terraform Practitioner    |
| 41–60  | Infrastructure Engineer   |
| 61–80  | Senior Terraform Engineer |
| 81–95  | Platform Engineer         |
| 96–100 | Terraform Architect       |
