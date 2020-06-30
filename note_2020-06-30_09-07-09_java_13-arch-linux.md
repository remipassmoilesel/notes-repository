# Installer Openjdk 13 (ou un JDK spécial) sur Arch Linux

Télécharger et extraire le JDK:

	$ curl https://cdn.azul.com/zulu/bin/zulu13.31.11-ca-fx-jdk13.0.3-linux_x64.tar.gz -o zulu-jdk-13.tar.gz
	$ tar -xvf zulu-jdk-13.tar.gz


Déplacer le JDK:

	$ sudo mv zulu-jdk-13 /usr/lib/jvm


Activer le JDK:

	$ sudo arch-linux-java status
	$ sudo arch-linux-java set zulu-jdk-13


