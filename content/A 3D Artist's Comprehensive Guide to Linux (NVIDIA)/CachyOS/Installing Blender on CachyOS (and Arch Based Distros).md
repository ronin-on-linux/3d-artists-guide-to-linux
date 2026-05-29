---
title: Installing Blender on Arch Based Distros
permalink: cachyos-blender
draft: "false"
---
Arch Blender repos are pretty on-top of the Blender updates, so you can usually trust the `pacman` repo if you are looking for the latest Blender version.

`sudo pacman -S blender`

If you want the most recent Blender LTS version as well then you can install it via the AUR `yay` or `paru` repo.

`paru -S blender-lts-bin`

> [!warning] Keybind Conflict
> Be sure if you are installing with gnome, kde or cinnamon, that you swap the alt-mouse with super-mouse to avoid blender navigation conflicts. See the [Blender Documentation]( https://docs.blender.org/manual/en/latest/getting_started/installing/linux.html) for details.

> [!tip] Auto Updates
> Both of these will update on their own, although whether that happens automatically will depend on your system update settings and your system maintenance configurations on Arch Linux or CachyOS.
> 
> You can update your system with `sudo pacman -Syu`
