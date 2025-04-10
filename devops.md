---

# 🚀 DevOps Cheat Sheet

## 📌 DevOps Meaning
**DevOps** is a cultural sensibility that promotes a **unified, metrics-based** approach to software development and operations. It emphasizes **automation, collaboration, and continuous improvement** to build and deploy software **efficiently and fearlessly**.

However, many companies lack the will or discipline to foster a true **DevOps culture**. Instead, they create roles like **"DevOps Engineer"**, which often focus on infrastructure management, cloud technologies, and CI/CD pipelines rather than true cultural transformation.

---

## 🔗 Core DevOps Concepts

### 📡 **APIs (Application Programming Interfaces)**
- **Definition:** A set of **subroutines, protocols, and tools** that enable communication between software applications.
- **Purpose:** Allows applications to send web-based requests and receive responses.

### 🔄 **REST (Representational State Transfer)**
- **Definition:** A web service architecture that provides a **stateless** and **scalable** way to communicate between systems.
- **Key Constraints:**
  - **Client-Server** separation
  - **Stateless communication**
  - **Cacheable responses**
  - **Layered system architecture**
  
### 🗂️ **CRUD Operations (Create, Read, Update, Delete)**
- Basic operations performed on data stored in databases or services.

### 🔥 **HTTP Methods**
| Method | Purpose |
|--------|---------|
| **POST** | Create |
| **GET** | Read |
| **PUT** | Update |
| **DELETE** | Delete |

### 📦 **JSON (JavaScript Object Notation)**
- **Definition:** A lightweight, human-readable data format used for transmitting structured data.
- **Example:**
```json
{
  "name": "DevOps",
  "category": "Automation"
}
```

### 🔑 **API Token (Authentication)**
- A **unique identifier** used for authenticating API requests.
- Similar to **passwords**, API tokens allow access to services without needing direct user credentials.

---

## ⚙️ DevOps Best Practices

### 🔄 **Continuous Integration (CI)**
- Automatically merging and testing code to detect issues early.
- Common tools: **Jenkins, GitHub Actions, GitLab CI/CD, CircleCI**.

### 🚀 **Continuous Deployment (CD)**
- Automating software releases to production environments.
- **CI/CD Pipelines** use tools like:
  - **ArgoCD** (Kubernetes)
  - **Terraform** (Infrastructure as Code)
  - **Ansible** (Configuration Management)

### 🏗️ **Infrastructure as Code (IaC)**
- Defining infrastructure using code instead of manual configuration.
- Common tools: **Terraform, CloudFormation, Pulumi**.

### 📊 **Monitoring & Logging**
- **Key Tools:**
  - **Prometheus & Grafana** → Metrics & Visualization
  - **ELK Stack (Elasticsearch, Logstash, Kibana)** → Centralized logging
  - **Datadog, Splunk, New Relic** → Application Performance Monitoring (APM)

### 🔒 **Security & DevSecOps**
- **Shift Left Security** → Embed security testing in CI/CD pipelines.
- **Common tools:**
  - **OWASP ZAP** → Web app security scanning.
  - **Trivy** → Container security scanning.
  - **HashiCorp Vault** → Secrets management.

---

## 🌎 Cloud & Containerization

### ☁️ **Cloud Platforms**
| Platform | Description |
|----------|------------|
| **AWS**  | Amazon Web Services |
| **GCP**  | Google Cloud Platform |
| **Azure** | Microsoft Cloud Services |

### 🐳 **Containers & Orchestration**
- **Docker** → Packages applications into containers.
- **Kubernetes** → Manages containerized applications at scale.

### 🚢 **Kubernetes Core Components**
| Component | Purpose |
|-----------|---------|
| **Pod** | Smallest deployable unit in Kubernetes |
| **Node** | A worker machine running containers |
| **Cluster** | A group of nodes running Kubernetes |
| **Deployment** | Manages the rollout of applications |
| **Service** | Exposes applications inside/outside the cluster |

---

## 🛠️ Common DevOps Tools

| Category | Tools |
|----------|------|
| **CI/CD** | Jenkins, GitHub Actions, GitLab CI/CD, CircleCI |
| **IaC** | Terraform, CloudFormation, Pulumi |
| **Config Management** | Ansible, Chef, Puppet, SaltStack |
| **Containers** | Docker, Kubernetes, Helm |
| **Monitoring** | Prometheus, Grafana, Datadog, ELK Stack |
| **Security** | OWASP ZAP, Trivy, HashiCorp Vault |

---

## 🔗 Useful DevOps Resources
- [DevOps Roadmap](https://roadmap.sh/devops)
- [AWS DevOps Guide](https://aws.amazon.com/devops/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)

---

This cheat sheet provides:
- **Definitions** of core DevOps concepts.
- **Best practices** for CI/CD, infrastructure, and security.
- **Cloud & containerization essentials**.
- **Common DevOps tools** for automation.

