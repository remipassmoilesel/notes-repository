# Partager une machine virtuelle Virtualbox entre plusieurs utilisateurs

Creér un dossier partagé et un groupe d'utilisateurs:

	$ cd /home
	$ mkdir shared-folder
	$ sudo groupadd vm-users
	$ sudo chgrp -R vm-users shared-folder
	$ sudo chmod -R 770 shared-folder
	$ sudo chmod +s shared-folder


Ajouter le groupe aux utilisateurs (penser à se déconnecter si utilisateurs actuel modifié):

	$ sudo usermod -aG vm-users user1
	$ sudo usermod -aG vm-users user2


Une fois la VM créé, dupliquer le fichier .vbox dans le but que chaque utilisateurs ai son propre
fichier de description de VM:

	$ cd vm
	$ cp arch.vbox arch-user1.vbox
	$ cp arch.vbox arch-user2.vbox


