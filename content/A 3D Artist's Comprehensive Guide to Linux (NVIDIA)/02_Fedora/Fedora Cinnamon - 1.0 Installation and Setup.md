---
title: Fedora Cinnamon Spin - 1.0 Installation and Setup
permalink: fedora-install
draft: "false"
---
# Install Fedora
### Install Fedora
1. Select Language, Keyboard & Time.
2. Select SSD or NVMe to install to.
	1. (Optional) Encrypt drive with a passphrase (Good for laptops and travel computers.)
3. Set username and password.
4. Run installer and then reboot. (If dual booting, select your Fedora drive in the boot menu.)
# Fedora Drivers and Repos
### Update Fedora
Before doing anything else after installing a linux distribution, perform a system update to ensure everything is current prior to installing software and drivers.
1. `sudo dnf update && sudo dnf upgrade`
2. `reboot`
### Install Flathub Repo
https://flathub.org/en/setup/Fedora. This step is  necessary if you are not installing the main workstation editions. Since we are using the cinnamon spin, it is recommended.
1. `flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`
### Install RPM Fusion Repos
https://rpmfusion.org/Configuration
1. `sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm`
2. `sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1`
### Install NVIDIA Drivers
https://rpmfusion.org/Howto/NVIDIA
1. `sudo dnf update -y`
2. `sudo dnf install akmod-nvidia`
3. `sudo dnf install xorg-x11-drv-nvidia-cuda`
4. `reboot`
5. `nvidia-smi` to verify installation worked and check driver/cuda version.
# Software-Specific Requirements (Recommended anyways)
### Install Fuse 2
This step is necessary if you want to use DaVinci Resolve Studio on Linux.
1. `sudo dnf install fuse-libs`
### Set SELinux to Permissive
This step is necessary if you want to use Houdini and some server licensing on Fedora and RHEL distros.
1. `sudo nano /etc/selinux/config`
2. Change the line `SELINUX=enforcing` to `SELINUX=permissive`
3. Ctrl + S, Ctrl + X
4. `reboot`

### Proceed to [[Fedora Cinnamon - 2.0 Install Software Packages]]