# 🛠️ AWS IaC & Configuration Tools Overview

## Terraform
**Terraform** is an open-source Infrastructure-as-Code (IaC) tool that allows you to define, provision, and manage cloud infrastructure using a declarative language. It works across multiple cloud providers, making it ideal for orchestrating complex, repeatable AWS environments with version control and modularity.

## AWS CloudFormation
**AWS CloudFormation** is Amazon's native IaC service that allows you to define AWS resources using JSON or YAML templates. It integrates tightly with AWS services and provides stack-based deployments, rollback mechanisms, and drift detection to manage infrastructure natively within AWS.

## AWS Systems Manager (SSM)
**AWS Systems Manager (SSM)** is a suite of AWS services for managing, configuring, patching, and automating tasks on EC2 instances and hybrid infrastructure. It allows secure remote execution, inventory tracking, and automation workflows without requiring SSH access to the servers.

---

## 🧭 Migration Use Case: From On-Prem to AWS

An organization migrating from on-prem to AWS might start by using **Terraform** or **CloudFormation** to define and spin up core infrastructure such as VPCs, subnets, EC2 instances, and IAM roles.

- If cross-cloud or modular flexibility is needed, **Terraform** is preferred.
- If sticking with AWS-native tooling, **CloudFormation** offers tighter integration.

Once infrastructure is up, **SSM** can be used to install software, configure servers, run patching, and manage instances securely—replacing legacy SSH or config management systems.

> 🔁 Together, these tools help replicate and modernize the on-prem environment in the cloud with automation, repeatability, and security.

