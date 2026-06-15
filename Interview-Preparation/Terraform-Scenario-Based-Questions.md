# Terraform Scenario-Based Questions

> Terraform Scenario Interview Preparation
>
> Purpose:
>
> * Terraform Associate (004) Reinforcement
> * DevOps Interview Preparation
> * Cloud Engineer Interview Preparation
> * Infrastructure Engineer Interview Preparation
> * Platform Engineering Discussions
>
> Focus:
>
> * Real-world Terraform scenarios
> * Troubleshooting situations
> * State management decisions
> * Module design challenges
> * Security and governance scenarios
> * HCP Terraform use cases
>
> Important:
>
> Do not memorize answers.
>
> Focus on:
>
> * Problem analysis
> * Trade-offs
> * Risk identification
> * Operational decisions
> * Architecture thinking

---

# Section 1 — Infrastructure as Code Scenarios

## Scenario 1

Your organization provisions AWS infrastructure manually through the AWS Console.

Different engineers create resources differently.

Production and staging environments are inconsistent.

### Questions

1. What problems do you identify?
2. How would Terraform solve them?
3. What risks exist during migration?
4. How would you execute the migration?

---

## Scenario 2

A development team requests infrastructure in AWS while another team uses Azure.

Management wants a common provisioning process.

### Questions

1. How can Terraform support this requirement?
2. What Terraform features enable multi-cloud deployments?
3. What governance concerns exist?
4. How would you structure repositories?

---

## Scenario 3

An engineer manually changes a security group rule in production.

Terraform code is not updated.

### Questions

1. What problem has occurred?
2. How would Terraform detect it?
3. What risks exist?
4. How would you resolve it?

---

# Section 2 — Terraform Workflow Scenarios

## Scenario 4

A junior engineer runs:

```bash
terraform apply
```

without reviewing a plan.

Production resources are unexpectedly destroyed.

### Questions

1. What process failure occurred?
2. What controls should exist?
3. How can Terraform reduce this risk?
4. What review process would you implement?

---

## Scenario 5

Your CI/CD pipeline automatically runs:

```bash
terraform apply -auto-approve
```

for every commit.

### Questions

1. What risks exist?
2. When is auto-approve acceptable?
3. What governance controls should be added?
4. How would HCP Terraform improve the process?

---

## Scenario 6

Terraform validation succeeds but apply fails.

### Questions

1. Why can this happen?
2. What troubleshooting steps would you follow?
3. Which Terraform commands help investigate?
4. How would you prevent future failures?

---

# Section 3 — State Management Scenarios

## Scenario 7

Two engineers run Terraform simultaneously.

Both modify infrastructure.

State becomes inconsistent.

### Questions

1. What happened?
2. Which Terraform feature prevents this?
3. What backend design would you recommend?
4. How would you recover?

---

## Scenario 8

Your team stores:

```text
terraform.tfstate
```

inside a Git repository.

### Questions

1. Why is this dangerous?
2. What information might be exposed?
3. What backend would you recommend?
4. What migration process would you follow?

---

## Scenario 9

A Terraform state file is accidentally deleted.

### Questions

1. What impact could this have?
2. How would you recover?
3. What preventive controls should exist?
4. Why is remote state preferred?

---

## Scenario 10

Terraform plan shows resources being recreated unexpectedly.

### Questions

1. What could cause this?
2. What state-related issues might exist?
3. How would you investigate?
4. Would you apply immediately?

---

## Scenario 11

An engineer manually edits the Terraform state file.

### Questions

1. What risks does this introduce?
2. When is manual editing acceptable?
3. What safer alternatives exist?
4. How would you validate the changes?

---

# Section 4 — Module Design Scenarios

## Scenario 12

Three teams maintain nearly identical VPC configurations.

Each repository contains duplicated code.

### Questions

1. What Terraform feature should be introduced?
2. How would you structure the solution?
3. What benefits would be gained?
4. What governance controls would you add?

---

## Scenario 13

A shared module receives a breaking update.

Twenty production environments use the module.

### Questions

1. What risks exist?
2. Why should versions be pinned?
3. How would you roll out the update?
4. What testing strategy would you use?

---

## Scenario 14

A module contains over 80 input variables.

Engineers struggle to use it.

### Questions

1. What design problem exists?
2. How would you improve maintainability?
3. What trade-offs exist?
4. What module design principles would you follow?

---

## Scenario 15

A child module needs access to a VPC ID created by another module.

### Questions

1. How should the modules communicate?
2. Why shouldn't resources be referenced directly?
3. What Terraform feature supports this?
4. How would you design the interface?

---

# Section 5 — Security & Secrets Scenarios

## Scenario 16

A database password is committed to GitHub.

### Questions

1. What risks exist?
2. What immediate actions are required?
3. How would Terraform handle secrets correctly?
4. What controls would prevent recurrence?

---

## Scenario 17

An engineer marks a variable:

```hcl
sensitive = true
```

and assumes the secret is fully protected.

### Questions

1. Why is this assumption incorrect?
2. Where might the secret still exist?
3. What additional controls are required?
4. What interview trap does this represent?

---

## Scenario 18

Your organization must rotate cloud credentials every 30 days.

### Questions

1. Why is hardcoding credentials problematic?
2. How could Vault help?
3. How would Terraform retrieve credentials?
4. What operational benefits are gained?

---

## Scenario 19

Security requires all storage buckets to be encrypted.

### Questions

1. How would you enforce this consistently?
2. Should this be implemented in modules, policies, or both?
3. How could Sentinel help?
4. What governance model would you recommend?

---

# Section 6 — Import & Migration Scenarios

## Scenario 20

Your company has 500 manually created AWS resources.

Terraform adoption begins next month.

### Questions

1. How would you approach migration?
2. Which resources should be imported first?
3. What risks exist?
4. How would you validate success?

---

## Scenario 21

An imported EC2 instance immediately appears for replacement in the next plan.

### Questions

1. Why could this happen?
2. What should be investigated?
3. Would you apply immediately?
4. How would you correct the configuration?

---

## Scenario 22

An engineer imports infrastructure but never creates Terraform configuration.

### Questions

1. What problem exists?
2. Why is import alone insufficient?
3. What future risks exist?
4. How should the process be corrected?

---

# Section 7 — HCP Terraform Scenarios

## Scenario 23

Your team uses local state and email-based change approvals.

Management wants better governance.

### Questions

1. What challenges exist?
2. How could HCP Terraform help?
3. What features would provide value?
4. How would you implement migration?

---

## Scenario 24

A pull request modifies production infrastructure.

The team wants visibility before approval.

### Questions

1. Which HCP Terraform feature helps?
2. What is a speculative plan?
3. Why is this valuable?
4. How does this improve collaboration?

---

## Scenario 25

A company wants automated compliance checks before deployment.

### Questions

1. Which HCP Terraform feature should be used?
2. How would Sentinel help?
3. What policies would you implement?
4. How would failures be handled?

---

## Scenario 26

Developers need security scanning integrated into Terraform runs.

### Questions

1. What HCP Terraform feature supports this?
2. How do Run Tasks work?
3. What tools could integrate?
4. What governance benefits are achieved?

---

# Section 8 — Enterprise Terraform Scenarios

## Scenario 27

Your company operates:

* 50 AWS Accounts
* Multiple Regions
* Hundreds of Applications

### Questions

1. How would you organize Terraform?
2. How would state be managed?
3. How would governance be enforced?
4. How would modules be structured?

---

## Scenario 28

A critical production outage requires emergency infrastructure changes.

### Questions

1. Should engineers modify infrastructure manually?
2. How should Terraform remain authoritative?
3. What post-incident actions are required?
4. How would drift be handled?

---

## Scenario 29

An auditor requests evidence of infrastructure changes from six months ago.

### Questions

1. What records should exist?
2. How would HCP Terraform help?
3. What Git practices support auditing?
4. What governance controls should be implemented?

---

## Scenario 30

Your organization is building an Internal Developer Platform.

Terraform will be used by hundreds of engineers.

### Questions

1. How should modules be designed?
2. What governance controls are required?
3. How would self-service infrastructure be enabled?
4. What platform engineering principles apply?

---

# Advanced Architecture Scenarios

## Scenario 31

Design Terraform architecture for:

* Development
* Staging
* Production

with strict isolation requirements.

---

## Scenario 32

Design a remote-state architecture for a multi-team AWS organization.

---

## Scenario 33

Design a Terraform module strategy for hundreds of microservices.

---

## Scenario 34

Design a disaster recovery strategy for Terraform state.

---

## Scenario 35

Design a governance framework using:

* HCP Terraform
* Sentinel
* Run Tasks
* GitHub

---

# Scenario Self-Assessment

| Score | Assessment                    |
| ----- | ----------------------------- |
| 0–10  | Beginner                      |
| 11–20 | Junior                        |
| 21–28 | Terraform Practitioner        |
| 29–33 | Interview Ready               |
| 34–35 | Senior-Level Discussion Ready |
