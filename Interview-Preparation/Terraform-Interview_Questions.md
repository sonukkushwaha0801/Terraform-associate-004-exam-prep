# Terraform Interview Questions

> Terraform Interview Preparation Guide
>
> Purpose:
>
> * Terraform Associate (004) Interview Preparation
> * DevOps Engineer Interviews
> * Cloud Engineer Interviews
> * Infrastructure Engineer Interviews
> * Platform Engineer Interviews
>
> Difficulty Levels:
>
> * Foundation
> * Intermediate
> * Advanced
> * Senior-Level Discussion
>
> Recommendation:
>
> Do not memorize answers.
> Focus on explaining concepts, trade-offs, architecture decisions, and production use cases.

---

# Section 1 — Terraform Fundamentals

### Question 1

What is Terraform?

---

### Question 2

How does Terraform differ from traditional infrastructure provisioning?

---

### Question 3

What is Infrastructure as Code (IaC)?

---

### Question 4

What problems does IaC solve?

---

### Question 5

Why is Terraform considered declarative?

---

### Question 6

What is desired state?

---

### Question 7

What is actual state?

---

### Question 8

How does Terraform reconcile desired state and actual state?

---

### Question 9

What are Terraform providers?

---

### Question 10

Why are providers required?

---

### Question 11

How does Terraform interact with AWS?

---

### Question 12

Can Terraform manage non-cloud resources?

Provide examples.

---

### Question 13

What is service-agnostic infrastructure automation?

---

### Question 14

How does Terraform support multi-cloud deployments?

---

### Question 15

How does Terraform support hybrid-cloud environments?

---

# Section 2 — Terraform Configuration

### Question 16

What is a Terraform resource?

---

### Question 17

What is a Terraform data source?

---

### Question 18

What is the difference between a resource block and a data block?

---

### Question 19

When would you use a data source instead of a resource?

---

### Question 20

Explain Terraform variables.

---

### Question 21

Explain Terraform outputs.

---

### Question 22

What are Terraform local values?

---

### Question 23

What Terraform data types have you used?

---

### Question 24

Difference between:

* list
* set
* map

---

### Question 25

Difference between:

* object
* tuple

---

### Question 26

Explain count.

---

### Question 27

Explain for_each.

---

### Question 28

When should for_each be preferred over count?

---

### Question 29

What Terraform functions do you frequently use?

---

### Question 30

Explain dynamic blocks.

---

### Question 31

How do expressions improve Terraform configurations?

---

### Question 32

What are Terraform conditional expressions?

---

### Question 33

What is variable validation?

---

### Question 34

Why is variable validation important?

---

### Question 35

What are preconditions and postconditions?

---

# Section 3 — Terraform Workflow

### Question 36

Explain the complete Terraform workflow.

---

### Question 37

What happens during terraform init?

---

### Question 38

What happens during terraform validate?

---

### Question 39

What happens during terraform plan?

---

### Question 40

What happens during terraform apply?

---

### Question 41

Why should execution plans always be reviewed?

---

### Question 42

What information appears in a Terraform plan?

---

### Question 43

What does terraform destroy do?

---

### Question 44

What is terraform fmt?

---

### Question 45

Why should code formatting be enforced?

---

# Section 4 — State Management

### Question 46

What is Terraform State?

---

### Question 47

Why does Terraform require state?

---

### Question 48

What information is stored in state?

---

### Question 49

Where is state stored by default?

---

### Question 50

Why should local state be avoided in teams?

---

### Question 51

What is a backend?

---

### Question 52

Difference between local and remote backends.

---

### Question 53

What is state locking?

---

### Question 54

Why is state locking important?

---

### Question 55

What happens if state locking is not implemented?

---

### Question 56

How does Terraform detect configuration drift?

---

### Question 57

What causes resource drift?

---

### Question 58

How would you handle drift in production?

---

### Question 59

What risks exist when editing state manually?

---

### Question 60

When would terraform state commands be necessary?

---

# Section 5 — Terraform Modules

### Question 61

What is a Terraform module?

---

### Question 62

Why use modules?

---

### Question 63

Difference between root module and child module.

---

### Question 64

How do modules improve maintainability?

---

### Question 65

How do modules improve standardization?

---

### Question 66

Where can modules be sourced from?

---

### Question 67

How do you version modules?

---

### Question 68

Why should module versions be pinned?

---

### Question 69

How do modules communicate with one another?

---

### Question 70

How are outputs used within modules?

---

### Question 71

Can child modules directly access root variables?

Why or why not?

---

### Question 72

What challenges have you encountered with module design?

---

# Section 6 — Security & Secrets

### Question 73

How should secrets be managed in Terraform?

---

### Question 74

What risks exist when storing secrets in code?

---

### Question 75

What does sensitive = true do?

---

### Question 76

Does sensitive prevent state storage?

---

### Question 77

Why is secret management still required if variables are sensitive?

---

### Question 78

What role does Vault play in Terraform?

---

### Question 79

How does Vault improve security?

---

### Question 80

What security controls should protect Terraform state?

---

# Section 7 — Terraform CLI & Troubleshooting

### Question 81

How do you inspect Terraform state?

---

### Question 82

What is terraform state list?

---

### Question 83

What is terraform state show?

---

### Question 84

What is terraform import?

---

### Question 85

Does terraform import create configuration?

---

### Question 86

What challenges occur after importing resources?

---

### Question 87

How do you troubleshoot Terraform failures?

---

### Question 88

What is TF_LOG?

---

### Question 89

What log levels does Terraform support?

---

### Question 90

When should TRACE logging be used?

---

# Section 8 — HCP Terraform

### Question 91

What is HCP Terraform?

---

### Question 92

What problems does HCP Terraform solve?

---

### Question 93

What is a Workspace?

---

### Question 94

What is a Project?

---

### Question 95

Difference between Projects and Workspaces.

---

### Question 96

What are remote runs?

---

### Question 97

What are speculative plans?

---

### Question 98

How does VCS integration work?

---

### Question 99

Why use GitHub integration?

---

### Question 100

What are Run Tasks?

---

### Question 101

What is Sentinel?

---

### Question 102

How does Sentinel improve governance?

---

### Question 103

What is Policy-as-Code?

---

### Question 104

How does HCP Terraform manage state?

---

### Question 105

What security benefits does HCP Terraform provide?

---

# Advanced Discussion Questions

### Question 106

How would you structure Terraform for:

* Development
* Staging
* Production

environments?

---

### Question 107

How would you organize Terraform repositories for a large enterprise?

---

### Question 108

How would you design reusable Terraform modules for hundreds of teams?

---

### Question 109

How would you implement governance across multiple cloud accounts?

---

### Question 110

How would you prevent configuration drift at scale?

---

### Question 111

How would you implement disaster recovery for Terraform state?

---

### Question 112

How would you migrate from manually created infrastructure to Terraform?

---

### Question 113

How would you manage Terraform in a multi-account AWS environment?

---

### Question 114

How would you secure Terraform pipelines?

---

### Question 115

How would you audit Terraform deployments?

---

### Question 116

What Terraform anti-patterns have you seen?

---

### Question 117

What Terraform design decisions improve maintainability?

---

### Question 118

How would you review a Terraform pull request?

---

### Question 119

What Terraform practices separate junior and senior engineers?

---

### Question 120

If given a greenfield cloud environment, how would you architect the Terraform platform?

---

# Rapid-Fire Interview Round

Answer each in under 30 seconds.

### Question 121

What command initializes Terraform?

---

### Question 122

What command validates configuration?

---

### Question 123

What command previews changes?

---

### Question 124

What command deploys changes?

---

### Question 125

What command destroys infrastructure?

---

### Question 126

What file stores state by default?

---

### Question 127

What file locks provider versions?

---

### Question 128

What command imports resources?

---

### Question 129

What command lists state resources?

---

### Question 130

What command shows resource details?

---

### Question 131

What command opens the Terraform console?

---

### Question 132

What command formats code?

---

### Question 133

What command displays outputs?

---

### Question 134

What feature prevents concurrent state modification?

---

### Question 135

What governance framework exists in HCP Terraform?

---

# Self-Assessment Scorecard

| Score   | Evaluation                    |
| ------- | ----------------------------- |
| 0–40    | Beginner                      |
| 41–70   | Developing                    |
| 71–95   | Associate Ready               |
| 96–115  | Strong Terraform Practitioner |
| 116–135 | Interview Ready               |
| 135+    | Senior-Level Discussion Ready |

---

