### ✅ Guide 1: Diagram-Enhanced CI/CD Pipeline with Ansible + Terraform  

# 🚀 Diagram-Enhanced CI/CD Pipeline: Ansible + Terraform

---

## 📦 Purpose

This guide illustrates a **CI/CD pipeline** using **Terraform** for infrastructure provisioning and **Ansible** for configuration management, with clear **ASCII diagrams** to visualize each step.

---

## 🧭 Overview Diagram

```plaintext
          ┌────────────┐
          │  Developer │
          └────┬───────┘
               │
         Git Push to Main
               │
        ┌──────▼─────┐
        │ CI Pipeline│
        └──────┬─────┘
               │
        ┌──────▼────────┐
        │ Terraform Init│
        └──────┬────────┘
               │
        ┌──────▼────────┐
        │Terraform Apply│
        └──────┬────────┘
               │
        ┌──────▼─────────────────────────┐
        │Output EC2 IPs → inventory.ini  │
        └──────┬─────────────────────────┘
               │
        ┌──────▼────────┐
        │Ansible Playbook│
        └──────┬────────┘
               │
        ┌──────▼─────┐
        │App Deployed│
        └────────────┘
```

---

## ⚙️ Key Components

- **Terraform** provisions infrastructure (e.g., EC2)
- **Ansible** configures servers (e.g., install NGINX, deploy app)
- **CI/CD Tool** (e.g., GitHub Actions) triggers everything

---

## 🗂️ Project Structure

```plaintext
project/
├── .github/workflows/deploy.yml
├── terraform/
│   └── *.tf
├── ansible/
│   ├── playbook.yml
│   ├── templates/
│   └── inventory.ini
└── app/
    └── index.html
```

---

## 🛠️ Example Pipeline Flow

```plaintext
1. Developer pushes code
2. GitHub Actions workflow starts
3. Terraform provisions EC2 instance
4. Terraform writes IP to Ansible inventory
5. Ansible connects via SSH, installs NGINX
6. Ansible copies HTML app to EC2
7. App is live 🎉
```

---

## 🔐 Security Notes

- Store credentials (AWS keys, SSH keys) as encrypted CI secrets
- Use `ansible-vault` or AWS SSM for secret management
- Avoid hardcoding anything sensitive in `.tf` or `.yml`

---

## 📚 Further Reading

- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest)
- [Ansible AWS Collections](https://docs.ansible.com/ansible/latest/collections/amazon/aws/)
- [GitHub Actions Docs](https://docs.github.com/en/actions)

---

