---
title: AlmaLinux 9 - 2.0 Installing Creative Packages
permalink: almalinux-packages
draft: "false"
---
# Familiarize Yourself with Bash Installation
Linux distros include a [[Package Manager]] for installing, updating, and removing software. AlmaLinux uses [dnf](https://docs.fedoraproject.org/en-US/quick-docs/dnf/) and [Flatpak](https://flatpak.org/). To install a package, use `sudo dnf install [pkg-name]` or `flatpack install [pkg-name]`.

---
# Install Common Packages
> [!tip] Bundle dnf Installs
> You can install multiple packages from `dnf` by placing a space between each one: `sudo dnf install nodejs npm` To remove, swap `install` with `remove` -> `sudo dnf remove npm`
 
  Lets say that I want to install an **office suite, chrome, obsidian notes, obs studio and a pdf viewer** all in one go.

`sudo dnf install onlyoffice-bin chromium code obsidian obs-studio okular`

Enter your password and all packages download at once. See [[Common Package List for Linux Installs]] for other software I commonly install.

---
# Installing Creative Packages
Once your AlmaLinux installation is prepped, Start installing the software you need for your workflow. The packages I have included on this page are relevant to my own work and may look different than another persons desired packages.

Blender - [[Installing Blender on AlmaLinux & RHEL Based Distros]]

[[DaVinci Resolve]] - [[Installing DaVinci Resolve on RHEL Based Distros]]

Houdini - [[Installing Houdini on AlmaLinux & RHEL Based Distros]]

Natron - [[Installing Natron on Linux]]

*COMING SOON* - Nuke - [[Installing Nuke on Linux]]

*COMING SOON* - Unreal Engine - [[Installing Unreal Engine 5 on RHEL Linux]]

VSCodium - [[Installing VSCodium on AlmaLinux & RHEL based distros]]

