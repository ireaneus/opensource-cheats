# 🧰 Ansible Guide

---

## 🔧 What is Ansible?

**Ansible** is an open-source **automation tool** used for:

- Configuration Management
- Application Deployment
- Provisioning
- Orchestration

It uses **YAML** for writing automation instructions (called *Playbooks*) and **SSH** to communicate with remote machines—**no agents needed**.

---

## 🧱 Ansible Architecture

```plaintext
+------------------+
| Control Machine  |  <---- You run Ansible here
+------------------+
        |
        | SSH / WinRM
        v
+------------------+      +------------------+
| Managed Node 1   | ...  | Managed Node N   |
+------------------+      +------------------+
```

- **Control Node**: Where you run Ansible.
- **Managed Nodes**: Machines being configured (no agents needed).
- **Inventory File**: List of managed nodes (hosts).
- **Modules**: Pre-written scripts Ansible uses to perform tasks.
- **Playbooks**: YAML files describing the desired state of systems.

---

## 🗂️ Inventory Example

```ini
# hosts.ini

[web]
web1.example.com
web2.example.com

[db]
db1.example.com ansible_user=admin ansible_port=2222
```

---

## 📜 Playbook Example

```yaml
# site.yml

- name: Install and start Apache
  hosts: web
  become: true

  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
        update_cache: yes

    - name: Ensure Apache is running
      service:
        name: apache2
        state: started
        enabled: true
```

---

## 🚀 Running Ansible

```bash
# Ping all hosts
ansible all -i hosts.ini -m ping

# Run a playbook
ansible-playbook -i hosts.ini site.yml
```

---

## 🛠️ Common Modules

| Module      | Purpose                          |
|-------------|----------------------------------|
| `apt`       | Manage Debian packages           |
| `yum`       | Manage RHEL/CentOS packages      |
| `service`   | Start/stop/restart services      |
| `copy`      | Copy files to remote machines    |
| `template`  | Deploy files using Jinja2        |
| `command`   | Run shell commands               |
| `shell`     | Run shell scripts                |
| `file`      | Manage permissions/ownership     |
| `git`       | Clone/update Git repositories    |
| `user`      | Manage user accounts             |

---

## 🧩 Ansible Concepts

- **Tasks**: A single action (e.g., install package).
- **Roles**: Reusable, modular units of configuration (collections of tasks, handlers, templates).
- **Handlers**: Tasks triggered by `notify` (e.g., restart service).
- **Facts**: System info collected from hosts (like OS, IP, etc).
- **Templates**: Jinja2-based dynamic files.
- **Variables**: Custom values for flexible playbooks.

---

## 📦 Folder Structure (Best Practice)

```plaintext
project/
├── inventory/
│   └── hosts.ini
├── playbooks/
│   └── site.yml
├── roles/
│   └── webserver/
│       ├── tasks/
│       │   └── main.yml
│       ├── templates/
│       └── handlers/
└── group_vars/
    └── web.yml
```

---

## 🔐 Ansible Vault (Encrypt Secrets)

```bash
# Create an encrypted file
ansible-vault create secrets.yml

# Edit the encrypted file
ansible-vault edit secrets.yml

# Use the vault in playbook
ansible-playbook site.yml --ask-vault-pass
```

---

## 🌐 Ad-Hoc Commands

```bash
# Install a package
ansible web -i hosts.ini -m apt -a "name=nginx state=present" --become

# Copy a file
ansible all -m copy -a "src=hello.txt dest=/tmp/hello.txt"

# Reboot servers
ansible all -m reboot --become
```

---

## 🧪 Tips & Best Practices

- Use **roles** for reusable and organized configurations.
- Store sensitive info with **Ansible Vault**.
- Keep your **inventory files modular** using groups.
- Test playbooks with `--check` (dry-run mode).
- Use `ansible-lint` for style checks.
- Use `tags` to selectively run tasks.

---

## 📚 Resources

- 📘 [Official Docs](https://docs.ansible.com/)
- 📘 [Ansible Galaxy (Community Roles)](https://galaxy.ansible.com/)
- 📗 [Ansible for DevOps (Book)](https://www.ansiblefordevops.com/)

---

```


