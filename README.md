# 🧰 Fedora KDE Automation

This playbook automates the setup of a Fedora KDE workstation using Ansible.

It includes:

- Dnf and Flatpak configuration
- Dotfiles fetching
- Installation of common apps, terminal tools, development software, docker
- RPM-based proprietary tools like Slack, Chrome, GitKraken
- KDE-specific package adjustments

---

## 🚀 Quick Start

### First-time setup:

```bash
ansible-playbook main.yml --ask-become-pass -e first_run=true
```

This will run all key tasks: environment setup, dotfiles, software, docker, etc.

---

## 🏷 Run specific sections with tags

You can run individual parts using tags — this bypasses the need for `first_run`:

| Feature                 | Tag           |
|-------------------------|---------------|
| Dnf and Flatpak config  | `environment` |
| Fetch dotfiles/home     | `home`        |
| Common software         | `common`      |
| Terminal tools          | `terminal`    |
| Zsh and shell setup     | `shell`       |
| KDE adjustments         | `kde`         |
| Development tools       | `development` |
| Docker install & config | `docker`      |
| Work RPM apps (Slack…)  | `work`        |

### Example:

```bash
ansible-playbook main.yml --ask-become-pass --tags docker
```

---

## ⚙️ Example with variable override

```bash
ansible-playbook main.yml --ask-become-pass \
  -e first_run=true \
  -e real_user=xaknick
```

---

## ✅ Notes

- Make sure your user is **not `root`** when running the playbook.
- You must have **ansible** and **git** installed.
- To make things faster, only include relevant tags or set `first_run: true` once.
