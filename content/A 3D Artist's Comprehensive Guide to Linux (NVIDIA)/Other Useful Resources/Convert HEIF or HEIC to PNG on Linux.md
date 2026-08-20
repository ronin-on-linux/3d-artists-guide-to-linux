Some applications like PolyCam only accept PNG files, and iPhones and other devices often store photos in a HEIF or HEIC format instead. Doing so on [[Linux]] is generally faster than on other systems without 3rd party tools.

### Install Required Package
1. Arch `sudo pacman -S libheif`
2. RHEL Adjacent `sudo dnf install libheif`
3. Debian `sudo apt install libheif libheif-examples`
### Convert a Single Image
1. `cd` to desired directory.
2. `heif-convert input.heic output.png`
### Batch Convert a Folder
1. `cd` to desired directory containing multiple HEIF/HEIC files.
2. `for f in *.heic; do heif-convert "$f" "${f%.*}.png"; done`

> [!info] Replace *.heic* with *.heif* depending on the specific file extension of your HEIF files.

> [!info] Be sure to execute commands in *bash* if your distro uses *zsh* or *fish*, etc in the terminal emulators. This is my case when using [[CachyOS]].

