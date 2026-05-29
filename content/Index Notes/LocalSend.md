[LocalSend Website](https://localsend.org/)
### [[Linux]]
1. Make sure Flatpak is installed.
2. `flatpak install org.localsend.localsend_app`
3. Firewall exception
	1. ufw (CachyOS)
		1. `sudo ufw allow 53317/tcp`
		2. `sudo ufw allow 53317/udp`
	2. firewalld (AlmaLinux/Fedora)
		1. `sudo firewall-cmd --permanent --add-port=53317/tcp`
		2. `sudo firewall-cmd --permanent --add-port=53317/udp`
		3. `sudo firewall-cmd --reload`   
