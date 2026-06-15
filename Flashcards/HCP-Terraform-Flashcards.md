# HCP Terraform Flashcards

> Terraform Associate (004) — HCP Terraform Flashcards
>
> Purpose:
>
> * Master Domain 8 Exam Objectives
> * Rapid HCP Terraform Revision
> * Interview Preparation
> * Exam-Day Recall
>
> Coverage:
>
> * HCP Terraform Fundamentals
> * Workspaces
> * Projects
> * Remote Operations
> * Collaboration
> * Governance
> * Security
> * VCS Integration
> * Run Tasks
> * Sentinel
> * Exam Traps

---

# HCP Terraform Fundamentals

### Flashcard 1

**Q:** What is HCP Terraform?

**A:** HashiCorp's managed platform for provisioning, managing, and governing infrastructure using Terraform.

---

### Flashcard 2

**Q:** What was HCP Terraform previously called?

**A:** Terraform Cloud.

---

### Flashcard 3

**Q:** What problem does HCP Terraform solve?

**A:**

* Collaboration
* State management
* Governance
* Automation
* Security

---

### Flashcard 4

**Q:** What is the primary advantage of HCP Terraform over local execution?

**A:** Centralized infrastructure operations.

---

### Flashcard 5

**Q:** Does HCP Terraform require local state files?

**A:** No.

---

### Flashcard 6

**Q:** Where is Terraform state stored in HCP Terraform?

**A:** Remotely within the workspace.

---

### Flashcard 7

**Q:** Why is remote state beneficial?

**A:** Secure collaboration and centralized management.

---

### Flashcard 8

**Q:** Does HCP Terraform support team-based workflows?

**A:** Yes.

---

# Organizations, Projects & Workspaces

### Flashcard 9

**Q:** What is an Organization?

**A:** Top-level container for users, teams, projects, and workspaces.

---

### Flashcard 10

**Q:** What is a Project?

**A:** Logical grouping of related workspaces.

---

### Flashcard 11

**Q:** What is a Workspace?

**A:** A unit that stores configuration, state, variables, and run history.

---

### Flashcard 12

**Q:** Which entity actually executes Terraform runs?

**A:** Workspace.

---

### Flashcard 13

**Q:** Can multiple workspaces exist in a project?

**A:** Yes.

---

### Flashcard 14

**Q:** Typical workspace organization?

**A:**

* Dev
* Test
* Stage
* Production

---

### Flashcard 15

**Q:** Why use projects?

**A:** Organizational separation and governance.

---

### Flashcard 16

**Q:** What is workspace state isolation?

**A:** Each workspace maintains independent Terraform state.

---

# Remote Operations

### Flashcard 17

**Q:** What is a Remote Run?

**A:** Terraform execution performed inside HCP Terraform infrastructure.

---

### Flashcard 18

**Q:** What phases occur during a run?

**A:**

* Plan
* Policy Checks
* Apply

---

### Flashcard 19

**Q:** What is a speculative plan?

**A:** Plan generated without infrastructure modification.

---

### Flashcard 20

**Q:** When are speculative plans commonly used?

**A:** Pull Request reviews.

---

### Flashcard 21

**Q:** Does a speculative plan modify infrastructure?

**A:** No.

---

### Flashcard 22

**Q:** Why use remote execution?

**A:** Standardized execution environments.

---

### Flashcard 23

**Q:** What does run history provide?

**A:** Auditable deployment records.

---

# VCS Integration

### Flashcard 24

**Q:** What is VCS Integration?

**A:** Connection between HCP Terraform and source control systems.

---

### Flashcard 25

**Q:** Common supported VCS platforms?

**A:**

* GitHub
* GitLab
* Bitbucket
* Azure DevOps

---

### Flashcard 26

**Q:** What event commonly triggers a run?

**A:** Git commit or merge.

---

### Flashcard 27

**Q:** Why integrate Terraform with Git?

**A:** Infrastructure-as-Code lifecycle automation.

---

### Flashcard 28

**Q:** What is a VCS-driven workflow?

**A:** Infrastructure changes initiated through repository commits.

---

### Flashcard 29

**Q:** Why are pull requests important?

**A:** Peer review before deployment.

---

# Variables & Secrets

### Flashcard 30

**Q:** Where can workspace variables be stored?

**A:** Workspace settings.

---

### Flashcard 31

**Q:** What are Terraform Variables?

**A:** Input values available to Terraform configuration.

---

### Flashcard 32

**Q:** What are Environment Variables?

**A:** Variables used by Terraform runtime or providers.

---

### Flashcard 33

**Q:** Can HCP Terraform store sensitive variables?

**A:** Yes.

---

### Flashcard 34

**Q:** Are sensitive variables visible after saving?

**A:** No.

---

### Flashcard 35

**Q:** Why store secrets as sensitive variables?

**A:** Reduce exposure in UI and logs.

---

### Flashcard 36

**Q:** Does marking a variable sensitive encrypt state?

**A:** No.

---

# Teams & Collaboration

### Flashcard 37

**Q:** What is a Team?

**A:** Collection of users with assigned permissions.

---

### Flashcard 38

**Q:** Why use teams instead of individual permissions?

**A:** Easier access management.

---

### Flashcard 39

**Q:** What principle should govern permissions?

**A:** Least privilege.

---

### Flashcard 40

**Q:** Why centralize Terraform operations?

**A:** Improve governance and auditability.

---

### Flashcard 41

**Q:** What feature provides deployment history?

**A:** Run history.

---

### Flashcard 42

**Q:** What feature improves collaboration during reviews?

**A:** Speculative plans.

---

# Governance Features

### Flashcard 43

**Q:** What is Governance?

**A:** Enforcing organizational standards and policies.

---

### Flashcard 44

**Q:** What is Sentinel?

**A:** Policy-as-Code framework.

---

### Flashcard 45

**Q:** What does Sentinel evaluate?

**A:** Terraform plans and configuration behavior.

---

### Flashcard 46

**Q:** Why use Sentinel?

**A:** Prevent policy violations before deployment.

---

### Flashcard 47

**Q:** Example Sentinel policy?

**A:** Block public cloud storage buckets.

---

### Flashcard 48

**Q:** Can Sentinel stop an apply?

**A:** Yes.

---

### Flashcard 49

**Q:** What are Policy Checks?

**A:** Automated governance validations during runs.

---

### Flashcard 50

**Q:** When do policy checks execute?

**A:** After planning and before apply.

---

# Run Tasks

### Flashcard 51

**Q:** What are Run Tasks?

**A:** External integrations executed during Terraform runs.

---

### Flashcard 52

**Q:** Purpose of Run Tasks?

**A:** Extend workflow automation.

---

### Flashcard 53

**Q:** Example Run Task integrations?

**A:**

* Security scanning
* Compliance validation
* Cost estimation

---

### Flashcard 54

**Q:** When can Run Tasks execute?

**A:**

* Post-plan
* Pre-apply

---

### Flashcard 55

**Q:** Can Run Tasks block deployments?

**A:** Yes.

---

# State Management

### Flashcard 56

**Q:** What state advantage does HCP Terraform provide?

**A:** Centralized remote state management.

---

### Flashcard 57

**Q:** Does HCP Terraform support state locking?

**A:** Yes.

---

### Flashcard 58

**Q:** Why is state locking important?

**A:** Prevent concurrent modifications.

---

### Flashcard 59

**Q:** What problem does state locking prevent?

**A:** State corruption.

---

### Flashcard 60

**Q:** Does HCP Terraform automatically manage state locking?

**A:** Yes.

---

# Security & Compliance

### Flashcard 61

**Q:** Why is remote execution more secure?

**A:** Reduces dependency on local credentials.

---

### Flashcard 62

**Q:** Why avoid storing secrets in code repositories?

**A:** Security risk and credential exposure.

---

### Flashcard 63

**Q:** What security benefit does centralized state provide?

**A:** Controlled access and auditing.

---

### Flashcard 64

**Q:** What security model should organizations adopt?

**A:** Least privilege access.

---

# Exam Trap Flashcards

### Flashcard 65

**Q:** Does HCP Terraform eliminate Terraform state?

**A:** No. It manages state remotely.

---

### Flashcard 66

**Q:** Is a Project the same as a Workspace?

**A:** No.

---

### Flashcard 67

**Q:** Does a speculative plan deploy resources?

**A:** No.

---

### Flashcard 68

**Q:** Are Run Tasks the same as Sentinel policies?

**A:** No.

---

### Flashcard 69

**Q:** Does Sentinel replace Terraform configuration?

**A:** No.

---

### Flashcard 70

**Q:** Are sensitive variables stored in plaintext UI?

**A:** No.

---

### Flashcard 71

**Q:** Can HCP Terraform be used without VCS integration?

**A:** Yes.

---

### Flashcard 72

**Q:** Does remote execution require local terraform apply?

**A:** No.

---

# Rapid Revision Table

| Component        | Purpose                        |
| ---------------- | ------------------------------ |
| Organization     | Top-level container            |
| Project          | Group of workspaces            |
| Workspace        | Execution environment          |
| Remote Run       | Executes Terraform remotely    |
| Speculative Plan | Plan-only review               |
| Sentinel         | Policy-as-Code                 |
| Run Tasks        | External workflow integrations |
| Team             | Permission management          |
| Variables        | Runtime configuration          |
| Remote State     | Centralized state storage      |
| State Locking    | Prevents concurrent updates    |
| VCS Integration  | Git-driven automation          |

---

# One-Minute HCP Terraform Review

Remember:

* Organization contains Projects
* Projects contain Workspaces
* Workspaces execute Terraform
* State is stored remotely
* Speculative Plans do not deploy
* Sentinel enforces policies
* Run Tasks integrate external systems
* Teams manage access
* Remote execution improves consistency
* State locking prevents corruption

---

