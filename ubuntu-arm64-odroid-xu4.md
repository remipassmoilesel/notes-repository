# Installer Ubuntu ARM 20.04.1 LTS sur un Odroid XU-4

Téléchargement l'image:


	$ wget http://de.eu.odroid.in/ubuntu_20.04lts/XU3_XU4_MC1_HC1_HC2/ubuntu-20.04.1-5.4-minimal-odroid-xu4-20200812.img.xz



Flasher un carte micro SD:

	$ sudo dd if=ubuntu-arm.iso of=/dev/mmcblk0 bs=4096 && sync



Identifiants par défaut:

	root
	odroid



