# Flatpak
The easiest, universal containerized method is to use `flatpak install flathub fr.natron.Natron` 
# Native Package Manager
You can also use your package manager to install them.
1. Fedora & AlmaLinux - `sudo dnf install natron`
2. CachyOS - `sudo pacman -S natron`

> [!info] Native vs Flatpak
> Flatpak versions may not interface with local python scripts if you use those because of the sandboxing, but more easily consistent across operating systems. Native packages via `pacman` or `dnf` will be more compatible with python workflows.

Or go to the [website](https://natrongithub.github.io/#download) and download the preferred installer/portable version. Download the Installer and unzip it. Right click on it and ensure its executable, then run it. Follow the GUI installer prompts.