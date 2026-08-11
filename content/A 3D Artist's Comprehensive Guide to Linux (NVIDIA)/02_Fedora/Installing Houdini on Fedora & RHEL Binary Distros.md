---
title: Installing Houdini on AlmaLinux & RHEL Based Distros
permalink: almalinux-houdini
draft: "false"
---
# Install Houdini Launcher
1. Download Houdini launcher from www.sidefx.com/download
2. See initial instructions on www.sidefx.com/docs/houdini/licensing/install_launcher.html
3. Open terminal
	1. `cd Downloads`
	2. `chmod a+x install_houdini_launcher.sh; ./install_houdini_launcher.sh`
4. Follow prompts until done.
# Install Houdini
1. `cd /opt/sidefx/launcher/bin/`
2. `./houdini_launcher`
3. Then install your desired version of Houdini via launcher. Be sure to leave the desktop shortcut checked.
4. Once finished, be sure to connect to SideFX online license server to get licenses as needed. Labs as well.
5. Once it’s installed, you will need to initialize the environment for Houdini in the next step.
	1. `cd /opt/hfs21.0`
	2. Version/folder name can be found by:
	3. `ls /opt/`
	4. `source houdini_setup` It will say environment is initialized
	5. `houdini` It should now load. In your start menu/app menu, you can now pin Houdini or the launcher to your panel.
6. If you haven’t activated a license yet, at this point it will give you the option to use Houdini Apprentice or register your license/sign-in.
7. If licensing is not found or shows error max entries which is common to RHEL related distros, this command should fix it. (I only had this issue with Fedora and Rocky/AlmaLinux.)
	- `sudo setsebool -P nis_enabled 1`
# Troubleshooting
### Houdini won't Start/Crashes after Bug Report Prompt
1. On many systems where there is an integrated graphics and a discrete graphics card you will need to force OpenGL and Vulkan to run on your discrete GPU in the terminal.
	1. `__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia KARMA_XPU_DEVICES=optix houdini`
2. If you want to use the Houdini desktop file/icon to open Houdini in this situation, you will need to add the environment variable above to your desktop file.
	1. It will often need the env var on the `Exec=` line and include the full file path to the executable. Often you also have to remove the quotations from the path. It should look like these examples:
	2. Houdini Launcher .desktop `Exec= env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia KARMA_XPU_DEVICES=optix /opt/sidefx/launcher/bin/houdini_launcher`
	3. Houdini .desktop `Exec= env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia KARMA_XPU_DEVICES=optix /opt/sidefx/launcher/bin/houdini`
3. Open and have fun in Houdini.
### Houdini on Wayland Crashes, UI Bugs, etc
If you are on a Wayland based system(Gnome, KDE, MangoWM, Cosmic, Hyprland, Niri) you will need to install a version of Houdini that is qt5 and supports Wayland, which is still only version 20.6 and back. Houdini 21 won't support Wayland for a while.

Once you have a Wayland compatible version installed, add `QT_QPA_PLATFORM=xcb` to its environment variables.
1. `env QT_QPA_PLATFORM=xcb __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia KARMA_XPU_DEVICES=optix /opt/sidefx/launcher/bin/houdini`
### Other
https://www.sidefx.com/community/sidefx-labs-april-update/?mc_cid=b062071184