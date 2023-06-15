- # Eliminar metadatos con ExifTool
	- Instalar exiftool:
		- ```zsh
		  sudo apt install libimage-exiftool-perl
		  ```
	- Mirar los metadatos:
		- ```zsh
		  exiftool <image.jpg>
		  ```
	- Eliminar los metadatos de un archivo:
		- ```zsh
		  exiftool -all= <image.jpg>
		  ```
	- Eliminar metadatos de un directorio entero:
		- ```zsh
		  exiftool -recurse -all= <path of directory>
		  ```