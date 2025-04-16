# 🖥️ Citrix Workspace on Ubuntu 24.04 with GUI Support

This guide installs Citrix Workspace App for Linux on Ubuntu 24.04 and resolves missing dependency issues (such as `libwebkit2gtk-4.0.so.37`) by temporarily backporting the WebKitGTK library from Ubuntu 22.04 (Jammy).

---

## ✅ Prerequisites

- Ubuntu 24.04 (Noble)
- Citrix Workspace `.deb` package (e.g. `icaclient_25.03.0.66_amd64.deb`)

---

## 🛠 Installation Steps

### 1. Add Jammy Repositories Temporarily

```bash
sudo apt-add-repository "deb http://us.archive.ubuntu.com/ubuntu jammy main"
sudo apt-add-repository "deb http://us.archive.ubuntu.com/ubuntu jammy-updates main"
sudo apt-add-repository "deb http://us.archive.ubuntu.com/ubuntu jammy-security main"
```

### 2. Install Required Library

```bash
sudo apt update
sudo apt install libwebkit2gtk-4.0-dev
```

> This will install `libwebkit2gtk-4.0.so.37`, needed by Citrix GUI.

---

### 3. Remove Temporary Jammy Repositories

```bash
sudo add-apt-repository -r "deb http://us.archive.ubuntu.com/ubuntu jammy main"
sudo add-apt-repository -r "deb http://us.archive.ubuntu.com/ubuntu jammy-updates main"
sudo add-apt-repository -r "deb http://us.archive.ubuntu.com/ubuntu jammy-security main"
```

---

### 4. Install Citrix Workspace

```bash
sudo dpkg -i icaclient_25.03.0.66_amd64.deb
sudo apt -f install -y
```

---

## 🚀 Launch Citrix Workspace GUI

```bash
/opt/Citrix/ICAClient/selfservice
```

If the GUI doesn't launch, check for:
- Missing dependencies: `libva-drm2`, `libva-x11-2`, `libidn11`, etc.
- EULA rejection: accept it via GUI or add `~/.ICAClient/eula.txt` with `EULA_ACCEPTED=YES`.

---

## 📎 Reference

[Citrix Workspace App for Linux - System Requirements](https://docs.citrix.com/en-us/citrix-workspace-app-for-linux/system-requirements)
```

---

