---
title: Package Manager
permalink: linux-pkg-mgr
draft: "false"
---

All linux distros come with a Package Manager which you use in [[bash]] to easily install, update and remove software. Understanding this will help you get started no matter which distro you use because they all do the same thing.
### Package Managers for Each Distro/Platform Type

| Linux Distros/Platforms                                       | Package Managers                                                                                 |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Debian (Linux Mint, Ubuntu, Pop! OS, etc)                     | [apt](https://ubuntu.com/server/docs/how-to/software/package-management/)                        |
| Fedora & RHEL (AlmaLinux, Bazzite, Red Hat, Rocky Linux, etc) | [dnf](https://docs.fedoraproject.org/en-US/quick-docs/dnf/)                                      |
| Arch Linux (CachyOS, Omarchy, Manjaro, etc)                   | [pacman](https://wiki.archlinux.org/title/Pacman)                                                |
| Arch User Repository (AUR) (Unofficial User Repos)            | [paru, yay](https://wiki.archlinux.org/title/AUR_helpers)                                        |
| SUSE (OpenSUSE Leap & Tumbleweed)                             | [zypper](https://documentation.suse.com/smart/systems-management/html/concept-zypper/index.html) |
| Flathub (Universal Repo for Sandboxed Apps)                   | [flatpak](https://flatpak.org/)                                                                  |

---
### How to Use Your Distro's Package Manager
1. `sudo` is used to call on superuser/administrator privileges, needed to use all package managers except `flatpak`, `paru` and `yay`.

|          | Install Package                  | Remove Package                  | Update System                             |
| -------- | -------------------------------- | ------------------------------- | ----------------------------------------- |
| apt      | `sudo apt install [pkg-name]`    | `sudo apt remove [pkg-name]`    | `sudo apt update && sudo apt upgrade`     |
| dnf      | `sudo dnf install [pkg-name]`    | `sudo dnf remove [pkg-name]`    | `sudo dnf upgrade`                        |
| pacman   | `sudo pacman -S [pkg-name]`      | `sudo pacman -R [pkg-name]`     | `sudo pacman -Syu`                        |
| paru/yay | `paru -S [pkg-name]`             | `paru -R [pkg-name]`            | N/A                                       |
| zypper   | `sudo zypper install [pkg-name]` | `sudo zypper remove [pkg-name]` | `sudo zypper dup` or `sudo zypper update` |
| flatpak  | `flatpak install [address]`      | `flatpak uninstall [address]`   | N/A                                       |
