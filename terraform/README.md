# TERRAFORM #
HashiCorp TerraForm is an open source tool for managing infrastructure as code (IaC), which allows users to define and provision cloud and on-premise resources in a consistent and automated way.
It works by writing declarative configuration files to manage the lifecycle of infrastructure, from creation to deletion.
Key benefits include enabling a single workflow for different environments ( cloud, private datacenter, SaaS) reducing costs, and minimizing risk through automation and policy enforcement.

## TERRAFORM - CORE FUNCTIONS and WORKFLOW
DIFINE > INITIALIZE > PLAN > APPLY (EXECUTE) > DISTROY
### DEFINE Infrastructure
- Write human readable configuration files to define desired infrastructure
Such as: Virtual Machines, networks, and storage.
### INITIALIZE
The terraform init command prepares a working directory by downloading any necessary provider plugins
### PLAN
Terraform plan generates a execution plan. This plan shows "what action terraform will take to achive the desired stage."
### APPLY 
Terraform apply executes the plan, creating or updating the infrastructure match the configuration
### DISTROY
Destroy is used to remove all the resources that were created by terraform.

## KEY FEATURES AND BENEFITS 
### IaC (infrastructure as Code): 
Treats infrastructure configuration as a code, 
Allowing for version control. Collobartion and Consistency.

### Multi-Cloud support: 
works with a wide range of platforms and services, including AWS, Azure, Google Cloud, and IBM Cloud, by using various providers.

### Automation:
Automates the provisioning and management of infrastructure, saving time and reducing manual effort.

### Cost Optimization:
Helps reduce cloud spend by identifying and eliminating underutilized or unnecessary resources.

## Risk reduction: 
Improves security by enforcing policies, continuously monitoring infrastructure health and using reusable, compliant modules.

## Unified workflow: 
Provides a single workflow to manage infrastructure across different environments, including private datacenters and SaaS applications.


