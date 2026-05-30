I initially had some difficulty finding the file hierarchies that I was used to accessing on Windows once I migrated to [[Linux]]. These notes may be helpful in some situations.

### Native Package Managers
This document is running under the assumption that you are installing [[Blender]] via the native package managers like pacman, apt, dnf, etc. 

AppData equivalent is in `~/.config/blender/[version]/...`

Main file hierarchy is likely located in `/usr/share/blender/[version]/...`

Main repo OCIO/COlormanagement files are in `/usr/share/blender/[version]/datafiles/colormanagement`

AUR Blender LTS OCIO files are in `/opt/blender-lts/4.5/datafiles/colormanagement`

### AUR, Snapd, Etc
For additional Blender LTS installations alongside normal package managers, such as AUR in CachyOS and Arch via Paru or Yay are likely in other locations.

Blender-LTS from AUR via paru and yay usually shows up in `/opt/blender-lts/[version]/...` Additional files can also be found in the `.config` folder as listed above as well.

Blender Snap package executable is generally located at `/snap/bin/blender`, while the core installation files reside under `/snap/blender/current/`. User configuration and scripts for the snap version are usually stored in `~/snap/blender/current/.config/blender/`