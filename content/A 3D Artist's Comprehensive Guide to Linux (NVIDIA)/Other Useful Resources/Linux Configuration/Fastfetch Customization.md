### Use/Modify from Included Example Files
1. `fastfetch -c examples/13` To look at all the example and config files available. (There are 32 examples, starting at #2) (13 is one of the best minimal looking ones).
2. `cd ~/.config`
3. `mkdir -p fastfetch` to make fastfetch dotfiles folder.
4. `fastfetch --gen-config` To generate default config file.
5. `cd /usr/share/fastfetch/presets/examples` to enter the presets/examples location.
6. `cp 13.jsonc ~/.config/fastfetch/config.jsonc` to copy it over the default config file.
7. Edit the config to your liking. See [[fastfetch example 13 modded minus ip added os age gpu and cpu shorthand config-jsonc]] for my current working file.
### Import Custom Look and Feel
https://www.reddit.com/r/GarudaLinux/comments/1dcq0dl/making_fastfetch_more_beautiful_linux/

1. Navigate to your `.config` directory -> `cd ~/.config`
2. Make fastfetch folder `mkdir -p fastfetch`
3. Generate default config file `fastfetch --gen-config`
4. `cd fastfetch`
5. Remove default`rm config.jsonc`
6. `wget https://raw.githubusercontent.com/harilvfs/fastfetch/refs/heads/old-days/fastfetch/config.jsonc` or other GitHub repo.
7. `exit`
8. `fastfetch`
### Auto-run on Terminal Startup
1. `nano ~/.bashrc` 
2. Add `fastetch` at the end of the file
3. Close and save with `Ctrl + X` and `Y`
4. `source ~/.bashrc`

> [!info] bashrc vs zshrc
> If you are using zsh, replace .bashrc with .zshrc

