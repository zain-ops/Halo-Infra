
# AWS Infrastructure using Terraform

This repository contains Terraform code to deploy and manage AWS infrastructure. It uses various modules to handle resources like Load Balancers (ALB), Aurora DB, ECS, S3, and more.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Directory Structure](#directory-structure)
- [Setup Instructions](#setup-instructions)
- [Modules](#modules)
- [Outputs](#outputs)
- [Troubleshooting](#troubleshooting)

---

## Overview

This Terraform project is designed to simplify the provisioning of AWS infrastructure by breaking it down into reusable modules. These modules handle common components such as networking, compute, storage, and monitoring, making the setup highly modular and easy to manage.

---

## Prerequisites

Before getting started, ensure that you have the following tools installed and configured:

- [Terraform](https://www.terraform.io/downloads.html) (version `~> 1.0`)
- [AWS CLI](https://aws.amazon.com/cli/) (configured with credentials)
- AWS credentials (via `~/.aws/credentials` or environment variables)

---

## Directory Structure

Here’s the breakdown of the directory and file structure:

```bash
├── main.tf                 # Main Terraform configuration
├── modules                 # Custom Terraform modules
│   ├── alb                 # Module for AWS ALB (Application Load Balancer)
│   ├── auroradb            # Module for AWS AuroraDB
│   ├── cache               # Module for Caching (ElastiCache)
│   ├── cloudfront          # Module for CloudFront CDN
│   ├── cloudwatch          # Module for monitoring (CloudWatch)
│   ├── ecr                 # Module for AWS ECR (Elastic Container Registry)
│   ├── ecs                 # Module for running containers on ECS
│   ├── iam                 # IAM Roles and Policies
│   ├── s3                  # AWS S3 storage
│   ├── secretsmanager      # AWS Secrets Manager
│   ├── security_groups     # Security Groups for the VPC
│   └── vpc                 # Virtual Private Cloud (VPC) module
├── outputs.tf              # Output values (after applying the configuration)
├── terraform.tfvars        # Variable values to customize the deployment
├── variables.tf            # Defines variables used in the configuration
└── versions.tf             # Specifies the Terraform and AWS provider versions
```

---

## Setup Instructions

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone <repository-url>
cd <repository-directory>
```

### Step 2: Initialize Terraform

Run the following command to initialize the Terraform project and download necessary providers:

```bash
terraform init
```

### Step 3: Customize Variables

Modify `terraform.tfvars` to suit your environment. Example of `terraform.tfvars`:

```hcl
app_name         = "halo"
environment_name = "prod"
region_name      = "us-east-1"
```

### Step 4: Apply the Terraform Configuration

Deploy the infrastructure by running:

```bash
terraform apply
```

Review the planned changes, and type `yes` to confirm.

---

## Modules

This project uses several modules to simplify the management of AWS resources. Here’s a brief overview of each:


- **VPC**: Isolates resources in a private network.
- **Security Groups**: Firewall rules to control access to services.
- **Secrets Manager**: Securely stores and manages secrets.
- **CloudWatch**: Used for monitoring and logging your AWS resources.
- **IAM**: Manages roles and permissions for users and services.
- **ALB (Application Load Balancer)**: Balances incoming traffic across multiple servers.
- **AuroraDB**: A managed relational database service with high availability.
- **Cache (ElastiCache)**: Provides a caching layer to reduce load on databases.
- **S3**: Object storage service for storing files.
- **CloudFront**: A CDN for serving content quickly from various geographical locations.
- **ECR**: AWS container registry to store Docker images.
- **ECS (Elastic Container Service)**: Runs containerized applications at scale.

---

## Outputs

After running `terraform apply`, the following important information will be outputted:

- Load Balancer DNS Name
- AuroraDB Endpoint
- S3 Bucket Names
- VPC ID

To view the outputs after running Terraform, execute:

```bash
terraform output
```

---

## Troubleshooting

- **Issue: Unauthorized Operation**  
  Solution: Ensure your AWS credentials are configured correctly with the required permissions.

- **Issue: Terraform Init Fails**  
  Solution: Verify the correct Terraform version and AWS provider version in `versions.tf`.

- **Issue: Terraform Apply Fails**  
  Solution: Check the AWS service limits and ensure that all required resources (like VPC, Subnets) are available.

---

For further assistance, refer to the [Terraform documentation](https://www.terraform.io/docs/index.html).

