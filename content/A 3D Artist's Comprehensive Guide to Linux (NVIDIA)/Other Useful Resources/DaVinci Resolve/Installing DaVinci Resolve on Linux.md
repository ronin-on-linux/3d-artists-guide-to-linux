---
title: Installing DaVinci Resolve on Fedora
permalink: resolve-linux
draft: "false"
---
# How I Use DaVinci Resolve
*See [[My Full DaVinci Resolve 3D, VFX & Color Grading Pipeline]]*
# Install DaVinci Resolve (Studio and Free)
1. Download the free or studio version of [[DaVinci Resolve]] from https://www.blackmagicdesign.com/products/davinciresolve.
2. Unzip the file into downloads folder. *(Right click and extract).* Bring the `.run` into the downloads folder
3. Make sure the run file is executable. *(Right click and check executable in Permission tab).*
4. Install Fuse2 if you didn't during your initial setup `sudo pacman -S fuse-libs` or `sudo dnf install fuse-libs`
5. Run installer. It will prompt any missing packages you will need to install prior to running the installer.
	1. The most common packages it asks for on Fedora are `sudo dnf install apr apr-util mesa-libGLU` 
6. `sudo pacman -S libxcrypt-compat` or `sudo dnf install libxcrypt-compat` to fix the missing `libcrypt.so.1` error.
7. Double click the `.run` file and install DaVinci.
# Troubleshooting
### Non-RHEL Binary Distros - Fixing DaVinci Libraries (Necessary Fix)
You will need to move/rename a series of outdated glib files since DaVinci is made for RHEL binary distros like Rocky and AlmaLinux still on version 8-9 which rely on older glibs.

`cd /opt/resolve/libs && sudo mkdir archived-libs && sudo mv libglib* libgio* libmodule* libgobject* archived-libs`

---
### GPU Full Error (Recommended Fix)
In most cases, running DaVinci will show a `GPU full error` in the edit page because it’s attempting to load on the *motherboard Integrated graphics (iGPU)* instead of your *Discrete GPU (dGPU)*. Take note it is also best to run on an *x11* system instead of Wayland for best performance.
1. Right Click on the DaVinci `App Launcher` and select `Properties`. Check `use dedicated GPU if available`. This will generate a new desktop file in the home folder in Cinnamon.
2. Then open the DaVinci Resolve desktop file in `~/.local/share/applications/davinci.desktop` There should be a line to insert environment variables.
	1. Replace the `Exec=` line with `Exec=env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/resolve/bin/resolve %u`
---
### Media Imports with No Audio or Video
> [!warning] Missing Codecs
> **DaVinci Resolve Studio** on Linux does not support AAC audio codec. It does support H.264/H.265 and all other codecs.
> 
> **DaVinci Resolve (Free)** on Linux supports limited H.264  and does not support H.265 codecs or AAC audio. It’s recommended that you use DaVinci Resolve Studio on Linux. 
> 
> **Why?** DaVinci Resolve piggybacks off of a Windows or MacOS internal AAC license. Linux operating systems ARE compatible with AAC codec but do not license AAC at a system level, so DaVinci can't piggyback off of that. They don't fix this because the main VFX industry clients who use the Linux version for do not need AAC codecs and generally transcode their footage into editing formats anyways, so they don't bother to purchase the license.

> [!check] Record in Universal Formats or Transcode Footage
> Many cameras can record in H264/H265 with PCM audio, fully compatible for Studio version. If you are recording screen on OBS Studio, you will need to set the audio codec to Opus or PCM.
> 
> Media from stock websites or cameras with unsupported codecs can be transcoded with [ffmpeg](https://ffmpeg.org/), [Handbrake](https://handbrake.fr/) or [Shutter Encoder](https://www.shutterencoder.com/)  to AV1 or an editing format like ProRes or DNxHD on both free and studio versions (a common practice in the film industry).
---
### Davinci won’t Start or Crashes on Wayland
Davinci is looking for certain elements from X11 that need to be pointed to XWayland in the Environment Variables.

Add `QT_QPA_PLATFORM=xcb` at the beginning of your `Exec=env QT_QPA_PLATFORM=xcb __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/resolve/bin/resolve %u` in the desktop launcher file.

---
### Importing *config.ocio* Fails (for Blender Color Space Transforms)  
If you attempt to import a blender `config.ocio` file in the Fusion or Color Page, it will appear empty.

Resolve on Linux currently uses `/opt/resolve/libs/libOpenColorIO.so.2.4` meaning that it only supports importing OCIO files that are v2.4 and lower. For example, the current Blender config.ocio is ocio_profile_version: 2.5.1 so that can be an issue.

> [!success] Use Compatible OCIO Version 
> Easy solution is to just find an earlier version of your file. In my case for Blender, I use the blender 5.0 color management folder and config.ocio since It is only version 2.4 https://github.com/blender/blender/blob/blender-v5.0-release/release/datafiles/colormanagement/config.ocio

If a config.ocio fails to import, you can also check its file health in the terminal to ensure it’s not corrupted or broken.
1. `ociocheck --iconfig /your/file/path/to/config.ocio`
2. If you need blenders current ocio, make a copy of its color management folder to your home folder `~/colormanagement/` and edit the config.ocio file and just change the version number to 2.4. (ANything that uses code from 2.5+ will break, but the ACES, Kronos and AgX color spaces still work.)

---
> [!info] AlmaLinux Versions
> AlmaLinux, Rocky and Red Hat 10 come with newer zlib libraries meaning you will experience the same installation issues as Fedora and other modern Linux distros. Prefer AlmaLinux 9 or 8 if you want a clean install experience.

---
# Other Videos for AMD Users and Free Version
1. DaVinci on Fedora AMD https://www.youtube.com/watch?v=jLq7D1rxQeM&t=11s
2. DaVinci Free AMD on CachyOS https://www.youtube.com/watch?v=u_b9PSNlkPA&t=101s
3. DaVinci on Bazzite https://www.youtube.com/watch?v=iQtX6YfkiOU&t=723s
4. DaVinci Troubleshooting on Linux https://www.youtube.com/watch?v=oHsboGBxUuc