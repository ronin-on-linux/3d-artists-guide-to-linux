---
title: CachyOS - 1.2 Setting Up Wacom Tablet and Stylus
permalink: cachyos-wacom
draft: "false"
---
Since I most commonly use Cinnamon desktop on my personal CachyOS installations, there are some issues with linking custom button actions to the buttons on the tablet. Here are the steps I took to solve this via the terminal and an example setup that I use everyday.

1. `sudo pacman -S xf86-input-wacom` to make sure you can use `xsetwacom`
2. `xsetwacom list devices` to see all devices and their names. Find item labeled "pad" or "tablet".
	1. In my current case, it showed up as `Wacom Intuos PT M 2 Pad pad`
3. `xsetwacom -s get "Wacom Intuos PT M 2 Pad pad" all` to see all buttons.
	1. In my current case, there was more than the 4 buttons on my tablet listed (5). After some testing the buttons are laid out in a certain order.
		1. Button 3 = Upper Left Button
		2. Button 1 = Lower Left Button
		3. Button 9 = Upper Right Button
		4. Button 8 = Lower Right Button
4. Assign custom key binds to liking. In my current case, I like the Right side to scroll, and the left side upper to link to the terminal, and the lower left to linked to [[LocalSend]].
	1. To connect [[LocalSend]] or any other package launcher to the button, you have to set a custom shortcut in the keyboard shortcuts system settings page. I chose `Ctrl + Shift + L`  Once that is set, then you just link it to the shortcut key bind. 
		1. `xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 1 "key ctrl shift l"` 
	2. `xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 3 "key ctrl alt t"`
	3. `xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 8 "key Next"`
	4. `xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 9 "key Prior"`
5. Once you have set and tested the buttons to your desired inputs/commands, then you need to make this permanent, as these will reset after a reboot.
	1. `nano ~/.xprofile`
	2. Paste your commands and save. 
``` bash
xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 1 "key ctrl shift l"
xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 3 "key ctrl alt t"
xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 8 "key Next"
xsetwacom set "Wacom Intuos PT M 2 Pad pad" Button 9 "key Prior"
```

