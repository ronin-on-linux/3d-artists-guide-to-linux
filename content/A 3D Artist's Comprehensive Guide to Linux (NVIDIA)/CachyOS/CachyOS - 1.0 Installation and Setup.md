---
title: CachyOS - 1.0 Installation and Setup
permalink: cachyos-install
draft: "false"
---
# Install CachyOS
1. Select Language, Timezone and Keyboard Layout.
2. Select default Limine bootloader unless you know what that is.
3. Select disk from top drop down to install. Erase disk. Select disk encryption if you are privacy pilled.
4. Select a desktop environment. I will choose Cinnamon because its `X11` making it the more compatible with all 3D software, its what I use curretnly and looks familiar to Windows users.
	1. Coming from windows: KDE(Wayland) or Cinnamon(X11)
	2. Coming from Mac: KDE(Wayland) or Gnome(Wayland)
	3. You like to code: MangoWM(Wayland) or Hyprland(Wayland)
> [!warning] Desktop Environment
> Your choice of desktop environment usually is not a big deal, UNLESS you are going to need to run UE5 or Houdini. These are notorious for running into all kinds of issues because of what we call desktop compositors interfering with software processes.
> 
> I am currently in the process of researching the best desktop environments to better recommend two or three top options that will either give you maximum compatibility or a balanced compatibility with more modern look and feel.
5. Package Selection
	1. Printer & HP Support
	2. Uncheck Cinnamon `lightdm-gtk-greeter`
	3. LDXE `light-dm-slick-greeter`
	4. Under Gnome Apps, `showtime`, `gnome-disk-utility`, `gnome-calculator` and `file-roller`
6. Create Username/Password
7. Install and reboot.

---
# Initial Start
### Update System
1. Open `Hello CachyOS` from the desktop menu.
2. Select `Apps & Tweaks`
3. Select `System Update`
	(or)
4. Open terminal `CTRL + ALT + T`
5. `sudo pacman -Syu`
### Rank Mirrors
1. Open `Hello CachyOS` from the desktop menu.
2. Select `Apps & Tweaks`
3. Select `Rank Mirrors` option.
### Install Gaming Packages 
This installs Steam and additional dependencies to run graphically intensive applications beyond the graphics drivers.

1. Open `Hello CachyOS` from the desktop menu.
2. Select `Apps & Tweaks`
3. Select `Install Gaming Packages`
### Firewall 
1. Open terminal `CTRL + ALT + T` (you can also just search for it in the start menu)
2. `ufw enable` to verify firewall is running.

---
# Set Dark Theme in Cinnamon or KDE
1. Menu -> System Settings (right click to pin it to panel) -> Theme -> Dark (or, if simple not working), -> Advanced -> Adwaita-Dark, Papirus-Dark
2. Theme -> Settings -> Prefer Dark Mode
3. In main Settings -> Background -> Choose something dark.
4. If you would like to polish Cinnamon a bit more, see [[CachyOS - 1.1 Optional Cinnamon Mint-Y Appearance]]

See [[CachyOS - 2.0 Installing Software Packages]] for next steps.
