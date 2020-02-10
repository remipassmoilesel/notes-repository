# Installer Wordpress

Télécharger et décompresser les fichiers:

	$ cd /var/www
	$ wget https://fr.wordpress.org/wordpress-4.6.1-fr_FR.zip     
	$ unzip wordpress-...zip
	$ chown -R www-data:www-data wordpress
	$ cd wordpress/

Installer une base de données:	

	$ sudo mysql -u root
	$ create database wp_dtbs;
	$ CREATE USER 'abcd'@'localhost' IDENTIFIED BY 'abcd';  
	$ GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON wp_dtbs.* TO 'abdcd'@'localhost';

Augmenter la taille des fichiers à uploader:

	$ sudo vim /etc/php/7.0/apache2/php.ini
	
	post_max_size = 20M
	upload_max_filesize = 20M

	$ sudo service apache2 restart
 

## Sauvegarde de base de données

	$ sudo mysql -u root --execute="show databases" 
	$ sudo mysqldump --all-databases > file.sql
	$ sudo mysqldump wordpress_database > file.sql 
	

## Plugins

Editeur Wysiwyg 	Voir TinyMCE advanced: https://downloads.wordpress.org/plugin/tinymce-advanced.4.4.1.zip
Page à venir		Coming Soon Page & Maintenance Mode by SeedProd 
Insertion de code	wp-insert-code

Système de réservation	Booking Calendar 7.0
			(Penser à activer l'option: "Cochez cette case , si vous voulez paramétrer n'importe quel jour comme disponible dans le calendrier...."

(Dézipper le plugin dans wp-content/plugin)


## Configuration d'un proxy

Exemple:

	<VirtualHost *:80>

	  ServerName website-name.fr
	  DocumentRoot /var/www/empty

	  LogLevel info

	  ErrorLog ${APACHE_LOG_DIR}/website-name/error.log
	  CustomLog ${APACHE_LOG_DIR}/website-name/access.log combined

	  Redirect / https://website-name.fr/

	</VirtualHost>

	<VirtualHost *:443>

	  ServerName website-name.fr
	  ServerAlias www.website-name.fr

	  DocumentRoot /var/www/empty

	  LogLevel info

	  ErrorLog ${APACHE_LOG_DIR}/website-name/error.log
	  CustomLog ${APACHE_LOG_DIR}/website-name/access.log combined

	  Include /etc/letsencrypt/options-ssl-apache.conf
	  SSLCertificateFile /etc/letsencrypt/live/website-name.fr/fullchain.pem
	  SSLCertificateKeyFile /etc/letsencrypt/live/website-name.fr/privkey.pem

	  ProxyPass "/"  "http://localhost:8000/"
	  ProxyPassReverse "/"  "http://localhost:8000/"
	  
	  # Ces options permette d'activer la prise en charge TLS par Wordpress
	  RequestHeader set "X-Forwarded-Proto" expr=%{REQUEST_SCHEME}
	  ProxyPreserveHost On

	</VirtualHost>



