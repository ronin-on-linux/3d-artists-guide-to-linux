---
title: CachyOS - 2.0 Installing Creative Packages
permalink: cachyos-packages
draft: "false"
---
# Familiarize Yourself with Bash Installation
Linux distros include a [[Package Manager]] for installing, updating, and removing software. CachyOS uses [pacman](https://wiki.archlinux.org/title/AUR_helpers) and [Flatpak](https://flatpak.org/). To install, use `sudo pacman -S [pkg-name]` and `flatpak install [pkg.Name.name]`.

> [!tip] Beginner Tip - Bundle Installs
> You can install multiple packages by placing a space between each one: `sudo pacman -S nodejs npm` 

To remove, swap `-S` for `-R` -> `sudo pacman -R npm`

---
# Install Common Packages
Lets say that I want to install an **office suite, chrome, vscode, obsidian notes and a pdf viewer** all in one go.

`sudo pacman -S onlyoffice-bin chromium code obsidian okular`

Enter your password and all packages download at once. See [[Common Package List for Linux Installs]] for other software I commonly install.

---
# Install Creative Packages
Blender - [[Installing Blender on Linux]]

DaVinci Resolve - [[Installing DaVinci Resolve on Linux]]

Houdini - [[Installing Houdini on Linux]]

Natron - [[Installing Natron on Linux]]

Unreal Engine - [[Installing Unreal Engine 5 on CachyOS]]

*COMING SOON* - Nuke - [[../Other Useful Resources/Installing Nuke on Linux]]

*COMING SOON* - Substance Painter - [[Installing Substance Painter Perpetual on Linux with Steam]]

Affinity - [[Affinity on Linux]]