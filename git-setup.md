Perfect — let’s consolidate everything into a **clean, bulletproof procedure** for uploading your `ansible-project` to GitHub using **SSH**, including:

- SSH key setup & agent
- Git identity configuration
- GitHub repo linking via SSH
- Commit & push

---

# 🚀 Upload `ansible-project` to GitHub Using SSH

---

## ✅ Step 1: Configure Git Identity

Tell Git who you are (only once per system):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

> This info will show in GitHub commits and logs.

---

## ✅ Step 2: Ensure Your SSH Key Is Loaded

If you're using a non-default SSH key (like `id_ed25519`):

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

> Confirm the key is added:
```bash
ssh-add -l
```

If you see your key listed, you're good.

---

## ✅ Step 3: Test GitHub SSH Access

```bash
ssh -T git@github.com
```

Expected result:
```bash
Hi your-username! You've successfully authenticated...
```

If it asks to confirm the GitHub host key, type `yes`.

---

## ✅ Step 4: Initialize Git in Your Project

From inside your Ansible project folder:

```bash
cd ~/Public/ansible-project

# Optional: Add a README if you haven’t yet
echo "# ansible-project" >> README.md

git init
git add .
git commit -m "Initial commit: Ansible project setup"
```

---

## ✅ Step 5: Link to GitHub Repo Using SSH

Add your GitHub repo as the `origin` using **SSH URL**:

```bash
git remote add origin git@github.com:ireaneus/ansible-project.git
```

> You can verify with:
```bash
git remote -v
```

---

## ✅ Step 6: Push to GitHub

```bash
git branch -M main
git push -u origin main
```

Done! Your Ansible project is now live on GitHub 🎉

---

## 🧠 Optional Extras

### Ignore local cache & secrets:

```bash
cat <<EOF > .gitignore
*.retry
*.log
*.swp
__pycache__/
*.pyc
.venv/
vault_pass.txt
EOF

git add .gitignore
git commit -m "Add .gitignore"
git push
```

---

