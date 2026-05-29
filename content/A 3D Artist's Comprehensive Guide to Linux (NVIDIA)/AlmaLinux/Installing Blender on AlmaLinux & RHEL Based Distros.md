---
title: Installing Blender on AlmaLinux & RHEL Based Distros
permalink: almalinux-blender
draft: "false"
---
It seems like the native dnf/Fedora repos lag behind the current blender releases, not to mention its missing some gpu compatibility, ***so I recommend the Flatpak/Flathub blender install or the blender website download.***

# Flatpak Install

> [!warning] Flatpack versions!
> If you are using Fedora, DO NOT choose the fedora project Flatpak. It has GPU detection issues and version lag. Choose the official flathub package for the latest blender version.

1. Run `flatpak install flathub org.blender.Blender` in the terminal or select the Flathub version in the Fedora GUI software manager.
2. If it does not show in your menu, then `reboot`
It should now show up in your menus. You can also run it in the terminal via the command:
`flatpak run org.blender.Blender`

To setup Blender, see my personal [[Blender Startup Configuration]] notes.
# Download & Install from Blender.org

Visit the [Blender Website](https://www.blender.org/download/) to download the latest version.

Unzip it to a folder you desire and run the blender executable from the folder.