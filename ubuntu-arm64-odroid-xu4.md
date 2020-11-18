# Installer Ubuntu ARM 20.04.1 LTS sur un Odroid XU-4

Matériel:

- Odroid XU4
- Carte SD
- Un disque dur externe


Téléchargement l'image:


	$ wget http://de.eu.odroid.in/ubuntu_20.04lts/XU3_XU4_MC1_HC1_HC2/ubuntu-20.04.1-5.4-minimal-odroid-xu4-20200812.img.xz



Flasher un carte micro SD:

	$ sudo dd if=ubuntu-arm.iso of=/dev/mmcblk0 bs=4096 && sync



Se connecter:

	$ ssh root@192.168.X.X


Identifiants par défaut:

	root
	odroid


Identifier les partitions, fdisk sur le disque externe:

	$ lsblk
	$ sudo fdisk /dev/sda

	> n
	> primary +60G
	> n
	> primary last sector
	> w


Formatter les partitions:

	$ sudo mkfs -t ext4 /dev/sda1
	$ sudo mkfs -t ext4 /dev/sda2


Monter le disque externe, cloner le système d'exploitation (répeter la commande):

	$ mkdir /mnt/data1
	$ mkdir /mnt/system


	$ sudo mount /dev/sda2 /mnt/data1
	$ sudo mount /dev/sda1 /mnt/system
	$ rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / /mnt/data1


Identifier les partitions (repérer PARTUUID):

	$ sudo blkid


Remplacer la valeur de root=UUID=XXXXX:

	$ sudo nano media/boot/boot.ini
	
	root=UUID=XXXX



