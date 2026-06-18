# EXAM 01

> Terraform Associate (004)
>
> Questions: 57
>
> Time Recommendation: 60 Minutes
>
> Passing Target: 48+/57
>
> Instructions:
>
> * Choose the best answer.
> * Each question has one correct answer.
> * Do not use documentation.
> * Simulate real exam conditions.

---

## Question 1

Which command formats Terraform files?

* A. terraform format
* B. terraform tidy
* C. terraform fmt
* D. terraform clean

---

## Question 2

What is a Terraform module?

* A. Container image
* B. Provider plugin
* C. Reusable Terraform code
* D. Operating system

---

## Question 3

Which Terraform concept represents reusable infrastructure code?

* A. Providers
* B. Modules
* C. Resources
* D. Variables

---

## Question 4

Which feature allows sharing variables across multiple workspaces?

* A. Outputs
* B. Modules
* C. State files
* D. Variable Sets

---

## Question 5

What is the main purpose of Terraform state?

* A. Store logs
* B. Store configuration
* C. Track infrastructure resources
* D. Store secrets

---

## Question 6

Which Terraform command shows graph of resources?

* A. terraform show
* B. terraform plan
* C. terraform graph
* D. terraform visualize

---

## Question 7

Which block prevents resource destruction?

* A. prevent_destroy
* B. depends_on
* C. create_before_destroy
* D. ignore_changes

---

## Question 8

Which command previews changes before applying them?

* A. terraform validate
* B. terraform plan
* C. terraform apply
* D. terraform run

---

## Question 9

Which command generates a JSON representation of a plan?

* A. terraform plan -json
* B. terraform plan -out
* C. terraform apply -json
* D. terraform show -json

---

## Question 10

Which block specifies provider version constraints?

* A. required_providers
* B. dependency
* C. provider
* D. version

---

## Question 11

Which command imports existing infrastructure?

* A. terraform init
* B. terraform apply
* C. terraform plan
* D. terraform import

---

## Question 12

Which platform provides remote Terraform runs and collaboration?

* A. Jenkins
* B. HCP Terraform
* C. Docker Hub
* D. GitLab

---

## Question 13

Which block defines input variables?

* A. output
* B. variable
* C. module
* D. resource

---

## Question 14

Which block defines infrastructure resources?

* A. data
* B. resource
* C. module
* D. provider

---

## Question 15

Which block retrieves data from external sources?

* A. variable
* B. output
* C. resource
* D. data

---

## Question 16

Which lifecycle rule creates resource before destroying old one?

* A. ignore_changes
* B. depends_on
* C. create_before_destroy
* D. prevent_destroy

---

## Question 17

Which feature prevents concurrent state changes by multiple users?

* A. State caching
* B. State encryption
* C. State locking
* D. State versioning

---

## Question 18

Which block defines output values?

* A. provider
* B. output
* C. module
* D. variable

---

## Question 19

Which lifecycle rule prevents accidental deletion?

* A. replace_triggered_by
* B. ignore_changes
* C. depends_on
* D. prevent_destroy

---

## Question 20

Which Terraform command initializes a working directory?

* A. terraform start
* B. terraform plan
* C. terraform deploy
* D. terraform init

---

## Question 21

Which lifecycle rule ignores attribute changes?

* A. prevent_destroy
* B. ignore_changes
* C. depends_on
* D. replace_triggered_by

---

## Question 22

Which command locks state during operations?

* A. terraform state lock
* B. terraform plan
* C. terraform lock
* D. terraform apply

---

## Question 23

Which file stores Terraform backend configuration?

* A. variables.tf
* B. backend.tf
* C. terraform.tfvars
* D. main.tf

---

## Question 24

Which block iterates over multiple values?

* A. depends_on
* B. count
* C. for_each
* D. lifecycle

---

## Question 25

Which command lists resources in Terraform state?

* A. terraform inspect
* B. terraform state show
* C. terraform state list
* D. terraform show

---

## Question 26

Which language is used in Terraform configuration files?

* A. YAML
* B. JSON
* C. XML
* D. HCL

---

## Question 27

Which command checks Terraform and provider versions?

* A. terraform validate
* B. terraform check
* C. terraform providers
* D. terraform version

---

## Question 28

Which block defines default variable values?

* A. variable
* B. output
* C. locals
* D. default

---

## Question 29

Which configuration stores Terraform state remotely?

* A. provider configuration
* B. module configuration
* C. backend configuration
* D. resource configuration

---

## Question 30

Which command generates an execution plan?

* A. terraform plan
* B. terraform create
* C. terraform preview
* D. terraform run

---

## Question 31

Which block defines explicit dependencies?

* A. module
* B. provider
* C. depends_on
* D. lifecycle

---

## Question 32

Which file extension is used for Terraform configuration files?

* A. .conf
* B. .tf
* C. .json
* D. .yaml

---

## Question 33

Which block defines a module call?

* A. resource
* B. module
* C. provider
* D. output

---

## Question 34

Which block defines dynamic resource blocks?

* A. for_each
* B. resource
* C. provider
* D. dynamic

---

## Question 35

Which block iterates over map objects?

* A. count
* B. lifecycle
* C. depends_on
* D. for_each

---

## Question 36

Which block manages resource dependencies?

* A. lifecycle
* B. resource
* C. depends_on
* D. for_each

---

## Question 37

Which provider manages AWS infrastructure?

* A. gcp
* B. aws
* C. kubernetes
* D. azure

---

## Question 38

Which block is used to output sensitive information?

* A. variable
* B. module
* C. output
* D. resource

---

## Question 39

What is a Terraform provider?

* A. A database
* B. A container
* C. A programming language
* D. A plugin interacting with APIs

---

## Question 40

Which command upgrades modules and providers?

* A. terraform init -upgrade
* B. terraform upgrade
* C. terraform get
* D. terraform update

---

## Question 41

Which command validates Terraform configuration syntax?

* A. terraform check
* B. terraform validate
* C. terraform verify
* D. terraform inspect

---

## Question 42

Which command destroys Terraform-managed resources?

* A. terraform clean
* B. terraform destroy
* C. terraform terminate
* D. terraform remove

---

## Question 43

What is the purpose of Terraform variables?

* A. Store logs
* B. Parameterize configurations
* C. Store outputs
* D. Store state

---

## Question 44

Which feature marks sensitive variables?

* A. sensitive=false
* B. sensitive=true
* C. sensitive=protected
* D. sensitive=optional

---

## Question 45

Where can public Terraform modules be found?

* A. AWS Marketplace
* B. GitHub Actions
* C. Terraform Registry
* D. Docker Hub

---

## Question 46

Which block configures providers?

* A. provider
* B. resource
* C. module
* D. output

---

## Question 47

Which command removes resources from state without destroying them?

* A. terraform remove
* B. terraform delete
* C. terraform destroy
* D. terraform state rm

---

## Question 48

Which lifecycle rule ignores changes to specific attributes?

* A. create_before_destroy
* B. ignore_changes
* C. depends_on
* D. prevent_destroy

---

## Question 49

Which command validates provider installation?

* A. terraform plan
* B. terraform init
* C. terraform providers
* D. terraform validate

---

## Question 50

Which block allows resource replacement before destruction?

* A. prevent_destroy
* B. create_before_destroy
* C. replace_triggered_by
* D. ignore_changes

---

## Question 51

Which command downloads required providers and modules?

* A. terraform download
* B. terraform init
* C. terraform setup
* D. terraform install

---

## Question 52

Which command applies configuration changes to reach the desired state?

* A. terraform execute
* B. terraform commit
* C. terraform apply
* D. terraform build

---

## Question 53

Which block defines Terraform local values?

* A. variables
* B. modules
* C. outputs
* D. locals

---

## Question 54

Which block allows multiple instances of a resource?

* A. lifecycle
* B. count
* C. for_each
* D. depends_on

---

## Question 55

Which command shows the state of resources?

* A. terraform status
* B. terraform info
* C. terraform inspect
* D. terraform show

---

## Question 56

Which command shows detailed resource outputs?

* A. terraform output
* B. terraform view
* C. terraform show
* D. terraform inspect

---

## Question 57

Which block allows conditional resource creation?

* A. count
* B. lifecycle
* C. for_each
* D. depends_on

---

## Question 58

Which Terraform feature stores reusable variables globally?

* A. Outputs
* B. Locals
* C. Variable Sets
* D. Modules

---

## Question 59

Which block fetches external data?

* A. module
* B. resource
* C. data
* D. provider

---

## Question 60

Which command refreshes state with real infrastructure?

* A. terraform validate
* B. terraform update
* C. terraform plan
* D. terraform refresh
