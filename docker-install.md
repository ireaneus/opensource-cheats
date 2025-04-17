# 🐳 Docker Installation Guide (Linux)

This guide walks you through installing the latest Docker Engine and Docker CLI using the official Docker repositories.

---

## 📑 Table of Contents

- [🔧 Prerequisites](#-prerequisites)
- [📥 Install Docker on Ubuntu / Debian](#-install-docker-on-ubuntu--debian)
- [📥 Install Docker on RHEL / CentOS / Fedora](#-install-docker-on-rhel--centos--fedora)
- [⚙️ Post-Install Steps](#️-post-install-steps)
- [🚀 Verify Installation](#-verify-installation)
- [🧪 Optional: Install Docker Compose Plugin](#-optional-install-docker-compose-plugin)
- [🧹 Uninstall Docker](#-uninstall-docker)

---

## 🔧 Prerequisites

- A 64-bit supported Linux OS
- `sudo` or root privileges
- Internet access

---

## 📥 Install Docker on Ubuntu / Debian

```bash
# 1. Update existing packages
sudo apt update && sudo apt upgrade -y

# 2. Remove older Docker versions
sudo apt remove docker docker-engine docker.io containerd runc

# 3. Install required packages
sudo apt install -y apt-transport-https ca-certificates curl gnupg lsb-release

# 4. Add Docker's GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# 5. Add Docker's repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 6. Install Docker Engine
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

---

## 📥 Install Docker on RHEL / CentOS / Fedora

```bash
# 1. Remove old Docker versions
sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine

# 2. Install required packages
sudo yum install -y yum-utils

# 3. Add Docker repository
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# 4. Install Docker Engine
sudo yum install -y docker-ce docker-ce-cli containerd.io

# 5. Start Docker
sudo systemctl start docker
sudo systemctl enable docker
```

---

## ⚙️ Post-Install Steps

**Optional but recommended**:

```bash
# Create a docker group (if not exists)
sudo groupadd docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Apply group changes (log out and back in or run:)
newgrp docker
```

---

## 🚀 Verify Installation

```bash
docker --version
docker run hello-world
```

You should see a message saying Docker is working correctly.

---

## 🧪 Optional: Install Docker Compose Plugin

```bash
# Install Docker Compose v2 (as a plugin)
sudo apt install docker-compose-plugin

# Test it
docker compose version
```

For v1 (deprecated):
```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

---

## 🧹 Uninstall Docker

```bash
# Remove Docker packages
sudo apt remove docker-ce docker-ce-cli containerd.io

# Optional: remove all images, containers, volumes, and config
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

---

## 📚 References

- [Docker Docs](https://docs.docker.com/engine/install/)
- [Docker GitHub Releases](https://github.com/docker/compose/releases)

---

