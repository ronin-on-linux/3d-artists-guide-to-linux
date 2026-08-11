There are 3 primary ways to install Blender on Linux. Download from www.blender.org, install via your native package manager(which has its own caveats), or via flatpak in a sandboxed environment.
# Flatpak Install (Recommended - Most universal option with auto-updates.)

1. Make sure flatpak is installed.
2. Run `flatpak install flathub org.blender.Blender` in the terminal or select the Flathub version in the GUI of your distro's software store.
3. If it does not show in your menu, then Log out and back in.

It should now show up in your menus under Graphics. You can also run it in the terminal via the command:
`flatpak run org.blender.Blender`

> [!warning] Fedora Flatpack Versions!
> Always use the flathub package for the latest blender version. If you are using Fedora, DO NOT choose the fedora project Flatpak in the software store. It has GPU detection issues and version lag. (Non-issue if you are following the Fedora install guide on this website.)
# Download & Install from Blender Website (Recommended - Most Reliable)

1. Visit the [Blender Website](https://www.blender.org/download/) to download the latest version.
2. Unzip it to your home folder (`~/`) folder and run the blender executable from the folder.
3. Inside the unzipped folder, find the file named `blender.desktop`. 
	1. Copy/Paste it to `~/.local/share/applications`.
	2. Open the desktop file in a text editor.
	3. Replace the `Exec=` line with `Exec=/home/YOUR_USERNAME/BLENDER_VERSION/blender %f` (Be sure to swap in the correct folder and username!)
		1. *Example: `Exec=/home/john/blender-5.2.0-linux-x64/blender %f`*
4. Blender should now show up in your menu under Graphics.
# Install via native package manager (Fastest but with Caveats)

Depending on the distro you are running, blender may or may not be up-to-date with the latest release, and depending on the distro policies, may be compiled missing certain features due to licensing.
### Fedora/RHEL Binary
- `sudo dnf install blender` Lags behind in versions sometimes and has no Optix support due to strict open source-only policies at Fedora, Not recommended method.
### Arch/CachyOS
-  `sudo pacman -S blender` Useable, works great, stays up-to-date but is compiled using system python, meaning a very select few addons like Lens Sim by Håvard Dalen that use the blender specific python/pip libraries will not work.
### Debian/Ubuntu/Linux Mint
- `sudo apt install blender` Version is always about a year behind, but otherwise supports all included features. Not Recommended.
# Other Methods
There are other third-party methods like the AUR on Arch or Snaps on Ubuntu, but are not recommended and should generally be avoided for stability and security reasons.
### To setup Blender, see my personal [[Blender Startup Configuration]] notes.