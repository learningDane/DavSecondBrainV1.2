#self-taught 
easy way: `archinstall` (do a `pacman -Syy` before)

Time/date sync
	`timedatectl set-ntp true`
Partitioning Drives
	`lsblk` shows disks
	`cfdisk/dev/nvme0` 
	selecting label type: GPT for modern and bigger than 2tb disks, else (and for VMs) DOS
	size for boot partition: 128M (for grub, other boot loaders may need more), then press __B__ for flagging it as bootable
	as much memory you want, flag it as primary
	write changes and quit cfdisk
	home is needed if you want to share it between different linux installations
	swap is needed if you don't have much RAM
Format as EXT4
	`mkfs.ext4/dev/nvme0p0`
	`mkfs.ext4/dev/nvme0p1`
	ecc
Mount boot partition
	`mount /dev/nvm0p0(root) /mnt`  
	`mkdir /mnt/boot` 
	`mount /dev/nvme0p1(boot) /mnt/boot`
Useful tool for autoinstalling a lot of things
	`pacstrap /mnt base base-devel linux linux-firmware vim(or nano ecc)`


Starting a service every startup
	`sudo systemctl enable SERVICENAME` 
Starting a service Right now
	`sudo systemctl start SERVICENAME` 
Customizing user startup and settings
	Check out files like `~/.profile` or `~/.bash_profile`, which will run on login etc