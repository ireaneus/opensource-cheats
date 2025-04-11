# 🧰 Ansible Installation & Bootstrap Setup Guide

This guide walks you through installing Ansible, configuring your environment, and bootstrapping managed hosts with a dedicated automation user.

---

## 📦 Step 1: Install Ansible on Your Control Node

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

---

## 📁 Step 2: Set Up Project Structure

Create your working project directory:

```bash
mkdir -p ~/Public/ansible-project/playbooks
cd ~/Public/ansible-project
```

Add an Ansible config file:

```ini
# ansible.cfg
[defaults]
inventory = hosts.ini
remote_user = ansible
host_key_checking = False
private_key_file = ~/.ssh/id_rsa

[privilege_escalation]
become = True
become_method = sudo
```

---

## 🖥️ Step 3: Create and Edit Inventory File

Create `hosts.ini`:

```ini
[bootstrap]
laptop1 ansible_host=192.168.12.35 ansible_user=david

[control]
ansible_control ansible_host=192.168.12.63 ansible_user=ansible

[remote]
laptop1 ansible_host=192.168.12.35 ansible_user=ansible

[local]
localhost ansible_connection=ssh ansible_user=ansible

[all:children]
bootstrap
control
remote
local

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

> ⚠️ During bootstrap, use `ansible_user=david` under `[bootstrap]`, then switch back to `ansible_user=ansible` after the `ansible` user is configured.

---

## 🔐 Step 4: Confirm SSH Key Access (Passwordless)

Ensure the `david` user can connect to each target system **without password**:

```bash
ssh david@192.168.12.35
```

If it works, you’re good to bootstrap.

---

## 🚀 Step 5: Bootstrap the `ansible` User with a Playbook

### File: `playbooks/bootstrap-ansible-user.yml`

```yaml
---
- name: Bootstrap ansible user on managed hosts
  hosts: bootstrap
  become: true
  vars:
    ansible_ssh_pub_key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
    new_user: ansible

  tasks:
    - name: Create ansible user
      user:
        name: "{{ new_user }}"
        shell: /bin/bash
        groups: sudo
        append: yes
        create_home: yes

    - name: Create .ssh directory
      file:
        path: "/home/{{ new_user }}/.ssh"
        state: directory
        mode: '0700'
        owner: "{{ new_user }}"
        group: "{{ new_user }}"

    - name: Copy SSH key for ansible user
      authorized_key:
        user: "{{ new_user }}"
        key: "{{ ansible_ssh_pub_key }}"
        state: present

    - name: Add passwordless sudo privileges
      copy:
        dest: "/etc/sudoers.d/{{ new_user }}"
        content: "{{ new_user }} ALL=(ALL) NOPASSWD:ALL\n"
        owner: root
        group: root
        mode: '0440'
```

---

## 🧪 Step 6: Run Bootstrap (Dry-Run Optional)

### Dry-run test:
```bash
ansible-playbook -i hosts.ini playbooks/bootstrap-ansible-user.yml -u david --check --diff
```

### Run for real:
```bash
ansible-playbook -i hosts.ini playbooks/bootstrap-ansible-user.yml -u david
```

---

## ✅ Step 7: Update `hosts.ini` to Use the `ansible` User

```ini
[remote]
laptop1 ansible_host=192.168.12.35 ansible_user=ansible
```

Now you're ready to automate with the new dedicated `ansible` user.

---

## 🧪 Step 8: Test All Systems

```bash
ansible all -m ping
```

or specify the inventory directly:

```bash
ansible -i hosts.ini all -m ping
```

You should get `pong` responses from all your systems.

---

## Ansible Options:

| Arguments | Description
| --- | --- |
| -v    --verbose | |
| -i    --inventory=Path | # hosts file |
| --private-key=Priv_key_file | |
| -m    --module-name | |
| -M directory | # loads module directory |
| -a arguments | # to pass to module |
| -k    --ask-pass | # ssh password |
| -K    --ask-sudo-pass |
| -o    --one-line |
| -s    --sudo |
| -u    --remote_user= |
| -U    --sudo-user|
| -c    --connection= | # ssh or local |
| -l    --limit subset |
| -l~REGEX | # limits hosts with regex pattern |

## Examples from the host file:

```ini
some_host         ansible_port=2222     ansible_user=manager
aws_host          ansible_ssh_private_key_file=/home/example/.ssh/aws.pem
freebsd_host      ansible_python_interpreter=/usr/local/bin/python
ruby_module_host  ansible_ruby_interpreter=/usr/bin/ruby.1.9.3
```

## ansible modules:

```bash
[user@server1] ansible -m setup all            # 'inventory' of all systems
[user@server1] ansible -m ping all             # 'ping' inventory
[user@server1] ansible -m service -a 'name=httpd state=started'     # 'service'
```

## Non SSH connection types:

`local` - This connector can be used to deploy the playbook to the control machine itself:

`docker` - This connector deploys the playbook directly into Docker containers using the local Docker client. Following parameters are processed by this connector:  

`ansible_host` - The name of the Docker container to connect to:  

`ansible_user` - The user name to operate within the container. The user must exist inside the container:  

`ansible_become` - If set to true the become_user will be used to operate within the container:  

`ansible_docker_extra_args` - Could be a string with any additional arguments understood by Docker, which are not command specific. This parameter is mainly used to configure a remote Docker daemon to use:

### Here is an example of how to instantly deploy to created containers:

```yaml
- name: create jenkins container
  docker:
    name: my_jenkins
    image: jenkins

- name: add container to inventory
  add_host:
    name: my_jenkins
    ansible_connection: docker
    ansible_docker_extra_args: "--tlsverify --tlscacert=/path/to/ca.pem --tlscert=/path/to/client-cert.pem --tlskey=/path/to/client-key.pem -H=tcp://myserver.net:4243"
    ansible_user: jenkins
  changed_when: false

- name: create directory for ssh keys
  delegate_to: my_jenkins
  file:
    path: "/var/jenkins_home/.ssh/jupiter"
    state: directory
```

```bash
vars playbook: `--extra-vars "varname1= varname2="`

system facts: `ansible host -m setup -a 'filter=*ipv4'`
```

## Q: What is Ansible Tower:

> Ansible is classified as a web-based solution which makes Ansible very easy to use. It is considered to be or acts like a hub for all of your automation tasks. The tower is free for usage till 10 nodes.

## Q: Please define what is Ansible Galaxy:

> Ansible Galaxy refers to the website Galaxy where the users will be able to share all the roles to a CLI ( Command Line interface) where the installation, creation, and managing of roles happen

## Q: What does Fact mean in Ansible?

> The term “Facts” is commonly used in Ansible environment. They are described in the playbooks areas where it displays known and discovered variables about the system.  Facts are used to implement conditionals executions and also used for getting ad-hoc information of the information.
