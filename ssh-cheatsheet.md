# 🛡️ SSH Cheatsheet

## 📑 Table of Contents

- [🔧 Basic SSH Usage](#-basic-ssh-usage)
- [⚙️ SSH Config (`~/.ssh/config`)](#️-ssh-config-sshsshconfig)
- [🔐 Key-Only Login Setup (Disables Password)](#-key-only-login-setup-disables-password)
- [🧠 Known Hosts](#-known-hosts)
- [🔀 ProxyJump (SSH via Jump Host)](#-proxyjump-ssh-via-jump-host)
- [🛠 Useful SSH Features](#-useful-ssh-features)
- [📦 File Transfers](#-file-transfers)
- [🖥 Remote Commands and Scripting](#-remote-commands-and-scripting)
- [🧰 SSH Server Setup & Management](#-ssh-server-setup--management)
- [🔐 Host Restrictions](#-host-restrictions)
- [🧪 Miscellaneous](#-miscellaneous)
- [📚 Resources](#-resources)


## 🔧 Basic SSH Usage

```bash
# Connect to a server
ssh user@example.com

# Connect using a PEM key (make sure it has 0600 permissions)
ssh -i ~/.ssh/file.pem user@example.com

# Connect to a host defined in ~/.ssh/config
ssh myserver
```

---

## ⚙️ SSH Config (`~/.ssh/config`)

```bash
Host myserver
    HostName 192.168.1.100
    User david
    IdentityFile ~/.ssh/id_ed25519
    Port 22
    ForwardAgent yes
```

Use it like:

```bash
ssh myserver
scp file.txt myserver:/tmp/
```

---

## 🔐 Key-Only Login Setup (Disables Password)

### On the client:
```bash
ssh-keygen -t ed25519
ssh-copy-id user@server
```

### On the server:
Edit `/etc/ssh/sshd_config`:

```ini
PasswordAuthentication no
PubkeyAuthentication yes
```

Then restart SSH:

```bash
sudo systemctl restart ssh
```

---

## 🧠 Known Hosts

SSH stores trusted server fingerprints in:

```bash
~/.ssh/known_hosts
```

Remove a problematic entry:

```bash
ssh-keygen -R example.com
```

---

## 🔀 ProxyJump (SSH via Jump Host)

```bash
# ~/.ssh/config
Host internal
    HostName internal.server.local
    User user
    ProxyJump jumpuser@jumphost.example.com
```

Connect using:

```bash
ssh internal
```

---

## 🛠 Useful SSH Features

```bash
# Forward your SSH authentication agent
ssh -A user@example.com

# X11 forwarding (GUI apps)
ssh -X user@example.com
ssh -X -t user@example.com 'firefox'

# SOCKS proxy (localhost:9999)
ssh -D 9999 user@example.com

# Port forwarding: localhost:8080 to remote:5000
ssh -L 8080:remote.example.com:5000 user@jump.example.com -N
```

---

## 📦 File Transfers

```bash
# Copy from local to remote
scp file.txt user@example.com:/path/

# Rsync over SSH
rsync -avz ./stuff/ user@example.com:/path/stuff/
```

---

## 🖥 Remote Commands and Scripting

```bash
# Run single command remotely
ssh user@server 'uptime'

# Run multiple commands
ssh user@server << EOF
date
hostname
EOF

# Run local script remotely
cat script.sh | ssh user@server
```

---

## 🧰 SSH Server Setup & Management

```bash
# Install SSH server
sudo apt install openssh-server

# Check if SSH is listening on port 22
nc -v -z 127.0.0.1 22

# Restart SSH server
sudo systemctl restart ssh

# Change default SSH port in /etc/ssh/sshd_config
Port 2222
```

---

## 🔐 Host Restrictions

```ini
# Restrict access to subnet in /etc/hosts.allow
sshd : 192.168.0.0/24

# Deny all others
/etc/hosts.deny
sshd : ALL
```

---

## 🧪 Miscellaneous

```bash
# Create a SOCKS proxy
ssh -D 9999 user@example.com

# Check if sshd.socket is active (on-demand socket)
systemctl status sshd.socket
```

---

## 📚 Resources

- https://www.ssh.com/academy/ssh/config
- https://www.tecmint.com/5-best-practices-to-secure-and-protect-ssh-server/
- https://man.openbsd.org/ssh_config
