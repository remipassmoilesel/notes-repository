# Installer Manjaro sur un Acer Helios 300

Configuration BIOS:

	Configurer un mot de passe admin
	Désactiver secure boot
	Sur Advanced Settings > Main > CTRL + S puis désactiver Intel Octane


Installer Manjaro.   

Puis: 
	
	$ sudo manjaro-chroot -a
	$ sudo pacman -Syu
	$ sudo mhwd -a pci nonfree 0300


