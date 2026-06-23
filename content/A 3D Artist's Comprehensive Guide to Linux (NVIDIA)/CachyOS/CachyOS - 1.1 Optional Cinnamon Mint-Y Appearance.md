---
title: CachyOS - 1.1 Optional Cinnamon Mint-Y Appearance
permalink: cachyos-cinnamon-mint
draft: "false"
---
If you have Cinnamon, complete some extra steps to get the best appearance and dark mode, with Mint-Y themes and a better cursor.
### Theme and Appearance
1. Install `sudo pacman -S mint-themes mint-y-icons` to enable the simplified appearance menu in the cinnamon settings. (It will take a while to download and install)
	- `paru -S bibata-cursor-theme` to install better looking cursor)
2. In theme appearance settings set desired dark Mint-Y themes, Select Bibata-Modern-Classic Cursor and in the settings tab select again to prefer dark mode.
	- The bash version of what the above command is doing: `gsettings set org.gnome.desktop.interface color-scheme prefer-dark`
