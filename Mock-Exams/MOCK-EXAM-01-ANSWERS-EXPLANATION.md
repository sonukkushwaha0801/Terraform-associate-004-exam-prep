# MOCK-EXAM-01-ANSWERS

---

# Question 1

### Correct Answer

**B**

### Objective

1a — Explain What IaC Is

### Explanation

Infrastructure as Code (IaC) manages infrastructure using machine-readable configuration files that can be version controlled.

### Why Others Are Incorrect

**A:** IaC reduces manual configuration.

**C:** Terraform works with cloud providers; it does not replace them.

**D:** Infrastructure is still required.

---

# Question 2

### Correct Answer

**C**

### Objective

1b — Advantages of IaC

### Explanation

IaC enables consistent and repeatable deployments across environments.

### Why Others Are Incorrect

**A:** IaC reduces manual work.

**B:** IaC improves consistency.

**D:** State management is still required.

---

# Question 3

### Correct Answer

**B**

### Objective

1c — Multi-Cloud and Service-Agnostic Workflows

### Explanation

Terraform uses provider plugins to interact with multiple cloud platforms from the same configuration.

### Why Others Are Incorrect

**A:** Only one Terraform installation is needed.

**C:** Virtualization is unrelated.

**D:** State files do not provide multi-cloud functionality.

---

# Question 4

### Correct Answer

**C**

### Objective

2b — Describe How Terraform Uses Providers

### Explanation

The provider block configures how Terraform communicates with external APIs.

### Why Others Are Incorrect

**A:** Modules organize reusable code.

**B:** Resources manage infrastructure.

**D:** Variables accept input values.

---

# Question 5

### Correct Answer

**C**

### Objective

3b — Initialize a Terraform Working Directory

### Explanation

terraform init prepares a working directory for use.

### Why Others Are Incorrect

**A:** Apply executes changes.

**B:** Validate checks configuration.

**D:** Plan previews changes.

---

# Question 6

### Correct Answer

**B**

### Objective

2a — Install and Version Terraform Providers

### Explanation

terraform init downloads required providers and modules.

### Why Others Are Incorrect

**A:** Infrastructure is not created.

**C:** State is not destroyed.

**D:** Resources are not imported.

---

# Question 7

### Correct Answer

**D**

### Objective

2a — Install and Version Terraform Providers

### Explanation

The version argument is used inside required_providers to constrain provider versions.

### Why Others Are Incorrect

**A:** source specifies provider location.

**B:** backend configures state storage.

**C:** required_version constrains Terraform itself.

---

# Question 8

### Correct Answer

**B**

### Objective

2c — Multiple Providers

### Explanation

Providers allow Terraform to interact with multiple platforms simultaneously.

### Why Others Are Incorrect

**A:** Workspaces isolate state.

**C:** Outputs expose values.

**D:** Variables provide input.

---

# Question 9

### Correct Answer

**C**

### Objective

2d — State Management

### Explanation

Terraform state maps configuration to actual infrastructure.

### Why Others Are Incorrect

**A:** Providers are stored separately.

**B:** Documentation is unrelated.

**D:** State does not replace configuration.

---

# Question 10

### Correct Answer

**C**

### Objective

2d — State Management

### Explanation

The local backend stores state in terraform.tfstate.

### Why Others Are Incorrect

**A:** Lock file.

**B:** Variable values file.

**D:** Variable definitions.

---

# Question 11

### Correct Answer

**B**

### Objective

3c — Validate Configuration

### Explanation

terraform validate checks configuration syntax and internal consistency.

### Why Others Are Incorrect

**A:** Plan previews changes.

**C:** Apply executes changes.

**D:** Output displays values.

---

# Question 12

### Correct Answer

**C**

### Objective

3d — Generate and Review a Plan

### Explanation

terraform plan shows what Terraform intends to do before changes occur.

### Why Others Are Incorrect

**A:** No resources are created.

**B:** No resources are destroyed automatically.

**D:** Import is unrelated.

---

# Question 13

### Correct Answer

**D**

### Objective

3d — Generate and Review a Plan

### Explanation

Plan allows teams to review proposed changes safely.

### Why Others Are Incorrect

**A:** Apply performs modifications.

**B:** Destroy removes infrastructure.

**C:** Init prepares the directory.

---

# Question 14

### Correct Answer

**B**

### Objective

3e — Apply Changes

### Explanation

terraform apply executes infrastructure changes.

### Why Others Are Incorrect

**A:** Validate only checks configuration.

**C:** Output displays values.

**D:** Fmt formats files.

---

# Question 15

### Correct Answer

**C**

### Objective

3g — Formatting and Style

### Explanation

terraform fmt standardizes Terraform code formatting.

### Why Others Are Incorrect

**A:** Does not create resources.

**B:** Does not validate configuration.

**D:** Does not import resources.

---

# Question 16

### Correct Answer

**A**

### Objective

3f — Destroy Infrastructure

### Explanation

terraform destroy removes Terraform-managed resources.

### Why Others Are Incorrect

**B:** Removes state entries only.

**C:** Validation command.

**D:** Output command.

---

# Question 17

### Correct Answer

**B**

### Objective

4a — Resource Blocks

### Explanation

Resources represent infrastructure objects managed by Terraform.

### Why Others Are Incorrect

**A:** Providers are plugins.

**C:** State entries track resources.

**D:** Backends manage state.

---

# Question 18

### Correct Answer

**C**

### Objective

4a — Data Blocks

### Explanation

Data sources read information about existing infrastructure.

### Why Others Are Incorrect

**A:** Resources create infrastructure.

**B:** Data sources do not destroy resources.

**D:** State locking is unrelated.

---

# Question 19

### Correct Answer

**B**

### Objective

4a — Resource vs Data

### Explanation

Data blocks retrieve information from existing infrastructure.

### Why Others Are Incorrect

**A:** Resources create infrastructure.

**C:** Providers configure API access.

**D:** State is stored separately.

---

# Question 20

### Correct Answer

**C**

### Objective

4a — Resource vs Data

### Explanation

A data block should be used to reference an existing VPC.

### Why Others Are Incorrect

**A:** Resource blocks create/manage resources.

**B:** Backend blocks configure state storage.

**D:** Output blocks expose values.

---

# Question 21

### Correct Answer

**C**

### Objective

4c — Use Variables and Outputs

### Explanation

Variable blocks define input values that can be supplied to a Terraform configuration.

### Why Others Are Incorrect

**A:** Outputs return values.

**B:** Providers configure API access.

**D:** Backends manage state storage.

---

# Question 22

### Correct Answer

**B**

### Objective

4c — Use Variables and Outputs

### Explanation

Outputs expose information from Terraform-managed infrastructure after deployment.

### Why Others Are Incorrect

**A:** Outputs do not store credentials.

**C:** Outputs do not manage state locking.

**D:** Outputs do not install providers.

---

# Question 23

### Correct Answer

**D**

### Objective

4d — Complex Types

### Explanation

A map is a collection of key-value pairs.

### Why Others Are Incorrect

**A:** String is a single value.

**B:** List is an ordered collection.

**C:** Bool represents true or false.

---

# Question 24

### Correct Answer

**B**

### Objective

4f — Resource Dependencies

### Explanation

depends_on creates an explicit dependency when Terraform cannot infer one automatically.

### Why Others Are Incorrect

**A:** References usually create implicit dependencies.

**C:** Variables do not define dependencies.

**D:** Outputs do not create dependencies.

---

# Question 25

### Correct Answer

**C**

### Objective

4f — Resource Dependencies

### Explanation

Terraform automatically determines dependencies through resource references.

### Why Others Are Incorrect

**A:** Sentinel enforces policies.

**B:** Run Tasks integrate external tools.

**D:** Projects organize workspaces.

---

# Question 26

### Correct Answer

**D**

### Objective

4e — Expressions and Functions

### Explanation

length() returns the number of elements in a collection.

### Why Others Are Incorrect

**A:** lookup() retrieves a value from a map.

**B:** merge() combines maps.

**C:** concat() combines lists.

---

# Question 27

### Correct Answer

**B**

### Objective

4e — Expressions and Functions

### Explanation

lookup() retrieves a value associated with a specified key from a map.

### Why Others Are Incorrect

**A:** Does not return resource IDs automatically.

**C:** Does not return provider versions.

**D:** Does not return backend types.

---

# Question 28

### Correct Answer

**B**

### Objective

4g — Validate Configuration Using Custom Conditions

### Explanation

Validation blocks ensure variable values meet defined requirements.

### Why Others Are Incorrect

**A:** Validation blocks do not create resources.

**C:** They do not configure providers.

**D:** They do not lock state.

---

# Question 29

### Correct Answer

**C**

### Objective

4h — Sensitive Data

### Explanation

The sensitive argument marks values as sensitive.

### Why Others Are Incorrect

**A:** Invalid Terraform argument.

**B:** Invalid Terraform argument.

**D:** Invalid Terraform argument.

---

# Question 30

### Correct Answer

**B**

### Objective

4h — Sensitive Data

### Explanation

Sensitive values are hidden from Terraform CLI output.

### Why Others Are Incorrect

**A:** Sensitive values are not automatically encrypted.

**C:** Sensitive values may still exist in state.

**D:** Terraform does not automatically store them in Vault.

---

# Question 31

### Correct Answer

**C**

### Objective

5c — Use Modules in Configuration

### Explanation

Modules enable code reuse and standardization.

### Why Others Are Incorrect

**A:** State locking is unrelated.

**B:** Modules do not provide encryption.

**D:** Modules do not install providers.

---

# Question 32

### Correct Answer

**B**

### Objective

5a — Explain How Terraform Sources Modules

### Explanation

The source argument tells Terraform where to find the module.

### Why Others Are Incorrect

**A:** Providers are unrelated.

**C:** Backends manage state.

**D:** Outputs expose values.

---

# Question 33

### Correct Answer

**D**

### Objective

5a — Explain How Terraform Sources Modules

### Explanation

Terraform supports modules from:

* Terraform Registry
* Git repositories
* Local paths

### Why Others Are Incorrect

**A, B, C:** Each is valid individually, but D is the complete answer.

---

# Question 34

### Correct Answer

**A**

### Objective

5d — Manage Module Versions

### Explanation

Version constraints prevent unexpected changes from new releases.

### Why Others Are Incorrect

**B:** Versioning does not enable state locking.

**C:** Versioning does not encrypt outputs.

**D:** Versioning does not create providers.

---

# Question 35

### Correct Answer

**B**

### Objective

5b — Variable Scope Within Modules

### Explanation

Module inputs are passed through variables.

### Why Others Are Incorrect

**A:** Outputs return information.

**C:** State does not pass values.

**D:** Backends do not pass values.

---

# Question 36

### Correct Answer

**B**

### Objective

6c — Configure Remote State Using the Backend Block

### Explanation

Backends define where Terraform state is stored.

### Why Others Are Incorrect

**A:** Providers manage APIs.

**C:** Variables accept input.

**D:** Outputs expose information.

---

# Question 37

### Correct Answer

**C**

### Objective

6a — Describe the Local Backend

### Explanation

The local backend is Terraform's default backend.

### Why Others Are Incorrect

**A:** Remote backend requires configuration.

**B:** S3 backend is optional.

**D:** GCS backend is optional.

---

# Question 38

### Correct Answer

**B**

### Objective

6c — Configure Remote State

### Explanation

Remote state improves collaboration by allowing teams to share state.

### Why Others Are Incorrect

**A:** Provider downloads are unrelated.

**C:** Remote state does not create modules.

**D:** Resource count is unaffected.

---

# Question 39

### Correct Answer

**A**

### Objective

6b — Describe State Locking

### Explanation

State locking prevents multiple users from modifying state simultaneously.

### Why Others Are Incorrect

**B:** Locking does not encrypt state.

**C:** Locking does not create backups.

**D:** Locking does not install providers.

---

# Question 40

### Correct Answer

**B**

### Objective

6d — Manage Resource Drift and Terraform State

### Explanation

Drift occurs when infrastructure changes outside Terraform.

### Why Others Are Incorrect

**A:** Import brings resources under management.

**C:** Validation checks configuration.

**D:** Initialization prepares the working directory.

---
# MOCK-EXAM-01-ANSWERS

## Questions 41–57

---

# Question 41

### Correct Answer

**C**

### Objective

6d — Manage Resource Drift and Terraform State

### Explanation

terraform plan compares the current state of infrastructure with the desired configuration and can identify drift.

### Why Others Are Incorrect

**A:** terraform output displays outputs.

**B:** terraform fmt formats code.

**D:** terraform init initializes a working directory.

---

# Question 42

### Correct Answer

**B**

### Objective

7a — Import Existing Infrastructure into Your Terraform Workspace

### Explanation

terraform import associates existing infrastructure with Terraform state.

### Why Others Are Incorrect

**A:** Import does not generate configuration.

**C:** Import does not create providers.

**D:** Import does not initialize backends.

---

# Question 43

### Correct Answer

**C**

### Objective

7a — Import Existing Infrastructure

### Explanation

After importing a resource, the configuration should match the actual infrastructure to avoid unexpected changes.

### Why Others Are Incorrect

**A:** Destroying infrastructure is unnecessary.

**B:** Removing the resource from state defeats the purpose of importing.

**D:** Terraform does not need reinstallation.

---

# Question 44

### Correct Answer

**A**

### Objective

7b — Use the CLI to Inspect State

### Explanation

terraform state list displays all resources tracked in state.

### Why Others Are Incorrect

**B:** Displays outputs.

**C:** Validates configuration.

**D:** Displays provider information.

---

# Question 45

### Correct Answer

**C**

### Objective

7b — Use the CLI to Inspect State

### Explanation

terraform state show displays detailed information about a resource in state.

### Why Others Are Incorrect

**A:** Moves state entries.

**B:** Removes state entries.

**D:** Creates an execution plan.

---

# Question 46

### Correct Answer

**B**

### Objective

7c — Describe When and How to Use Verbose Logging

### Explanation

TF_LOG enables Terraform logging.

### Why Others Are Incorrect

**A:** Invalid Terraform logging variable.

**C:** Not a Terraform environment variable.

**D:** Not a Terraform environment variable.

---

# Question 47

### Correct Answer

**C**

### Objective

7c — Verbose Logging

### Explanation

TF_LOG=DEBUG provides detailed troubleshooting information.

### Why Others Are Incorrect

**A:** OFF disables logging.

**B:** Not a valid Terraform log level.

**D:** Not a valid Terraform log level.

---

# Question 48

### Correct Answer

**B**

### Objective

8a — Use HCP Terraform to Create Infrastructure

### Explanation

Workspaces provide remote execution environments and state management.

### Why Others Are Incorrect

**A:** State locking is a feature, not an execution environment.

**C:** Variable validation is unrelated.

**D:** Providers communicate with APIs.

---

# Question 49

### Correct Answer

**B**

### Objective

8c — Organize and Use Workspaces and Projects

### Explanation

A workspace manages Terraform runs, variables, and state for a specific configuration.

### Why Others Are Incorrect

**A:** Provider plugins are not stored in workspaces.

**C:** Modules are stored elsewhere.

**D:** Projects organize workspaces.

---

# Question 50

### Correct Answer

**B**

### Objective

8c — Organize and Use Workspaces and Projects

### Explanation

Projects are used to group related workspaces.

### Why Others Are Incorrect

**A:** State belongs to workspaces.

**C:** Organizations are top-level containers.

**D:** Providers are unrelated.

---

# Question 51

### Correct Answer

**C**

### Objective

8b — Collaboration and Governance Features

### Explanation

Sentinel is HashiCorp's Policy-as-Code framework.

### Why Others Are Incorrect

**A:** Run Tasks integrate external tools.

**B:** Registry stores modules.

**D:** Projects organize workspaces.

---

# Question 52

### Correct Answer

**B**

### Objective

8b — Collaboration and Governance Features

### Explanation

Sentinel policies enforce organizational rules and governance controls.

### Why Others Are Incorrect

**A:** Sentinel does not install providers.

**C:** Sentinel does not replace state.

**D:** Sentinel does not generate modules.

---

# Question 53

### Correct Answer

**A**

### Objective

8d — Configure and Use HCP Terraform Integration

### Explanation

Run Tasks allow integration with external systems during Terraform runs.

### Why Others Are Incorrect

**B:** Outputs expose values.

**C:** Variables provide input.

**D:** Providers communicate with APIs.

---

# Question 54

### Correct Answer

**B**

### Objective

8b — Collaboration and Governance Features

### Explanation

Private Module Registry stores reusable Terraform modules for organizational use.

### Why Others Are Incorrect

**A:** Does not store state.

**C:** Does not execute plans.

**D:** Does not manage workspaces.

---

# Question 55

### Correct Answer

**C**

### Objective

8b — Collaboration and Governance Features

### Explanation

The Private Module Registry enables teams to share approved modules across the organization.

### Why Others Are Incorrect

**A:** Run Tasks provide integrations.

**B:** Sentinel provides governance.

**D:** State locking prevents concurrent updates.

---

# Question 56

### Correct Answer

**B**

### Objective

8c — Organize and Use Workspaces and Projects

### Explanation

Terraform workspaces provide separate state instances.

### Why Others Are Incorrect

**A:** Workspaces do not create provider configurations.

**C:** Workspaces do not replace modules.

**D:** Workspaces do not install providers.

---

# Question 57

### Correct Answer

**C**

### Objective

8a, 8b, 8c, 8d — HCP Terraform

### Explanation

HCP Terraform provides:

* Remote state
* Remote execution
* Collaboration
* Governance
* Policy enforcement
* Run history
* Integrations

making it the best solution for the stated requirements.

### Why Others Are Incorrect

**A:** Local backend lacks governance and collaboration.

**B:** Variables only provide configuration input.

**D:** Import only manages existing infrastructure.

---

