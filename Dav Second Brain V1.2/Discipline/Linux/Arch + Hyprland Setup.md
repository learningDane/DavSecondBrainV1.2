#self-taught 
https://www.youtube.com/watch?v=lfUWwZqzHmA
wifi internet connection
`iwctl`, `station wlan0 show`, `station wlan0 scan`, `station wlan0 connect NOMERETE` 
Updating GPG keys
`pacman-key --init`, `pacman-key --populate archlinux`
Archinstall
	`archinstall` 
	profile: minimal
	add packages: git ecc
	network configuration: use network manager
	optional repositories: multilib
	-> install
Boot into install
Connect to internet
`nmcli device wifi connect NOMERETE password PASSWORDRETE` 
Install yay
`cd /opt/`,`sudo git clone https://aur.archlinux.org/yay-git.git`
change ownership `sudo chown -R NOMEUTENTE:NOMEUTENTE yay-git/`
`cd yay-git/`,`makepkg -si` 
update yay `yay -Syu` 
Cloning project
`cd /opt` ,`sudo git clone https://github.com/soldoestech/hyprland.git
`sudo chown -R NOMEUTENTE:NOMEUTENTE hyprland/` 
set script to executable and run it
`chmod +x set-hypr` 
`./set-hypr` 
disable wifi saving yes
copy config files
install starship shell? bho yes
install rog software no
start hyprland now

HYPRLAND CONFIG
`cd`,`cd .config` 