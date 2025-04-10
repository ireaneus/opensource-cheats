# 📅 Daily DevOps Tasks with Ansible (and AWS Deployment)

---

## 🔧 Overview

As a DevOps Engineer, daily tasks often include:

- Provisioning infrastructure
- Configuring servers
- Deploying applications
- Managing secrets
- Monitoring system state

This guide shows how to use **Ansible** to automate those tasks and how it integrates with **AWS**. It also introduces **AWS-native tools** as alternatives.

---

## 🧰 Daily DevOps Tasks Using Ansible

### 🗂️ 1. **Inventory Management**
```bash
# Update inventory file (e.g., dynamic from AWS)
ansible-inventory -i aws_ec2.yml --graph
```

> Use static files for small projects or [Dynamic Inventory Plugins](https://docs.ansible.com/ansible/latest/plugins/inventory/aws_ec2.html) for AWS.

---

### 🛠️ 2. **Provision Infrastructure (Optionally via Terraform or Ansible)**
- While Ansible can provision AWS resources (e.g., EC2, VPCs) using `boto3`, **Terraform** is often preferred for IaC.
- Ansible is usually used **after** the infra is provisioned.

```yaml
# playbooks/provision_ec2.yml

- name: Launch EC2
  hosts: localhost
  connection: local
  gather_facts: false
  tasks:
    - name: Launch EC2 instance
      amazon.aws.ec2_instance:
        key_name: my-key
        instance_type: t2.micro
        image_id: ami-0abcdef1234567890
        wait: true
        count: 1
        region: us-east-1
        tags:
          Name: webserver
```

```bash
ansible-playbook playbooks/provision_ec2.yml
```

---

### 🧼 3. **Configuration Management**
```yaml
# playbooks/configure_web.yml

- name: Configure web servers
  hosts: tag_Name_webserver
  become: true
  tasks:
    - name: Install NGINX
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start and enable NGINX
      service:
        name: nginx
        state: started
        enabled: true
```

```bash
ansible-playbook -i aws_ec2.yml playbooks/configure_web.yml
```

---

### 🔁 4. **Deploy Application Code**
```yaml
- name: Deploy App
  hosts: tag_Name_webserver
  become: true
  tasks:
    - name: Pull code from Git
      git:
        repo: 'https://github.com/your-org/your-app.git'
        dest: /var/www/app
        version: main
```

---

### 🔐 5. **Manage Secrets with Ansible Vault**
```bash
ansible-vault create group_vars/all/vault.yml
```

```yaml
# Access with variables
- name: Use secret
  debug:
    msg: "Password is {{ vault_db_password }}"
```

```bash
ansible-playbook site.yml --ask-vault-pass
```

---

### 🧪 6. **System Health Checks**
```bash
# Quick ping check
ansible all -m ping -i aws_ec2.yml

# Uptime check
ansible all -a "uptime" -i aws_ec2.yml
```

---

### 🗓️ Daily Task Schedule Example

| Time       | Task                        | Tool        |
|------------|-----------------------------|-------------|
| 9:00 AM    | Check server health         | Ansible     |
| 9:30 AM    | Deploy latest code          | Ansible     |
| 10:00 AM   | Update packages/configs     | Ansible     |
| 1:00 PM    | Provision new environments  | Terraform + Ansible |
| 3:00 PM    | Monitor & respond to alerts | CloudWatch, Ansible, Grafana |

---

## ☁️  Can Ansible Be Used in AWS?

✅ **Yes!** Ansible integrates deeply with AWS via the `amazon.aws` and `community.aws` collections.

### How to Set Up:

```bash
# Install required collections
ansible-galaxy collection install amazon.aws community.aws

# Install boto3 for AWS API access
pip install boto3 botocore
```

📄 Use dynamic inventory or tag-based host targeting (e.g., `tag_Name_webserver`).

---

## 🧩 AWS-Native Alternatives to Ansible

| Tool                 | Description                                         |
|----------------------|-----------------------------------------------------|
| **AWS Systems Manager (SSM)** | Run commands, patch, and manage instances via SSM agent. |
| **CloudFormation**   | Declarative Infrastructure-as-Code (JSON/YAML).     |
| **AWS OpsWorks**     | Managed configuration using Chef/Puppet.            |
| **CDK (Cloud Dev Kit)** | Code-based IaC using Python/TypeScript.           |

---

## 🔍 When to Use What?

| Use Case                | Best Tool                  |
|-------------------------|----------------------------|
| Ad-hoc configuration    | ✅ Ansible                  |
| Repeated provisioning   | ✅ Terraform or CloudFormation |
| Agentless automation    | ✅ Ansible                  |
| Managed compliance      | ✅ AWS Systems Manager      |

---

## 📚 Resources

- [Ansible AWS Collections](https://docs.ansible.com/ansible/latest/collections/amazon/aws/)
- [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest)
- [Ansible Dynamic Inventory for AWS](https://docs.ansible.com/ansible/latest/plugins/inventory/aws_ec2.html)

---


