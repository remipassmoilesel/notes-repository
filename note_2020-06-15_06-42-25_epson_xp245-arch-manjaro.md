# Installer une imprimante Epson XP-245 sous Arch Linux / Manjaro

## Imprimante

Paquets:

	$ sudo pacman -S cups ghostscript libcups
	$ yay -S epson-inkjet-printer-escpr


Service:

	$ sudo systemctl enable org.cups.cupsd.service
	$ sudo systemctl start org.cups.cupsd.service
	$ sudo systemctl status org.cups.cupsd.service


Configuration:

- Ouvrir localhost:631, onglet administration
- User root, mot de passe root système
- Ajouter une imprimante > Configurer l'imprimante


## Scanner

Paquets:

	$ sudo pacman -S sane iscan iscan-data


Lister les scanners disponibles:

	$ scanimage -L


Scanner en ligne de commande pour essai: 

	$ scanimage --device "pixma:04A91749_247936" --format=tiff --output-file test.tiff --progress


En cas de problème, redémarrer, puis débrancher puis rebrancher le scanner.

