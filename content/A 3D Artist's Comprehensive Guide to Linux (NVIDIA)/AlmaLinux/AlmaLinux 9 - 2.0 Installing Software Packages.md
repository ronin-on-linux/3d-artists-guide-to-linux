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
 
  Lets say that I want to install chrome.

`sudo dnf install chromium`

Lets say that I want to install an **office suite, obsidian notes, vscode, obs studio** all in one go using Flatpak. 

`flatpak install onlyoffice obsidian vscodium com.obsproject.Studio `

Hit enter and all packages will download at once. See [[Common Package List for Linux Installs]] for other software I commonly install.
> [!info] If you don't know the address of the application either type its name as you know it and it will detect it, or use `flatpak search [guessed name]` and it will list the correlated address to type in.

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

