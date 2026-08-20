---
title: AlmaLinux 9 - 1.0 Installation and Setup
permalink: almalinux-install
draft: "false"
---
# Install AlmaLinux 9
1. Connect to WiFi. (Not required, but allows for latest bug fixes, etc. Dismiss the kwallet notification)
2. Click on *Install to Hard Drive*.
3. Select Keyboard Layout to continue.
4. Set Time & Date.
5. Disable KDUMP.
6. Select Network & Hostname to give your computer a name.
7. Leave Root Password *disabled*.
8. Choose *Installation Destination*.
	1. Select Target SSD/NVMe/HDD drive. 
		1. *Be sure you only see ONE CHECKMARK on your desired drive. You can accidentally check more than one drive by clicking on another. You can deselect a drive by clicking on it again.*
	2. Encrypting your drive is recommended but not required. (This adds a step at boot to unlock your drive with a passphrase).
	3. Reclaim Drive space
		1. Select top of drive hierarchy.
		2. Select Delete All.
		3. Select Reclaim Space.
9. User Creation
	1. Add name and username.
	2. Make Administrator.
	3. Set a strong password.
10. Begin Installation
11. Once its finished, exit and reboot.
# Initial Start
### Accept EULA, Set KDE to X11 and Log In
1. On first reboot, accept the EULA and select *Finish Configuration*.
2. On the login screen, BEFORE signing in: 
	1. Select KDE X11 desktop in the bottom left corner.
	2. Login
3. Click through the Welcome dialogue, and then close it.
### Update System
`sudo dnf upgrade`
### Install Third Party Repositories
1. Install RPM Fusion Repo. See RHEL section on their website for more. https://rpmfusion.org/Configuration
	1. `sudo dnf install -y --nogpgcheck https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-$(rpm -E %rhel).noarch.rpm`
	2. `sudo dnf install -y --nogpgcheck https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-$(rpm -E %rhel).noarch.rpm`
2. Enable RPM Fusion Repo `dnf repolist enabled`
3. Update package manager with `sudo dnf update`
4. Install Flatpak https://flatpak.org/setup/Fedora (DON'T SKIP, you will need this for Blender on AlmaLinux 9)!
	1. `sudo dnf install flatpak`
	2. Then follow directions from flatpak to install flathub repo https://flathub.org/en/setup/AlmaLinux
5. Reboot system `reboot`
### Install NVIDIA Drivers
See https://wiki.almalinux.org/documentation/nvidia.html for more details.
1. `sudo dnf install almalinux-release-nvidia-driver`
2. `sudo dnf install nvidia-open`
3. `sudo dnf install nvidia-driver-cuda`
4. `reboot`
5. Check if it was successful with `nvidia-smi`

![[Screenshot from 2026-08-11 10-52-47.png]]
> [!info] Failure to install NVIDIA drivers or Buggy Drivers
> Occasionally, this method can fail around the time of AlmaLinux updates (e.g. v9.7 -> v9.8). In this case, you might have better luck installing the RPM NVIDIA packages until it is patched by AlmaLinux. (I frequently use the RPM Fusion NVIDIA drivers instead if I encounter any issues with the AlmaLinux NVIDIA version).
>  1. `sudo dnf install akmod-nvidia xorg-x11-drv-nvidia-cuda`
> 2. `reboot`
> 3. Check success with `nvidia-smi`
> 
> Technically, you can still install them anyways by adding `--nobest` to the end of the command. This should eliminate the issue for you, but may not install the latest drivers and have a few bugs.
> 4. `sudo dnf install nvidia-open --nobest`
> 5. `sudo dnf install nvidia-driver-cuda --nobest`
### Install Multimedia Drivers
See https://rpmfusion.org/Howto/Multimedia?highlight=%28%5CbCategoryHowto%5Cb%29 for more in depth instructions.
1. `sudo dnf swap ffmpeg-free ffmpeg --allowerasing`
2. `sudo dnf update @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin`
3. `sudo dnf install intel-media-driver` (Replace with AMD if you have AMD hardware).
4. `sudo dnf install libva-nvidia-driver` (Replace with AMD if you have AMD hardware).

**Proceed to [[AlmaLinux 9 - 2.0 Installing Software Packages]]**
