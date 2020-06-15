# Installer une imprimante Epson XP-245 sous Arch Linux / Manjaro

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

