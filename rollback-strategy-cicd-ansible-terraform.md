### ✅ Guide 3: CI/CD Rollback Strategy with Terraform + Ansible  
Save this as `rollback-strategy-cicd-ansible-terraform.md`.

# 🔁 Rollback Strategy in CI/CD: Terraform + Ansible

---

## 🧭 Purpose

In a CI/CD pipeline using **Terraform** and **Ansible**, rollbacks are essential to recover quickly from bad deployments or infrastructure changes. This guide provides strategies to **revert app deployments and infrastructure changes** safely and automatically.

---

## 🚨 When Do You Need a Rollback?

- Failed deployment or configuration
- Broken infrastructure changes (e.g., wrong instance type)
- Service outage after a push to staging or prod
- Security misconfiguration
- Application crash or data corruption

---

## ⚙️ Rollback Scenarios

| Type             | Tool        | Rollback Strategy                              |
|------------------|-------------|-------------------------------------------------|
| Infra change     | Terraform   | Use `terraform destroy` or versioned modules   |
| App/config change| Ansible     | Use tags, Git versioning, or previous playbooks|

---

## 🛠️ Terraform Rollback Strategies

### 1. 📦 Versioned Modules (Recommended)

```hcl
module "ec2_web" {
  source  = "git::https://github.com/your-org/terraform-modules.git//ec2"
  version = "v1.0.0"
}
```

- Roll back by switching the version and re-applying:

```hcl
# Change version to previous stable
version = "v0.9.1"
```

```bash
terraform init -upgrade
terraform apply -auto-approve
```

---

### 2. 🕒 Use Terraform State History

Terraform automatically tracks state versions:

```bash
# List historical states
terraform state list

# Manually roll back with backed-up state
terraform state pull > current.tfstate
terraform state push previous.tfstate
```

---

## 🧰 Ansible Rollback Strategies

### 1. 🔖 Use Git for App Versioning

```yaml
- name: Checkout specific app version
  git:
    repo: https://github.com/your-org/app.git
    dest: /var/www/app
    version: "{{ rollback_version }}"
```

Rollback by setting:

```yaml
rollback_version: "v1.2.0"
```

Use Ansible tags and variables to make rollbacks dynamic and easy to automate.

---

### 2. 🗂️ Backup + Restore Tasks

```yaml
- name: Backup existing index.html
  copy:
    src: /usr/share/nginx/html/index.html
    dest: /usr/share/nginx/html/index.html.bak
    remote_src: true

- name: Restore backup if needed
  copy:
    src: /usr/share/nginx/html/index.html.bak
    dest: /usr/share/nginx/html/index.html
    remote_src: true
```

Trigger these via tags:

```bash
ansible-playbook playbook.yml --tags "restore_backup"
```

---

### 3. 📦 Maintain Rollback Playbooks

Create a separate rollback playbook for critical components:

```bash
ansible-playbook rollback.yml -i inventory.ini
```

---

## 🤖 GitHub Actions Example (Manual Rollback Trigger)

```yaml
# .github/workflows/rollback.yml

name: Rollback Prod

on:
  workflow_dispatch:
    inputs:
      rollback_version:
        description: 'App version to roll back to'
        required: true

jobs:
  rollback:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install Ansible
        run: sudo apt-get install -y ansible

      - name: Rollback with Ansible
        working-directory: ansible
        run: |
          ansible-playbook -i inventory.ini rollback.yml --extra-vars "rollback_version=${{ github.event.inputs.rollback_version }}"
```

> ✅ This allows **manual rollbacks** from the GitHub Actions UI!

---

## ✅ Best Practices

| Tip                               | Why It Helps                                |
|----------------------------------|---------------------------------------------|
| Use Git tags/releases            | Easy to reference stable versions           |
| Store app versions in variables  | Easier rollback via parameterized playbooks |
| Separate rollback playbooks      | Cleaner, safer recovery process             |
| Use Terraform modules            | Isolated, versionable infra changes         |
| Keep backups before config change| Fast local rollback without redeployment    |

---

## 📚 References

- [Terraform State Management](https://developer.hashicorp.com/terraform/docs/state)
- [Ansible Tags & Variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html)
- [GitHub Actions Manual Triggers](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#workflow_dispatch)

---
