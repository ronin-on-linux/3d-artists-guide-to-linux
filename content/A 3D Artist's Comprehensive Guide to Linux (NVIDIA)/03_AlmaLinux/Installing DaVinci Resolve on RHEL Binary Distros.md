---
title: Installing DaVinci Resolve on AlmaLinux & RHEL Based Distros
permalink: almalinux-davinci
draft: "false"
---
# How to Use DaVinci Resolve
*See [[My Full DaVinci Resolve 3D, VFX & Color Grading Pipeline]]*
# Install DaVinci Resolve (Studio and Free)
1. Download the free or studio version of [[DaVinci Resolve]] from https://www.blackmagicdesign.com/products/davinciresolve.
2. Unzip the file. *(Right click and extract).*
3. Make sure the run file is executable. *(Right click and check executable in Permission tab).*
4. Run installer. 
	1. *It will prompt any missing packages you will need to install prior, and then the DaVinci installer should run and complete correctly, because it was built on the REHL platform.*
# Troubleshooting
### GPU Full Error
In most cases, running DaVinci will show a `GPU full error` in the edit page because it’s attempting to load on the *motherboard Integrated graphics (iGPU)* instead of your *Discrete GPU (dGPU)*. Take note it is also best to run on an *x11* system instead of Wayland for best performance.
1. Add `__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia` to the beginning of your bash command. Should now look like `sudo __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/resolve/bin/resolve`.
2. Right Click on the DaVinci `App Launcher` and select `Properties`. There should be a line to insert environment variables.
	1. Paste `env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`
3. (Alternatively) Open the desktop file of Davinci with nvim or nano `sudo nano /usr/share/applications/DaVinciResolve.desktop`
	1. On the `Exec=` line, add `env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia` before the `appname %u`
---
### Media Imports with No Audio or Video
> [!warning] Missing Codecs
> **DaVinci Resolve Studio** on Linux does not support AAC audio codec. It does support H.264/H.265 and all other codecs.
> 
> **DaVinci Resolve (Free)** on Linux supports limited H.264  and does not support H.265 codecs or AAC audio. It’s recommended that you use DaVinci Resolve Studio on Linux. 
> 
> **Why?** DaVinci Resolve piggybacks off of a Windows or MacOS internal AAC license. Linux operating systems ARE compatible with AAC codec but do not license AAC at a system level, so DaVinci can't piggyback off of that. They don't fix this because the main VFX industry clients who use the Linux version for do not need AAC codecs and generally transcode their footage into editing formats anyways, so they don't bother to purchase the licensing.

> [!check] Record in Universal Formats or Transcode Footage
> Many cameras can record in H264/H265 with PCM audio, fully compatible for Studio version. If you are recording screen on OBS Studio, you will need to set the audio codec to Opus or PCM.
> 
> Media from stock websites or cameras with unsupported codecs can be transcoded with [ffmpeg](https://ffmpeg.org/), [Handbrake](https://handbrake.fr/) or [Shutter Encoder](https://www.shutterencoder.com/)  to AV1 or an editing format like ProRes or DNxHD on both free and studio versions (a common practice in the film industry).
---
### Davinci won’t Start or Crashes on Wayland
Davinci is looking for certain elements from X11 that need to be pointed to XWayland in the Environment Variables.

Add `QT_QPA_PLATFORM=xcb __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`

---
### Importing *config.ocio* Fails (for Blender Color Space Transforms)  
If you attempt to import a `config.ocio` file in the Fusion or Color Page, occasionally it will fail and will appear empty.

DaVinci Resolve on Linux currently uses `/opt/resolve/libs/libOpenColorIO.so.2.4` meaning that it only supports importing OCIO files that are v2.4 and lower. For example, the current Blender config.ocio is ocio_profile_version: 2.5.1 so that can be an issue.

> [!success] Use Compatible OCIO Version 
> Easy solution is to just find an earlier version of your file. In my case for Blender, I use the blender 4.5 LTS color management folder and config.ocio since It is only version 2. https://github.com/blender/blender/blob/blender-v4.5-release/release/datafiles/colormanagement/config.ocio

If a config.ocio fails to import, you can also check its file health in the terminal to ensure it’s not corrupted or broken.
1. `ociocheck --iconfig /your/file/path/to/config.ocio`

---
> [!info] AlmaLinux Versions
> AlmaLinux, Rocky and Red Hat 10 come with newer zlib libraries meaning you will experience the same installation issues as Fedora and other modern Linux distros. Prefer AlmaLinux 9.
