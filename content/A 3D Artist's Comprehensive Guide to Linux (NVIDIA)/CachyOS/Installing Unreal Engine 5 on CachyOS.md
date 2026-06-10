### Install Vulkan
1. `sudo pacman -S vulkan-devel`
2. Run `vkcube` to ensure that vulkan is working. (You should see a rotating cube with the on it.)
### Git Clone AUR package (downloads to your home folder.)
See https://aur.archlinux.org/packages/unreal-engine-bin for developers notes.
1. `git clone https://aur.archlinux.org/unreal-engine-bin.git`
### Download Unreal Engine for Linux
1. Visit https://www.unrealengine.com/linux and download the current version of Unreal Engine 5.
	1. Download the corresponding Linux Fab and Quixel files as well.
2. Copy/Move the ZIP folder into the `~/unreal-engine-bin` folder.
### Build the Package
1. `cd ~/unreal-engine-bin`
2. Install with `makepkg -si`
### Install Fab and Quixel Add-ons
1. Extract Zip files in `~/Downloads` folder
2. Copy `Fab` and `Quixel` folder from `~/Downloads/Linux_Fab_5.*/Engine/Plugins/` into `/opt/unreal-engine/Engine/Plugins`. (You will need sudo/admin privileges to do so.)
To open the /opt/ folder under sudo, type `admin:///` into the address bar of your file manager, type your password and then navigate to the above file directory.
### Add Environment Variables to Desktop Launcher
1. Find your desktop file for UE5 in `/usr/share/applications/unreal-engine.desktop`
2. Edit the file with nano or VSCode and replace the text after `Exec=` with `Exec=env SDL_VIDEODRIVER=x11 VK_ICD_FILENAMES=/usr/share/vulkan/icd.d/nvidia_icd.json __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia /opt/unreal-engine/Engine/Binaries/Linux/UnrealEditor %F`

If all has gone well, you will be able to launch Unreal Engine with minimal issues. *Keep in mind that UE5 is the application that I have had the most difficulty getting to work on Linux just because of the UI glitches and crashing that ensues when on the wrong desktop compositor.*

> [!warning] Desktop Environment REALLY matters for UE5
> No matter if you are using X11 or Wayland, most compositors basically break the UE5 user interface, so if you are planning on using Unreal Engine 5 on Linux, make sure that your desktop environment that you use supports disabling compositing entirely like XFCE or x11 Window Mangers like i3, bspwm or oxwm.
> 
> For example, I use Cinnamon for my "normal" environment, but I will switch to OXWM or XFCE to use Unreal Engine because it just works so much better and is much less buggy. Cinnamon uses Mutter Compositing and it can be problematic for UE5 UI elements. If you are a simple person, its probably better to just feel out what desktop environment works for everything you like and stick to one.

