# Mémo encodage

## Détection

Avec file:

	$ file /path/to/file.txt


Avec chardet:

	$ pip install chardet
	$ chardetect/path/to/file.txt


## Conversion

Avec iconv:

	$ iconv -f from-encoding-name -t to-encoding-name /path/to/file


Ignorer les caracères incorrects:

	$ iconv -f windows-1252 -t UTF-8//IGNORE ... ...


