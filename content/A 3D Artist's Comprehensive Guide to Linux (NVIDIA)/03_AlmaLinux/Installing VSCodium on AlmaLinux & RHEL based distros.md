---
title: Installing VSCodium on AlmaLinux & RHEL based distros
permalink: almalinux-vscode
draft: "false"
---
To install VSCodium, you can either install it via Flatpak, or if you want a native installation for locally installed sdk compatibility, you will need to add the repo yourself.

# Flatpak Installation
1. `flatpak install com.vscodium.codium`
# Native Installation
If you absolutely need VS Code natively, you need to add the repo yourself.
1. To add the repo, enter this into your terminal
``` bash
sudo tee /etc/yum.repos.d/vscodium.repo << 'EOF'
[vscodium]
name=VSCodium
baseurl=https://paulcarroty.gitlab.io/vscodium-deb-rpm-repo/rpms/
enabled=1
gpgcheck=1
gpgkey=https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg
EOF
```
2. Then, run `sudo dnf install codium`

