### ✅ Guide 2: Multi-Stage Environment CI/CD with Terraform + Ansible  
Save this as `multi-stage-cicd-ansible-terraform.md`.

# 🌐 Multi-Stage CI/CD Pipeline: Terraform + Ansible (Dev → Staging → Prod)

---

## 🧭 Overview

This guide explains how to structure and implement a **multi-environment CI/CD pipeline** using **Terraform** and **Ansible**, with distinct stages for **development**, **staging**, and **production**.

---

## 📦 Goal

Implement isolated and automated deployment flows for:

- ✅ Dev (test environment)
- ✅ Staging (UAT/QA environment)
- ✅ Prod (live environment)

---

## 🗂️ Recommended Project Structure

```plaintext
project/
├── environments/
│   ├── dev/
│   │   ├── terraform/
│   │   │   └── *.tf
│   │   └── ansible/
│   │       └── playbook.yml
│   ├── staging/
│   └── prod/
├── app/
└── .github/workflows/
    └── deploy.yml
```

Each environment contains its own isolated Terraform and Ansible configurations.

---

## 🔄 Git Flow Strategy (Recommended)

```plaintext
main → production
│
├── dev → development environment
│
└── staging → staging environment
```

> Use **branch-based pipelines**: push to `dev`, `staging`, or `main` to trigger deployments to corresponding environments.

---

## ⚙️ GitHub Actions Workflow (Simplified Example)

```yaml
# .github/workflows/deploy.yml

name: Multi-Stage CI/CD

on:
  push:
    branches:
      - dev
      - staging
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    env:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set Environment Paths
        run: |
          if [[ "${{ github.ref }}" == "refs/heads/dev" ]]; then
            echo "ENV_PATH=environments/dev" >> $GITHUB_ENV
          elif [[ "${{ github.ref }}" == "refs/heads/staging" ]]; then
            echo "ENV_PATH=environments/staging" >> $GITHUB_ENV
          else
            echo "ENV_PATH=environments/prod" >> $GITHUB_ENV
          fi

      - name: Terraform Init & Apply
        working-directory: ${{ env.ENV_PATH }}/terraform
        run: |
          terraform init
          terraform apply -auto-approve

      - name: Install Ansible
        run: |
          sudo apt update
          sudo apt install -y ansible

      - name: Run Ansible
        working-directory: ${{ env.ENV_PATH }}/ansible
        run: |
          ansible-playbook -i inventory.ini playbook.yml
```

---

## 🔐 Secret Management

Use GitHub Secrets or a vault to securely handle:
- AWS credentials
- Ansible vault passwords
- SSH keys for EC2 access

---

## 🚀 Benefits of Multi-Stage CI/CD

| Benefit                  | Description                                |
|--------------------------|--------------------------------------------|
| Environment isolation    | Prevents dev/staging/prod from interfering |
| Progressive delivery     | Promotes tested code through each stage    |
| Safer deployments        | Reduces risk of breaking production        |
| Easier rollbacks         | Each env has independent infra+config      |

---

## 📘 Optional Enhancements

- Add **manual approvals** for promotion to staging/prod
- Use **Terraform workspaces** instead of separate folders
- Add **testing steps** after each deployment (e.g., curl endpoint, integration tests)
- Implement **blue/green** or **canary deployment** logic

---

## 📚 References

- [GitHub Actions - Environments](https://docs.github.com/en/actions/deployment/targeting-different-environments)
- [Terraform CLI Workspaces](https://developer.hashicorp.com/terraform/docs/language/state/workspaces)
- [Ansible Best Practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html)

---
