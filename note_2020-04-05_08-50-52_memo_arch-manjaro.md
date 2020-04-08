# Memo Arch Linux / Manjaro

## Installation

Privilégier une installation avec connexion internet pour la configuration du matériel.


### Installer VIM

Installation:

	$ sudo pacman -S vim


Désactiver la souris:

	$ vim ~/.vimrc 

	set mouse-=a


### Réduire le seuil de swap

	$ sudo vim /etc/sysctl.d/100-manjaro.conf
	
	vm.swappiness=10


## Correction orthographique

	$ sudo pacman -S aspell-fr libmythes mythes-fr languagetool


## Activer trim pour les disques SSD

	$ sudo systemctl enable fstrim.timer


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

Pour utiliser un deuxième écran via le port HDMI de la carte graphique, installer optimus-manager et activer la carte Nvidia:

	$ sudo pacman -S optimus-manager
	$ sudo reboot now
	$ optimus-manager --set-startup nvidia
	$ optimus-manager --switch nvidia


### Polices

Polices emoticone:

	$ yay -S ttf-twemoji-color ttf-symbola
	$ sudo pacman -S ttf-joypixels


### Docker

	$ sudo pacman -S docker docker-compose


### Kubectl

	$ sudo pacman -S kubectl


### Java

	$ sudo pacman -S jdk-openjdk
	$ archlinux-java status
	$ archlinux-java set java-13-openjdk
	

### NodeJS

Avec la variable d'environnement N_PREFIX pointant vers $HOME:

	$ curl -L https://raw.githubusercontent.com/tj/n/master/bin/n -o n
	$ sudo mv n /usr/local/bin
	$ sudo chmod +x /usr/local/bin/n
	$ n stable


### Emulateur de terminal drop down XFCE

Créer un raccourci clavier lié à la commande:

	$ xfce4-terminal --drop-down

