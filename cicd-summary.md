# 🚀 CI/CD Pipeline with Jenkins, GitHub, Terraform, and Ansible

## 🔄 Summary of the CI/CD Process

This CI/CD pipeline automates application deployment using a combination of:

- **GitHub**: Source code management (stores application + infrastructure code)
- **Jenkins**: Automation server that triggers builds and orchestrates pipeline steps
- **Terraform**: Infrastructure-as-Code tool to provision cloud infrastructure
- **Ansible**: Configuration management tool to install, configure, and deploy app

### Flow Overview:
1. **Developer pushes code** (app or infra) to GitHub.
2. **Webhook triggers Jenkins** to start a pipeline.
3. **Jenkins runs Terraform** to provision or update cloud resources.
4. **Jenkins runs Ansible** to configure servers and deploy the app.
5. **Notifications/logs** are sent after build completes.

---

## 🛠 Tools & Setup

### Required Tools:
- Jenkins with plugins:
  - GitHub Integration
  - Pipeline
  - Ansible
  - Terraform
- GitHub repository with:
  - `Jenkinsfile`
  - `main.tf` / Terraform modules
  - `ansible/` directory with playbooks
  - Application code

---

## 🔧 Step-by-Step CI/CD Workflow

### 1. Setup GitHub Repo
- Organize project structure:
```
├── Jenkinsfile
├── main.tf
├── ansible/
│   └── site.yml
├── app/
│   └── your_app_code
```
- Push to GitHub

### 2. Configure Jenkins
- Install Jenkins and required plugins
- Add GitHub credentials (Personal Access Token)
- Create a pipeline job connected to the GitHub repo
- Add webhook from GitHub:
  - Payload URL: `http://your-jenkins-url/github-webhook/`

---

## 🧩 Sample `Jenkinsfile` (Declarative Pipeline)

```groovy
pipeline {
  agent any

  environment {
    TF_VAR_env = "dev"
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your/repo.git'
      }
    }

    stage('Terraform Init & Apply') {
      steps {
        dir('terraform') {
          sh 'terraform init'
          sh 'terraform apply -auto-approve'
        }
      }
    }

    stage('Run Ansible Playbook') {
      steps {
        dir('ansible') {
          sh 'ansible-playbook -i inventory.ini site.yml'
        }
      }
    }

    stage('Verify & Notify') {
      steps {
        sh 'curl -s http://your-app-endpoint/health || echo "Health check failed"'
      }
    }
  }
}
```

---

## ✅ Best Practices
- Separate app logic, infrastructure, and config management in your repo
- Use **Terraform remote state** (e.g., S3 + DynamoDB for AWS)
- Encrypt secrets using **Ansible Vault** or external secrets manager
- Test playbooks and plans locally before CI runs
- Use Jenkins credentials manager for tokens and secrets

---

> 🧠 _This pipeline brings infrastructure provisioning (Terraform) and application configuration (Ansible) into a single automated flow triggered by GitHub and orchestrated by Jenkins._

