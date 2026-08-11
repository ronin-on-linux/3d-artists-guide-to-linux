---
title: Installing DaVinci Resolve on CachyOS (and Arch Linux)
permalink: cachyos-davinci
draft: "false"
---
# How to Use DaVinci Resolve
*See [[My Full DaVinci Resolve 3D, VFX & Color Grading Pipeline]]*
# Install DaVinci Resolve (Free)
CachyOS has packaged the free version on pacman. (See missing codecs in troubleshooting section)

`sudo pacman -Sy davinci-resolve` (this only works on CachyOS)

> [!info] DaVinci Resolve on AMD GPUs
> If you have an AMD GPU, This FlipTheBitsTech video shows how to set up DaVinci free on AMD GPUs. https://youtu.be/u_b9PSNlkPA?si=oLO28RjYbS28vsu3

---
# Install DaVinci Resolve Studio
DaVinci Resolve Studio takes more steps to install because it’s made for AlmaLinux/RHEL, not Arch/CachyOS.
### Install Dependencies and Download DaVinci Studio 
1. `sudo pacman -Syu git base-devel`
2. Download `DaVinci_Resolve_Studio_[version_#]_Linux.zip` from [https://www.blackmagicdesign.com/support/family/davinci-resolve-and-fusion](https://www.blackmagicdesign.com/support/family/davinci-resolve-and-fusion) or the DaVinci Homepage.
### Setup & Build DaVinci Resolve Studio with AUR Script
1. `git clone https://aur.archlinux.org/davinci-resolve-studio.git`
2. `cp /Downloads/DaVinci_Resolve_Studio_[version_#]_Linux.zip /davinci-resolve-studio/`
3. `cd davinci-resolve-studio`
4. `makepkg -sric`
5. Studio is now installed but must be opened under `sudo` the first time to apply your License Activation Key.
6. Run `sudo /opt/resolve/bin/resolve` and enter your license, close resolve.
	1. You may need to add the environment variables from the troubleshooting section below to your bash command if it doesn't launch. (Don’t include `env`)
7. Run the same command again in some cases, then close resolve again
8. Finally open up Resolve from the application launcher and it should open and be licensed.



---
# Troubleshooting and Best Practices
### *Makepkg* Fails Sha265sum Check
This most likely happens when the maintainer of the AUR script has not updated the checksums to match those of the most current download (or) you are trying to install a newer/beta or older version than is expected in the `PKGBLD` script.

You can open the `PKGBLD` file in the `davinci-resolve-studio` folder that was created in the home directory to see what version of DaVinci it is looking for.

Replace the sha256sum keys with `SKIP` and change the version number to match your downloads version number.

> [!warning] Checksum Failure PSA
> If your checksum verification fails, your version numbers match and you decide to skip the checksum, you acknowledge that you are proceeding despite knowing the risk that your download may have been compromised or corrupted. Redownloading or manually verifying your sha256sums is recommended before proceeding.

---
### GPU Full Error
In most cases, running DaVinci will show a `GPU full error` in the edit page because it’s attempting to load on the *motherboard Integrated graphics (iGPU)* instead of your *Discrete GPU (dGPU)*. Take note it is also best to run on an *x11* system instead of Wayland for best performance.
1. Add `__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia` to the beginning of your bash command. Should now look like `sudo __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/resolve/bin/resolve`.
2. Right Click on the DaVinci `App Launcher` and select `Properties`. There should be a line to insert environment variables.
	1. Paste `env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`
2. (Alternatively) Open the desktop file of Davinci with nvim or nano `sudo nano /usr/share/applications/DaVinciResolve.desktop`
	1. On the `Exec=` line, add `env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia` before the `appname %u`
---
### Media Imports with No Audio or Video
> [!warning] Missing Codecs
> **DaVinci Resolve Studio** on Linux does not support AAC audio codec. It does support H.264/H.265 and all other codecs.
> **DaVinci Resolve (Free)** on Linux supports limited H.264  and does not support H.265 codecs or AAC audio. It’s recommended that you use DaVinci Resolve Studio on Linux. 
> **Why?** DaVinci Resolve piggybacks off of a Windows or MacOS internal AAC license. Linux operating systems ARE compatible with AAC codec but do not license AAC at a system level, so DaVinci can't piggyback off of that. They don't fix this because the main VFX industry clients who use the Linux version for do not need AAC codecs and generally transcode their footage into editing formats anyways, so they don't bother to purchase the licensing.

> [!check] Record in Universal Formats or Transcode Footage
> Many cameras can record in H264/H265 with PCM audio, fully compatible for Studio version. If you are recording screen on OBS Studio, you will need to set the audio codec to Opus or PCM.
> Media from stock websites or cameras with unsupported codecs can be transcoded with [ffmpeg](https://ffmpeg.org/), [Handbrake](https://handbrake.fr/) or [Shutter Encoder](https://www.shutterencoder.com/)  to AV1 or an editing format like ProRes or DNxHD on both free and studio versions (a common practice in the film industry).
---
### Davinci won’t Start or Crashes on Wayland
Davinci is looking for certain elements from X11 that need to be pointed to XWayland in the Environment Variables.

Add `QT_QPA_PLATFORM=xcb __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia`

In many cases when using this in Wayland, you will have issues running DaVinci under sudo to activate the license because of the way Xwayland works, but I have found a janky work around.
	1. `sudo chmod 777 /var/BlackmagicDesign`
	2. `sudo chmod -R 777 /opt/resolve`
	3. `QT_QPA_PLATFORM=xcb __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/resolve/bin/resolve`
	4. Then after you have entered the license key and its verified, you will need to reduce the folder privileges again:
	5. `sudo chmod -R 755 /opt/resolve`
	6. `sudo chmod -R 755 /var/BlackmagicDesign`
	7. `sudo chown -R $USER:$USER /var/BlackmagicDesign`
	8. It should then work fine.

---
### Importing *config.ocio* Fails (for Blender Color Space Transforms)  
If you attempt to import a `config.ocio` file in the Fusion or Color Page, occasionally it will fail and will appear empty.

DaVinci Resolve on Linux currently uses `/opt/resolve/libs/libOpenColorIO.so.2.4` meaning that it only supports importing OCIO files that are v2.4 and lower. For example, the current Blender config.ocio is ocio_profile_version: 2.5.1 so that can be an issue.

> [!success] Use Compatible OCIO Version 
> Easy solution is to just find an earlier version of your file. In my case for Blender, I use the blender 4.5 LTS color management folder and config.ocio since It is only version 2. https://github.com/blender/blender/blob/blender-v4.5-release/release/datafiles/colormanagement/config.ocio

If a config.ocio fails to import, you can also check its file health in the terminal to ensure it’s not corrupted or broken.
1. `ociocheck --iconfig /your/file/path/to/config.ocio`

---
### Installing on Arch Linux
If you are installing on Vanilla Arch, at least 4 dependencies are old enough they are no longer included in the `pacman` repos.

When you run `makepkg -sric` it will give you a long list of missing dependencies. Try to bulk install all of them, and pacman will tell you which ones are no longer in pacman. 

Remove those packages no longer on `pacman` and run that command with the rest to install most of the missing dependencies. 

The others you noted down must be installed via the `pacman archive` or through `paru` or `yay` from the AUR. (Note, it takes forever to build them from AUR, so probably better to use the archive)

These were the four I had to install from the archive:
1. `# pacman -U https://archive.archlinux.org/packages/q/qt5-webchannel/qt5-webchannel-5.15.9+kde+r3-1-x86_64.pkg.tar.zst`
2. `# pacman -U https://archive.archlinux.org/packages/q/qt5-webengine/qt5-webengine-5.15.9-3-x86_64.pkg.tar.zst`
3. `# pacman -U https://archive.archlinux.org/packages/g/gtk2/gtk2-2.24.33-5-x86_64.pkg.tar.zst`
4. `# pacman -U https://archive.archlinux.org/packages/l/libpng12/libpng12-1.2.59-2-x86_64.pkg.tar.zst`

Once they are all installed, run `makepkg -sric` again and it should still work.