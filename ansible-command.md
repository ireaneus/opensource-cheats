You can run the ZSH setup script **as an ad-hoc Ansible command** in two steps:

---

## ✅ 1. Copy the Script to the Remote System

Assuming your script is saved at:  
`~/Public/ansible-project/files/setup-zsh.sh`

Run this to copy it to `/tmp` on your target host(s):

```bash
ansible all -i hosts.ini -m copy \
  -a "src=files/setup-zsh.sh dest=/tmp/setup-zsh.sh mode=0755"
```

---

## ✅ 2. Run the Script on the Remote System

Now run the script as the **target user** (e.g., `david`, `ansible`, etc.):

```bash
ansible all -i hosts.ini -a "/tmp/setup-zsh.sh" -b -u david
```

Here’s what the options mean:
- `-a`: the shell command to run
- `-b`: use `become` to elevate privileges (run as root)
- `-u david`: connect as `david` (or use your actual SSH user)

If you want to run the script **as the remote user** (not root), but with `sudo` where needed (as built into the script), add `--become-user`:

```bash
ansible all -i hosts.ini -a "/tmp/setup-zsh.sh" -b --become-user=david -u david
```

---

## 💡 Optional: Limit to a Specific Host or Group

```bash
ansible laptop1 -i hosts.ini -a "/tmp/setup-zsh.sh" -b --become-user=david -u david
```

---

