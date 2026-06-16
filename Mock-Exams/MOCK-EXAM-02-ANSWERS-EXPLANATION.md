# MOCK-EXAM-02-ANSWERS-EXPLANATIONS

# Question 1

### Correct Answer

**B**

### Objective

1a — Explain What IaC Is

### Explanation

Infrastructure as Code (IaC) manages infrastructure through version-controlled configuration files rather than manual processes.

### Why Others Are Incorrect

**A:** IaC reduces reliance on manual configuration.

**C:** Spreadsheets are not IaC.

**D:** Documentation is still important.

---

# Question 2

### Correct Answer

**C**

### Objective

1b — Advantages of IaC

### Explanation

IaC improves consistency and repeatability across environments.

### Why Others Are Incorrect

**A:** IaC reduces manual work.

**B:** IaC increases automation.

**D:** APIs remain essential.

---

# Question 3

### Correct Answer

**C**

### Objective

1c — Multi-Cloud, Hybrid Cloud, and Service-Agnostic Workflows

### Explanation

Terraform works across many platforms through providers.

### Why Others Are Incorrect

**A:** Terraform supports more than AWS.

**B:** Terraform supports more than Azure.

**D:** Multiple installations are unnecessary.

---

# Question 4

### Correct Answer

**B**

### Objective

2b — Describe How Terraform Uses Providers

### Explanation

Providers are plugins that allow Terraform to communicate with APIs.

### Why Others Are Incorrect

**A:** State tracks infrastructure.

**C:** Modules organize reusable code.

**D:** Backends manage state storage.

---

# Question 5

### Correct Answer

**C**

### Objective

2a — Install and Version Terraform Providers

### Explanation

Required providers are typically declared in the terraform block.

### Why Others Are Incorrect

**A:** Backend blocks manage state.

**B:** Output blocks expose values.

**D:** Variable blocks define inputs.

---

# Question 6

### Correct Answer

**B**

### Objective

2a — Install and Version Terraform Providers

### Explanation

terraform init downloads required providers and modules.

### Why Others Are Incorrect

**A:** Apply modifies infrastructure.

**C:** Validate checks configuration.

**D:** Destroy removes infrastructure.

---

# Question 7

### Correct Answer

**C**

### Objective

2c — Multiple Providers

### Explanation

Provider aliases allow multiple configurations of the same provider.

### Why Others Are Incorrect

**A:** Aliases do not encrypt state.

**B:** Aliases do not create outputs.

**D:** Aliases do not create modules.

---

# Question 8

### Correct Answer

**C**

### Objective

2d — State Management

### Explanation

Terraform state tracks managed infrastructure resources.

### Why Others Are Incorrect

**A:** Variables provide input.

**B:** Outputs expose values.

**D:** Providers communicate with APIs.

---

# Question 9

### Correct Answer

**B**

### Objective

2d — State Management

### Explanation

State contains resource metadata and mappings between configuration and infrastructure.

### Why Others Are Incorrect

**A:** Documentation is not stored in state.

**C:** Cloud source code is unrelated.

**D:** Terraform binaries are not stored in state.

---

# Question 10

### Correct Answer

**C**

### Objective

2d — State Management

### Explanation

Terraform state maps desired configuration to actual infrastructure.

### Why Others Are Incorrect

**A:** Terraform requires state.

**B:** State is not optional.

**D:** State exists outside HCP Terraform as well.

---

# Question 11

### Correct Answer

**B**

### Objective

3a — Describe the Terraform Workflow

### Explanation

The standard workflow is:

```text
terraform init
terraform validate
terraform plan
terraform apply
```

### Why Others Are Incorrect

**A:** Incorrect sequence.

**C:** Apply happens after plan.

**D:** Init must occur first.

---

# Question 12

### Correct Answer

**C**

### Objective

3c — Validate a Terraform Configuration

### Explanation

terraform validate checks syntax and internal configuration consistency.

### Why Others Are Incorrect

**A:** Does not inspect cloud health.

**B:** Does not check state locking.

**D:** Does not install providers.

---

# Question 13

### Correct Answer

**B**

### Objective

3d — Generate and Review an Execution Plan

### Explanation

terraform plan generates an execution plan showing proposed changes.

### Why Others Are Incorrect

**A:** Does not generate state.

**C:** Does not create providers.

**D:** Not related to module registries.

---

# Question 14

### Correct Answer

**D**

### Objective

3e — Apply Changes to Infrastructure

### Explanation

terraform apply executes infrastructure changes.

### Why Others Are Incorrect

**A:** Plan only previews changes.

**B:** Validate checks configuration.

**C:** Fmt formats code.

---

# Question 15

### Correct Answer

**A**

### Objective

3f — Destroy Terraform-Managed Infrastructure

### Explanation

terraform destroy removes resources managed by Terraform.

### Why Others Are Incorrect

**B:** Providers remain installed.

**C:** Configuration files remain.

**D:** Variables are unaffected.

---

# Question 16

### Correct Answer

**C**

### Objective

3g — Apply Formatting and Style Adjustments

### Explanation

terraform fmt standardizes Terraform file formatting.

### Why Others Are Incorrect

**A:** Displays outputs.

**B:** Lists state resources.

**D:** Shows state or plan data.

---

# Question 17

### Correct Answer

**B**

### Objective

4a — Use and Differentiate Resource and Data Blocks

### Explanation

Resource blocks create, update, and destroy infrastructure.

### Why Others Are Incorrect

**A:** Data blocks read existing infrastructure.

**C:** Providers configure API access.

**D:** Terraform blocks configure Terraform itself.

---

# Question 18

### Correct Answer

**B**

### Objective

4a — Use and Differentiate Resource and Data Blocks

### Explanation

Data sources retrieve information about existing infrastructure.

### Why Others Are Incorrect

**A:** Data sources do not create resources.

**C:** Data sources do not manage state.

**D:** Data sources do not configure modules.

---

# Question 19

### Correct Answer

**C**

### Objective

4a — Resource vs Data Blocks

### Explanation

Data blocks are used to read existing infrastructure information.

### Why Others Are Incorrect

**A:** Resources create infrastructure.

**B:** Resources manage infrastructure.

**D:** They serve different purposes.

---

# Question 20

### Correct Answer

**C**

### Objective

4a — Resource vs Data Blocks

### Explanation

A data source should be used when referencing an existing VPC.

### Why Others Are Incorrect

**A:** Outputs expose values.

**B:** Modules organize reusable code.

**D:** Backends manage state.

---

# Question 21

### Correct Answer

**B**

### Objective

4c — Use Variables and Outputs

### Explanation

Variables allow users to provide input values to Terraform configurations.

### Why Others Are Incorrect

**A:** State tracks infrastructure.

**C:** Providers are installed through init.

**D:** Variables do not create modules.

---

# Question 22

### Correct Answer

**A**

### Objective

4c — Use Variables and Outputs

### Explanation

Output blocks expose useful information from Terraform-managed resources.

### Why Others Are Incorrect

**B:** Outputs do not configure state.

**C:** Outputs do not install providers.

**D:** Outputs do not create resources.

---

# Question 23

### Correct Answer

**C**

### Objective

4d — Understand and Use Complex Types

### Explanation

A list stores an ordered collection of values.

### Why Others Are Incorrect

**A:** String stores a single value.

**B:** Bool stores true or false.

**D:** Map stores key-value pairs.

---

# Question 24

### Correct Answer

**B**

### Objective

4d — Understand and Use Complex Types

### Explanation

Maps are collections of key-value pairs.

### Why Others Are Incorrect

**A:** Objects have a defined schema.

**C:** Lists are ordered collections.

**D:** Tuples contain fixed-position values.

---

# Question 25

### Correct Answer

**C**

### Objective

4f — Define Resource Dependencies

### Explanation

Terraform automatically determines dependencies through resource references.

### Why Others Are Incorrect

**A:** Sentinel enforces policies.

**B:** Run Tasks integrate external tools.

**D:** Outputs do not create dependencies.

---

# Question 26

### Correct Answer

**B**

### Objective

4f — Define Resource Dependencies

### Explanation

depends_on should only be used when Terraform cannot infer the dependency automatically.

### Why Others Are Incorrect

**A:** Overusing depends_on is discouraged.

**C:** Does not create variables.

**D:** Does not install providers.

---

# Question 27

### Correct Answer

**C**

### Objective

4e — Expressions and Functions

### Explanation

merge() combines multiple maps into a single map.

### Why Others Are Incorrect

**A:** concat() combines lists.

**B:** lookup() retrieves values.

**D:** length() counts elements.

---

# Question 28

### Correct Answer

**A**

### Objective

4e — Expressions and Functions

### Explanation

lookup() retrieves a value associated with a key from a map.

### Why Others Are Incorrect

**B:** upper() converts text to uppercase.

**C:** lower() converts text to lowercase.

**D:** concat() combines lists.

---

# Question 29

### Correct Answer

**A**

### Objective

4g — Validate Configuration Using Custom Conditions

### Explanation

Validation blocks enforce rules on variable values before deployment.

### Why Others Are Incorrect

**B:** Does not create state.

**C:** Does not install providers.

**D:** Does not create outputs.

---

# Question 30

### Correct Answer

**C**

### Objective

4h — Sensitive Data and Vault

### Explanation

Sensitive values are hidden from Terraform CLI output.

### Why Others Are Incorrect

**A:** Sensitive does not encrypt state.

**B:** Sensitive does not encrypt variables.

**D:** Sensitive does not automatically integrate with Vault.

---

# Question 31

### Correct Answer

**B**

### Objective

5c — Use Modules in Configuration

### Explanation

Modules improve reuse, consistency, and maintainability.

### Why Others Are Incorrect

**A:** Modules reduce duplication.

**C:** Providers remain necessary.

**D:** State is still required.

---

# Question 32

### Correct Answer

**A**

### Objective

5a — Explain How Terraform Sources Modules

### Explanation

The source argument specifies where Terraform can find the module.

### Why Others Are Incorrect

**B:** Provider configures APIs.

**C:** Backend manages state.

**D:** Output exposes values.

---

# Question 33

### Correct Answer

**D**

### Objective

5a — Explain How Terraform Sources Modules

### Explanation

Terraform supports modules from local paths, Git repositories, and the Terraform Registry.

### Why Others Are Incorrect

**A, B, C:** Each is valid but incomplete.

---

# Question 34

### Correct Answer

**A**

### Objective

5d — Manage Module Versions

### Explanation

Version constraints reduce risk by preventing unexpected module upgrades.

### Why Others Are Incorrect

**B:** Not related to outputs.

**C:** Not related to providers.

**D:** Not related to state locking.

---

# Question 35

### Correct Answer

**B**

### Objective

5b — Describe Variable Scope Within Modules

### Explanation

Modules receive input values through variables.

### Why Others Are Incorrect

**A:** Outputs return values.

**C:** State does not pass values.

**D:** Providers do not pass values.

---

# Question 36

### Correct Answer

**B**

### Objective

6c — Configure Remote State Using the Backend Block

### Explanation

Backends define where Terraform stores state.

### Why Others Are Incorrect

**A:** Variables provide input.

**C:** Providers interact with APIs.

**D:** Modules organize code.

---

# Question 37

### Correct Answer

**C**

### Objective

6a — Describe the Local Backend

### Explanation

The local backend is the default backend when none is configured.

### Why Others Are Incorrect

**A:** Remote backend must be configured.

**B:** S3 is optional.

**D:** GCS is optional.

---

# Question 38

### Correct Answer

**A**

### Objective

6c — Configure Remote State

### Explanation

Remote state enables collaboration and centralized state management.

### Why Others Are Incorrect

**B:** Provider speed is unrelated.

**C:** Resource count is unaffected.

**D:** Encryption depends on backend configuration.

---

# Question 39

### Correct Answer

**B**

### Objective

6b — Describe State Locking

### Explanation

State locking prevents multiple users from modifying state simultaneously.

### Why Others Are Incorrect

**A:** Variables are unrelated.

**C:** Providers are unrelated.

**D:** Module versioning is unrelated.

---

# Question 40

### Correct Answer

**C**

### Objective

6d — Manage Resource Drift and Terraform State

### Explanation

Drift occurs when infrastructure changes outside Terraform's control.

### Why Others Are Incorrect

**A:** State deletion is not drift.

**B:** Provider upgrades are unrelated.

**D:** Module version mismatches are unrelated.

---

# MOCK-EXAM-02-ANSWERS

## Questions 41–57

---

# Question 41

### Correct Answer

**A**

### Objective

6d — Manage Resource Drift and Terraform State

### Explanation

terraform plan compares Terraform state and configuration against actual infrastructure and is the primary method for detecting drift.

### Why Others Are Incorrect

**B:** terraform fmt only formats code.

**C:** terraform output displays outputs.

**D:** terraform init initializes the working directory.

---

# Question 42

### Correct Answer

**B**

### Objective

7a — Import Existing Infrastructure into Your Terraform Workspace

### Explanation

terraform import primarily updates Terraform state by associating existing infrastructure with a Terraform resource address.

### Why Others Are Incorrect

**A:** Import does not generate configuration.

**C:** Providers are not modified.

**D:** Outputs are not affected.

---

# Question 43

### Correct Answer

**C**

### Objective

7a — Import Existing Infrastructure into Your Terraform Workspace

### Explanation

Import associates an existing resource with Terraform state so Terraform can manage it.

### Why Others Are Incorrect

**A:** Terraform does not automatically generate complete configuration.

**B:** Provider plugins are not imported.

**D:** Import does not create state locking.

---

# Question 44

### Correct Answer

**A**

### Objective

7b — Use the CLI to Inspect State

### Explanation

terraform state list displays all resources currently tracked in state.

### Why Others Are Incorrect

**B:** Shows detailed information for one resource.

**C:** Displays state or plan information.

**D:** Displays outputs.

---

# Question 45

### Correct Answer

**C**

### Objective

7b — Use the CLI to Inspect State

### Explanation

terraform state show displays detailed information for a specific resource in state.

### Why Others Are Incorrect

**A:** Removes resources from state.

**B:** Moves resources within state.

**D:** Validates configuration.

---

# Question 46

### Correct Answer

**C**

### Objective

7c — Describe When and How to Use Verbose Logging

### Explanation

TF_LOG is the environment variable used to enable Terraform logging.

### Why Others Are Incorrect

**A:** Not a Terraform environment variable.

**B:** Not a Terraform environment variable.

**D:** Not a valid Terraform logging variable.

---

# Question 47

### Correct Answer

**B**

### Objective

7c — Describe When and How to Use Verbose Logging

### Explanation

TF_LOG=DEBUG is commonly used for troubleshooting and provides detailed diagnostic information.

### Why Others Are Incorrect

**A:** Not a valid Terraform log level.

**C:** Not a valid Terraform log level.

**D:** Not a valid Terraform log level.

---

# Question 48

### Correct Answer

**B**

### Objective

8c — Describe How to Organize and Use HCP Terraform Workspaces and Projects

### Explanation

A workspace is the primary execution environment within HCP Terraform and contains runs, variables, and state.

### Why Others Are Incorrect

**A:** Projects group workspaces.

**C:** Organizations contain projects and workspaces.

**D:** Registries store modules.

---

# Question 49

### Correct Answer

**A**

### Objective

8c — Describe How to Organize and Use HCP Terraform Workspaces and Projects

### Explanation

Projects are used to logically group related workspaces.

### Why Others Are Incorrect

**B:** Providers are not stored in projects.

**C:** Projects do not replace organizations.

**D:** State is not stored locally by projects.

---

# Question 50

### Correct Answer

**A**

### Objective

8a — Use HCP Terraform to Create Infrastructure

### Explanation

Workspaces provide centralized remote state management and execution.

### Why Others Are Incorrect

**B:** Outputs only expose values.

**C:** Variables provide input.

**D:** Providers communicate with APIs.

---

# Question 51

### Correct Answer

**B**

### Objective

8b — Describe HCP Terraform Collaboration and Governance Features

### Explanation

Sentinel is HashiCorp's Policy as Code framework.

### Why Others Are Incorrect

**A:** Run Tasks integrate external systems.

**C:** Projects organize workspaces.

**D:** Variables are unrelated.

---

# Question 52

### Correct Answer

**A**

### Objective

8b — Describe HCP Terraform Collaboration and Governance Features

### Explanation

Sentinel policies enforce governance, compliance, and security requirements.

### Why Others Are Incorrect

**B:** Sentinel does not install providers.

**C:** Sentinel does not generate modules.

**D:** Sentinel does not manage state storage.

---

# Question 53

### Correct Answer

**B**

### Objective

8d — Configure and Use HCP Terraform Integration

### Explanation

Run Tasks allow Terraform runs to integrate with external tools such as security scanners and compliance platforms.

### Why Others Are Incorrect

**A:** Run Tasks do not replace workspaces.

**C:** State storage is unrelated.

**D:** Variables are unrelated.

---

# Question 54

### Correct Answer

**C**

### Objective

8b — Describe HCP Terraform Collaboration and Governance Features

### Explanation

Private Module Registry stores reusable, approved Terraform modules for organizational use.

### Why Others Are Incorrect

**A:** State files are stored elsewhere.

**B:** Variables are not stored in the registry.

**D:** Providers are not stored in the module registry.

---

# Question 55

### Correct Answer

**C**

### Objective

8b — Describe HCP Terraform Collaboration and Governance Features

### Explanation

The Private Module Registry is designed to distribute approved modules across teams.

### Why Others Are Incorrect

**A:** Sentinel enforces policies.

**B:** Run Tasks provide integrations.

**D:** State locking prevents concurrent modifications.

---

# Question 56

### Correct Answer

**C**

### Objective

8c — Describe How to Organize and Use HCP Terraform Workspaces and Projects

### Explanation

Workspaces provide isolated state instances, allowing separate environments or deployments.

### Why Others Are Incorrect

**A:** Workspaces do not install providers.

**B:** Workspaces do not create modules.

**D:** Projects and workspaces serve different purposes.

---

# Question 57

### Correct Answer

**A**

### Objective

8a, 8b, 8c, 8d — HCP Terraform

### Explanation

Remote execution, centralized state management, collaboration, auditability, and governance are key HCP Terraform capabilities that improve team collaboration.

### Why Others Are Incorrect

**B:** Local state reduces collaboration.

**C:** Manual deployments reduce consistency.

**D:** Provider aliases are unrelated to collaboration.

---
