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

### Risk reduction: 
Improves security by enforcing policies, continuously monitoring infrastructure health and using reusable, compliant modules.

### Unified workflow: 
Provides a single workflow to manage infrastructure across different environments, including private datacenters and SaaS applications.

## Create a Terraform Module for AWS Resources
Creating a Terraform module for AWS resources involvs structuring your Terraform code to be reusable and encapsulated. 
This allows you to define a set of related AWS resources once and then deploy them multiple times with different configurations.

### 1. Module Structure

```
my-aws-module/
├── main.tf
├── variables.tf
├── outputs.tf
├── versions.tf
```
### 2. main.tf (Resource Defination)
This file contains the core resource definitions for your AWS infrastructure. For example, to create an S3 bucket:

```
# my-aws-module/main.tf
resource "aws_s3_bucket" "this" {
  bucket = var.bucket_name
  acl    = var.bucket_acl

  tags = var.tags
}
```
### 3. variables.tf (Input Variables):
Define input variables that allow users of your module to customize its behavior.
```
# my-aws-module/variables.tf
variable "bucket_name" {
  description = "The name of the S3 bucket."
  type        = string
}

variable "bucket_acl" {
  description = "The ACL for the S3 bucket."
  type        = string
  default     = "private"
}

variable "tags" {
  description = "A map of tags to assign to the bucket."
  type        = map(string)
  default     = {}
}
```
### 4. outputs.tf (Output Values):
Define output values that expose important information about the created resources to the parent module or root configuration.
```
# my-aws-module/outputs.tf
output "bucket_id" {
  description = "The ID of the S3 bucket."
  value       = aws_s3_bucket.this.id
}

output "bucket_arn" {
  description = "The ARN of the S3 bucket."
  value       = aws_s3_bucket.this.arn
}
```
### 5. versions.tf (Terraform and Provider Versions):
Specify the required Terraform and provider versions for your module.
```
# my-aws-module/versions.tf
terraform {
  required_version = ">= 1.0.0"
}

provider "aws" {
  region = "us-east-1" # Or make this a variable
}
```
### 6. Using the Module:
In your root Terraform configuration (e.g., main.tf in your main project directory), you can call your module:
```
# root/main.tf
module "my_s3_bucket" {
  source = "./my-aws-module" # Path to your module directory

  bucket_name = "my-unique-application-bucket"
  bucket_acl  = "public-read"
  tags = {
    Environment = "Development"
    Project     = "MyApplication"
  }
}

output "s3_bucket_arn" {
  value = module.my_s3_bucket.bucket_arn
}
```
$ Reference Links
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-create
