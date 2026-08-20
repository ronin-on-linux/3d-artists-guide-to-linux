---
title: Download ISO and Create Bootable USB
permalink: bootable-usb
draft: "false"
---
# Set Up Bootable USB
### Fedora Cinnamon Spin Download Link
I recommend choosing Fedora with the Cinnamon environment. Its been the most simple, stable and traditional desktop experience I have experienced across distros and hardware. Its also still x11, meaning it reduces the number of things you have to troubleshoot to get working with your favorite software.
1. https://fedoraproject.org/spins/cinnamon/
### Create Bootable Media
1. (Optional) Download desired ISO if not Fedora: [CachyOS](https://cachyos.org/download/) or [AlmaLinux 9 Live](https://almalinux.org/get-almalinux/#Live_Media-x86_64-9) 
2. Download ISO/USB Writer
	1. On Windows, `Rufus` from https://rufus.ie/en/
	2. On Linux, `Disks` with `gnome-disk-utility`
	3. On Mac, Balena Etcher from https://etcher.balena.io/
3. Insert `USB Drive`, select it in Rufus (or preferred USB Writer) and select ISO. Select Start.
	1. Restore Disk Image in `gnome-disk-utility`.
4. Safely eject and remove your usb drive.
### Boot to Live Installer
1. Insert USB into the computer that you want to install Linux.
2. Turn on and spam the boot menu key until the selection menu appears. Select your bootable Linux USB drive.
	1. Look up which F key is the boot menu key on your computer. (Often it’s either the `DEL`, `F2` or `F11` key).
3. The Linux live desktop should load up now.
4. Connect to the internet and run installer.
### Proceed to [[Fedora Cinnamon - 1.0 Installation and Setup]] for next steps.

Also see [[CachyOS - 1.0 Installation and Setup]] or [[AlmaLinux 9 - 1.0 Installation and Setup]]
