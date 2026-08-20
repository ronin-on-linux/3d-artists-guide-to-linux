---
title: Affinity on Linux
permalink: linux-affinity-wine
draft: "false"
---
Most easily enabled by [Ryzendew on Github](https://github.com/ryzendew/Linux-Affinity-Installer) as an [Appimage download](https://github.com/ryzendew/Linux-Affinity-Installer/releases/tag/3.0.2) or a Py installer that included the option to install the individual deprecated versions as well as the unified version.
# Install Affinity via Python Installer
The Python installer requires Qt6 prior to running the script, but willl give you the latest affinity version.
1. Pacman - `sudo pacman -S python-pyqt6`
2. DNF - `sudo dnf install python3-pyqt6 python3-pyqt6-svg`
	1. On some RHEL binary distros they won't have these directly in the repos, so you will instead have to install them via pip.
	2. `pip3 install pyqt6`
	3. `pip3 install pyqt6`
3. DEB - `sudo apt install python3-pyqt6.qtsvg`

Then run `curl -sSL https://raw.githubusercontent.com/ryzendew/AffinityOnLinux/refs/heads/main/AffinityScripts/AffinityLinuxInstaller.py | python3` in the terminal.

Select `one click install`.

# Install Affinity Appimage via AUR

`paru -S affinity-appimage-bin`