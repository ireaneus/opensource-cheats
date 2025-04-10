
- **Terraform** → Best for provisioning infrastructure (cloud-native resources)
- **Ansible** → Best for configuration management and application deployment

---

# 🔧 Ansible + Terraform Workflow Guide

---

## 🧭 Overview

Use **Terraform** to:
- Provision AWS resources (EC2, VPC, S3, RDS, etc.)

Use **Ansible** to:
- Configure EC2 instances (install packages, deploy code, manage users, etc.)

This hybrid approach creates a clear **separation of concerns**:
- **Terraform = Infrastructure as Code (IaC)**
- **Ansible = Configuration Management**

---

## 🔁 Workflow Summary

```plaintext
1. Write Terraform code
2. Apply Terraform to create infrastructure (EC2, etc.)
3. Export inventory from Terraform (e.g., EC2 IPs)
4. Run Ansible against new infrastructure
5. Optionally destroy everything with Terraform
```

---

## 📦 Folder Structure

```plaintext
project/
├── terraform/
│   ├── main.tf
│   ├── outputs.tf
│   └── variables.tf
├── ansible/
│   ├── playbook.yml
│   └── inventory.ini (auto-generated or dynamic)
└── README.md
```

---

## 🛠️ Step-by-Step Guide

---

### 1. 🌍 Provision Infrastructure with Terraform

```hcl
# terraform/main.tf

provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0abcdef1234567890"
  instance_type = "t2.micro"
  key_name      = "my-key"
  tags = {
    Name = "ansible-web"
  }

  provisioner "local-exec" {
    command = "echo ${self.public_ip} >> ../ansible/inventory.ini"
  }
}
```

```hcl
# terraform/outputs.tf

output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

```bash
# Run Terraform
cd terraform
terraform init
terraform apply -auto-approve
```

---

### 2. 🧾 Generate Ansible Inventory

Option 1: Use Terraform output directly

```bash
terraform output -raw instance_ip > ../ansible/inventory.ini
```

Example `inventory.ini`:

```ini
[web]
54.12.34.56 ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/my-key.pem
```

Option 2: Use **Ansible Dynamic Inventory** for AWS  
📚 https://docs.ansible.com/ansible/latest/plugins/inventory/aws_ec2.html

---

### 3. 🛠️ Configure with Ansible

```yaml
# ansible/playbook.yml

- name: Configure Web Server
  hosts: web
  become: true
  tasks:
    - name: Install NGINX
      yum:
        name: nginx
        state: present

    - name: Start NGINX
      service:
        name: nginx
        state: started
        enabled: true
```

```bash
# Run Ansible Playbook
cd ../ansible
ansible-playbook -i inventory.ini playbook.yml
```

---

### 4. 🚫 (Optional) Teardown

```bash
cd ../terraform
terraform destroy -auto-approve
```

---

## 🧩 Integration Tips

| Tip                                 | Description                                     |
|-------------------------------------|-------------------------------------------------|
| Use `local-exec` in Terraform       | To write IPs or data into Ansible inventory     |
| Use `remote-exec` in Terraform      | For simple tasks, but prefer Ansible for config |
| Use Ansible `tags`                  | To run only portions of your playbook           |
| Use Terraform outputs               | To pass dynamic values (IP, DNS, etc.) to Ansible |

---

## 📘 Example Workflow (Visual)

```plaintext
[TERRAFORM]
  |
  |  --> Create EC2 instance
  |  --> Output IP to file
  v
[ANSIBLE]
  |
  |  --> Read IPs from inventory.ini
  |  --> SSH into instances
  |  --> Install packages, deploy app
```

---

## 🔐 Security Note

- Ensure your SSH key (`.pem`) is secured and not hardcoded.
- Use `ansible-vault` for secrets.
- Use `terraform.tfvars` or environment variables for sensitive values.

---

## 📚 References

- [Ansible Docs](https://docs.ansible.com/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [Ansible + Terraform GitHub Example](https://github.com/hashicorp/terraform-guides/tree/master/operations/provisioners/ansible)

---
```

