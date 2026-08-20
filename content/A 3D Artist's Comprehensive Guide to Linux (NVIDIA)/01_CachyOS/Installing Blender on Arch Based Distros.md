---
title: Installing Blender on Arch Based Distros
permalink: cachyos-blender
draft: "false"
---
Arch Blender repos are pretty on-top of the Blender updates, so you can usually trust the `pacman` repo if you are looking for the latest Blender version.

`sudo pacman -S blender`

> [!warning] Pacman vs Flatpak Python for Add-ons
> Pacman/Arch blender relies on system python installation. If you use a lot of addons, you may run into issues. In that case, `sudo pacman -R blender` to uninstall blender and use Flatpak version instead. It packs its own python libraries into blender to ensure this is not an issue. `flatpak install org.blender.Blender/x86_64/stable`. I PREFER THE FLATPAK AT THE MOMENT.

If you want the most recent Blender LTS version as well then you can install it via the AUR `yay` or `paru` repo. (This one also has its own python so addons will not run into that issue here.)

`paru -S blender-lts-bin`

> [!warning] Keybind Conflict
> Be sure if you are installing with gnome, kde or cinnamon, that you swap the alt-mouse with super-mouse to avoid blender navigation conflicts. See the [Blender Documentation]( https://docs.blender.org/manual/en/latest/getting_started/installing/linux.html) for details.

> [!tip] Auto Updates
> All of these will update on their own, although whether that happens automatically will depend on your system update settings and your system maintenance configurations on Arch Linux or CachyOS.
> 
> You can update your system with `sudo pacman -Syu` or in run `cachyos-hello` and select update system to update all Pacman, AUR and Flatpak installations.
