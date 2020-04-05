# Memo Arch Linux / Manjaro

## Installation

Privilégier une installation avec connexion internet pour la configuration du matériel.


### Utilisation des Arch User Repositories

Installer base-devel:

	$ pacman -S base-devel


Installer Yay:

	$ cd /tmp
	$ git clone https://aur.archlinux.org/yay.git
	$ cd yay
	$ makepkg -si


### Pilotes Nvidia

A l'aide de la détection de matériel Manjaro:

	$ sudo mhwd -a pci nonfree 0300


### Setup HP Omen

Pour utiliser deux écrans, installer optimus-manager et activer la carte Nvidia:

	$ sudo pacman -S optimus-manager
	$ sudo reboot now
	$ optimus-manager --set-startup nvidia
	$ optimus-manager --switch nvidia


### Polices

Polices emoticone:

	$ yay -S ttf-twemoji-color ttf-symbola
	$ sudo pacman -S ttf-joypixels

