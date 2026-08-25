There are 3 primary ways to install Blender on Linux. Download from www.blender.org, install via your native package manager(which has its own caveats), or via flatpak in a sandboxed environment.

<div style="position: relative; width: 100%; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe 
    src="https://www.youtube.com/embed/luESgIQipnU" 
    title="3 Ways to Install Blender on Linux"
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" 
    allowfullscreen>
  </iframe>
</div>


# Flatpak Install (Recommended - Most universal option with auto-updates.)

1. Make sure flatpak is installed.
2. Run `flatpak install flathub org.blender.Blender` in the terminal or select the Flathub version in the GUI of your distro's software store.
3. If it does not show in your menu, then Log out and back in.

It should now show up in your menus under Graphics. You can also run it in the terminal via the command:

`flatpak run org.blender.Blender`

> [!warning] Fedora Flatpack Versions!
> Always use the flathub package for the latest blender version. If you are using Fedora, DO NOT choose the fedora project Flatpak in the software store. It has GPU detection issues and ocassional version lag. (Non-issue if you are following the Fedora install guide on this website.)

Some distros have a GUI app store like Software Store or Bazaar preinstalled that you can use to install flatpaks without the terminal if you would prefer.

`sudo pacman -S bazaar`

![[Screenshot from 2026-08-12 10-43-57.png]]

---
# Download & Install from Blender Website (Recommended - Most Reliable)

1. Visit the [Blender Website](https://www.blender.org/download/) to download the latest version.
2. Unzip it to your home folder (`~/`) folder and run the blender executable from the folder.
3. Inside the unzipped folder, find the file named `blender.desktop`. 
	1. Copy/Paste it to `~/.local/share/applications`.
	2. Open the desktop file in a text editor.
	3. Replace the `Exec=` line with `Exec=/home/YOUR_USERNAME/BLENDER_VERSION/blender %f` (Be sure to swap in the correct folder and username!)
		1. *Example: `Exec=/home/ronin/blender-5.2.0-linux-x64/blender %f`*
	4. Run `update-desktop-database ~/.local/share/applications` to refresh the menu.
4. Blender should now show up in your menu under Graphics. If it does not show up still, log out and back in and it should show up correctly.

![[Screenshot from 2026-08-12 10-52-31.png]]
![[Screenshot from 2026-08-12 11-09-27.png]]

---
# Install via native package manager (Fastest but with Caveats)

Depending on the distro you are running, blender may or may not be up-to-date with the latest release, and depending on the distro policies, may be compiled missing certain features due to licensing.
### Fedora/RHEL Binary
- `sudo dnf install blender` Lags behind in versions sometimes and has no Optix support due to strict open source-only policies at Fedora, Not recommended method.
### Arch/CachyOS
-  `sudo pacman -S blender` Useable, works great, stays up-to-date but is compiled using system python, meaning a very select few addons like Lens Sim by Håvard Dalen that use the blender specific python/pip libraries will not work.
### Debian/Ubuntu/Linux Mint
- `sudo apt install blender` Version is always about a year behind, but otherwise supports all included features. Not Recommended.

![[Screenshot from 2026-08-12 10-59-46.png]]

---
# Other Methods
There are other third-party methods like the AUR on Arch or Snaps on Ubuntu, but are not recommended and should generally be avoided for stability and security reasons.
### Arch User Repository
On Arch the AUR provides a Blender LTS binary that allows you to recieve updated LTS-only versions. 

> [!warning] Use the AUR at your own risk. https://aur.archlinux.org/

`paru -S blender-lts-bin`

### Snaps
Snaps are the official blender distribution of blender on Linux, but if you do a quick google search you will find hundreds of opinions about Canonical, Ubuntu and Snaps specifically and why most avoid them.

`sudo snap install blender --classic`

---
# Troubleshooting
> [!warning] Keybind Conflict
> Be sure if you are installing with gnome, kde or cinnamon, that you swap the alt-mouse with super-mouse to avoid blender navigation conflicts. See the [Blender Documentation]( https://docs.blender.org/manual/en/latest/getting_started/installing/linux.html) for details.

### To setup Blender, see my personal [[Blender Startup Configuration]] notes.