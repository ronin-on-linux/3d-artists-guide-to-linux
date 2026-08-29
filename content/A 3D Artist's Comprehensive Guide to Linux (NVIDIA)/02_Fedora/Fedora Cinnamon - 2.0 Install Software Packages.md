---
title: Fedora Cinnamon - 2.0 Install Software Packages
permalink: fedora-packages
draft: "false"
---
# Familiarize Yourself with Bash Installation
Linux distros include a [[Package Manager]] for installing, updating, and removing software. Fedora uses [dnf](https://docs.fedoraproject.org/en-US/quick-docs/dnf/) and [Flatpak](https://flatpak.org/). To install a package, use `sudo dnf install [pkg-name]` or `flatpack install [pkg-name]`.

> [!info] App Store
> Software packages can also be installed via the software app which may be a more simple or appealing method for some.

---
# Install Common Packages
Lets say that I want to install chrome.

`sudo dnf install chromium`

> [!tip] Bundle dnf Installs
> You can install multiple packages from `dnf` by placing a space between each one: `sudo dnf install nodejs npm` To remove, swap `install` with `remove` -> `sudo dnf remove npm`

Lets say that I want to install an **office suite, obsidian notes, vscode, obs studio** all in one go using Flatpak. 

`flatpak install onlyoffice obsidian vscodium com.obsproject.Studio `

Hit enter and all packages will download at once. See [[Common Package List for Linux Installs]] for other software I commonly install.
 
---
# Installing Creative Packages
Once your Fedora installation is up, start installing the software you need for your workflow. The packages I have included on this page are relevant to my own work and may look different than another persons desired packages.

Blender - [[Installing Blender on Linux]]

[[DaVinci Resolve]] - [[../Other Useful Resources/DaVinci Resolve/Installing DaVinci Resolve on Linux]]

Houdini - [[Installing Houdini on Linux]]

Natron - [[Installing Natron on Linux]]

*COMING SOON* - Nuke - [[../Other Useful Resources/Installing Nuke on Linux]]

*COMING SOON* - Unreal Engine - [[Installing Unreal Engine 5 on RHEL Linux]]

VSCodium - [[Installing VSCodium on AlmaLinux & RHEL based distros]]

