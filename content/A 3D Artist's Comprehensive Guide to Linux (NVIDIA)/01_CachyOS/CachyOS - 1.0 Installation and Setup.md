---
title: CachyOS - 1.0 Installation and Setup
permalink: cachyos-install
draft: "false"
---
<div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe 
    src="https://www.youtube.com/embed/s_cm_c8BxrM" 
    title="Turn Your Obsidian Notes Into A Website"
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" 
    allowfullscreen>
  </iframe>
</div>


# Install CachyOS
1. Select Language, Timezone and Keyboard Layout.
2. Select default Limine bootloader unless you know what that is.
3. Select disk from top drop down to install. Erase disk. Select disk encryption if you are privacy pilled.
4. Select a desktop environment. I suggest Cinnamon because its `X11` making it the more compatible with all 3D software, its what I use curretnly and looks familiar to Windows users.
5. Package Selection
	1. Printer & HP Support
	2. Under Gnome Apps, `loupe`, `gnome-disk-utility`, `gnome-calculator` and `file-roller`
	3. Under MATE, `celluloid`
6. Create Username/Password
7. Install and reboot.

---
# Initial Start
![[CachyOSHello_Hightlights.png]]
### Update System
1. Open `Hello CachyOS` from the desktop menu.
2. Select `Apps & Tweaks`
3. Select `System Update`
	(or)
4. Open terminal `CTRL + ALT + T`
5. `sudo pacman -Syu`
6. You may need to reboot after this update. (It will tell you with a popup notification if you will need to.)
### Rank Mirrors
1. Open `Hello CachyOS` from the desktop menu.
2. Select `Apps & Tweaks`
3. Select `Rank Mirrors` option.
### Install Gaming Packages 
This installs Steam and additional dependencies to run graphically intensive applications beyond the graphics drivers.
3. Open `Hello CachyOS` from the desktop menu.
4. Select `Apps & Tweaks`
5. Select `Install Gaming Packages`
### Verify NVIDIA Drivers are Working Properly
Cachy should have detected your GPU and the proper NVIDIA drivers should have been automatically installed.

`nvidia-smi`

You should see something like the example below.

![[Screenshot from 2026-08-11 10-52-47.png]]
### Install Flatpak
Flatpak sandboxes apps for easier version management and better security.
`sudo pacman -S flatpak flatseal`
### Install Software Specific Packages
1. `sudo pacman -S fuse2` Required to run Appimages and for DaVinci Resolve
2. `sudo pacman -S nemo-fileroller` Allows you to extract zip/compressed folders by right clicking items in the file browser.
### Firewall (Optional - Firewall should be running by default.)
1. Open terminal `CTRL + ALT + T` (you can also just search for it in the start menu)
2. `ufw enable` to verify firewall is running.

---
# Important Cinnamon Settings
### Window Settings (Important for Blender)
1. Menu -> System Settings -> Windows -> Behavior -> Special key to move and resize windows -> ***Change from ALT to `SUPER`*** (*This prevents cinnamon from interfering with ALT based shortcuts in Blender like loop selection, etc.)*
![[set-win-beh-super.png]]
2. Menu -> System Settings -> Windows -> Tiling -> ***`Enable` Maximize instead of tile on top edge.*** *(Quality of life/muscle memory)*
![[set-win-tile-max.png]]
### Dark Mode
1. Menu -> System Settings (right click to pin it to panel) -> Theme -> Dark (or, if simple not working), -> Advanced -> ***Adwaita-Dark, Papirus-Dark***
![[set-theme-dark.png]]
2. Theme -> Settings -> ***Prefer Dark Mode***
![[set-prefer-dark.png]]
3. In main Settings -> Background -> ***Choose something you like placed in your pictures folder.***
4. If you would like to polish Cinnamon a bit more, see ***[[CachyOS - 1.1 Optional Cinnamon Mint-Y Appearance]]***

### See [[CachyOS - 2.0 Installing Software Packages]] for next steps.
