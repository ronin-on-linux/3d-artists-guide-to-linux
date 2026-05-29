# Install on Linux
1. Make sure Flatpak is installed.
2. `flatpak run com.writerduet.writersolo`
	1. If it doesn't show up in your menus, logging out and back in should solve that.
# Troubleshooting
Sometimes Flatpaks will not see file system/access files you want to access. (This is by design, for best sandboxed security).
1. To fix this, install Flatseal. `flatpak install flathub com.github.tchx84.Flatseal`. Flatseal helps you manage sandbox permissions for each individual app.
[WriterSolo Online](https://writersolo.com/#)