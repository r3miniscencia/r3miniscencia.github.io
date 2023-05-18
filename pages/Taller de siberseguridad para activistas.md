- # Conceptos previos
	- ## 1. Seguridad poco a poco:
	  
	  * Es un mundo muy amplio por lo que **no hay que asustarse ni agobiarse**.
	  * Los **cambios** se deben hacer **poco a poco** para no agotarse.  
	  ![image.png](../assets/image_1681909752230_0.png){:height 179, :width 217, :align right}
	- ## 2. Los malos a.k.a modelo de amenazas
	  + Los cuerpos de seguridad del estado.
	  + Empresarios, políticos u otras personas que se vean contrariadas por nuestras actuaciones.
	  + Fascistas, machistas, racistas y el resto de reaccionarios.
	  + Rivales políticos.
	  + Resto de amenazas: datos entregados a grandes corporaciones (Google, Facebook), malware etc.
	- ## 3. Seguridad operacional vs. Seguridad intrumental
	  +  ^^Seguridad operacional^^: aquella centrada en el uso de **procesos y protocolos para aumentar la seguridad**.
	  + ^^Seguridad instrumental^^: aquella centrada en el uso de **herramientas y aplicaciones para aumentar la seguridad**.
- # Seguridad básica
	- #### 1. Contraseñas: 
	  
	  La mayoría de la seguridad depende de las contraseñas, pero todavía existen contraseñas como:
	  ```
	  password
	  pepe1997
	  urss1917
	  a&n2#yn8
	  ```
	  
	  Además sigue habiendo filtraciones de contraseñas, exponiendo hasta las contraseñas seguras.
	- ### 1.1. Solución:
	  ^^**Seguridad Operacional**^^
	  + **Larga** es mejor que compleja
	  + **Cambiarlas** de vez en cuando
	  + **Nunca reutilizarlas**
	- ### 1.1. Solución:
	  ^^**Seguridad Instrumental**^^
	  + [HaveIBeenPwned](https://haveibeenpwned.com/) --> sitio web para saber si algún servicio que usamos ha sido hackeado
	  + [KeePassXC](https://keepassxc.org/) --> gestor de contraseñas local y con extensión de navegador
	  + AuthPass --> gestor de contraseñas local y con app movil
	  + LastPass o BitWarden --> servicio online de gestión de contraseñas
	- #### 2. Software:
		- Aparecen vulnerabilidades nuevas todos los meses
		- Aparece nuevo malware frecuentemente
	- ##### 2.1. Solución:
		- **Seguridad Operacional**
			- Actualizar frecuentemente
			- Instalar solo de fuentes fiables
		- **Seguridad Instrumental**
			- GNU/Linux
				- ¿Por qué se dice que GNU/Linux es más seguro?
					- Porque al utilizarlo menos personas
			- Anti-Virus
				- WindowsDefender es suficientemente bueno y viene por defecto en Windows)
	- #### 3. Dispositivos:
		- Los teléfonos móviles, mediante sus antenas de telefonía anuncian su posición constantemente.
		- WiFi y Bluetooth también pueden (menos común y permite menos rango)
		- Eso se usa para rastrear e identificar a activistas
	- ##### 3.1 Solución:
		- Seguridad Operacional
		- Poner el modo avión o apagar cuando no se esté usando
		- Tener en cuenta qué información ofreces en una protesta
			- Seguridad Instrumental
		- Modo avión
		- Bolsa de Faraday
	- #### 4. Bloqueo de móvil:
		- Te arrestan en una manifestación. La policía tiene tu móvil. ¿Qué información podrán sacar?
	- ##### 4.1 Solución:
		- Seguridad Operacional
		- Cifrar el móvil
		- Utilizar un bloqueo seguro
		- Conoce al enemigo
			- Seguridad Instrumental
		- No utilizar bloqueo biométrico o de patrón
		- Cifrado nativo de Android o Apple
		- Hardenizar Android ([CopperheadOS](https://copperhead.co/android/), [GrapheneOS](https://grapheneos.org/)) --> sistemas operativos basados en Android centrados en seguridad
		- [Aplicaciones basadas en VeraCrypt](https://www.veracrypt.fr/en/Android%20%26%20iOS%20Support.html) --> aplicaciones para tener un sistema de ficheros encriptado en el movil
	- #### 5. Cifrado de ordenador:
		- Si se tiene acceso físico al ordenador estás vendido. Y la policía si te arresta tendrá acceso físico
	- ##### 5.1 Solución:
		- Seguridad Operacional
		- Mantener el ordenador apagado cuando no se usa
		- Contraseña segura y secreta
			- Seguridad Instrumental
		- Linux: [LUKS](https://wiki.archlinux.org/index.php/Dm-crypt), [VeraCrypt](https://www.veracrypt.fr/en/Home.html), y [más en la ArchWiki](https://wiki.archlinux.org/index.php/Disk_encryption)
		- Windows: [BitLocker](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview), [VeraCrypt](https://www.veracrypt.fr/en/Home.html)
		- Apple: [FileVault](https://support.apple.com/en-us/HT204837), [VeraCrypt](https://www.veracrypt.fr/en/Home.html)
	- #### 6. Conversaciones:
		- Para coordinar acciones en grupo es necesario comunicarse, y a la policía le gusta saber lo que se dice en esos grupos
	- ##### 6.1 Solución:
		- Seguridad Operacional
		- Cuidado con quién entra en el grupo
		- Cuidado con qué dices en el grupo
		- Borra los mensajes sensibles
		- El punto más débil no eres tú, puede ser otra
			- Seguridad Instrumental
		- [Signal](https://www.signal.org/)
		- [Wire](https://wire.com/en/)
		  
		  ---
### Anonimato
#### 1. Recolección masiva
	- Las nuevas formas de recolección de datos presentan amenazas nuevas. Lo importante no es ya los datos sino los metadatos.
#### 2. Privacidad
	- Con el control y recolección de información por parte de anunciantes, Google, Facebook, data brokers y prácticamente cualquiera nuestra actividad en internet funciona para crear perfiles que nos conocen mejor que a nosotras.
##### 2.1. Solución:
	- Seguridad Operacional
		- Conoce el valor de tus datos
		- Seguridad Instrumental
		- Navegadores: [Firefox](https://www.mozilla.org/en-US/firefox/new/), [Brave](https://brave.com/)
		- Buscadores: [DuckDuckGo](https://duckduckgo.com/), [StartPage](https://www.startpage.com/)
		- Extensiones para ofuscar IP de origen: [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/), [HTTPSEverywhere](https://www.eff.org/https-everywhere)
		- [CookieAutoDelete](https://addons.mozilla.org/en-US/firefox/addon/cookie-autodelete/), [Decentraleyes](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/?src=collection), y [bastantes más](https://blog.mozilla.org/firefox/make-your-firefox-browser-a-privacy-superpower-with-these-extensions/)
		- Bloquear scripts para evitar rastreadores: [NoScript](https://noscript.net/)
#### 3. Redes
- Nada en la red es anónimo, al menos hoy en día. Si realmente queremos que nadie sepa lo que hacemos hay que buscar otras formas de navegar internet.
##### 3.1. Solución:
	- Seguridad Operacional
		- No digas nada, no lo relaciones contigo.
		- Sigue el resto de consejos, especialmente el de separar perfiles.
			- Seguridad Instrumental
		- [Tor](https://www.torproject.org/) ([Tails](https://tails.boum.org/), [Whonix](https://www.whonix.org/)
		- [I2P](https://geti2p.net/en/)
#### 4. Reconocimiento físico
- Todas las manifestaciones son grabadas. Las caras y los tatuajes son muy útiles para reconocerte, tápalos.
##### 4.1. Solución:
	- Seguridad Operacional
	     -Tapa todo aquello que te pueda identificar físicamente
	  
	  ---
### Seguridad avanzada

1. Separación de perfiles:
	- Crear distintos perfiles: personal, activista, profesional... con distintos grados de vinculación a ti y totalmente separados entre ellos.
	- Separarlos desde el principio.
	- También puede ser útil tener perfiles de usar y tirar.
	  
	  2. No crear más información de la necesaria
	- Toda información que no generas no puede ser utilizada contra ti
	  
	    3. Pensamiento ofensivo
		- El atacante utilizará el método que le sea más fácil. Intentar atacarte te ayuda a encontrar los puntos débiles.
		  
		    4. OSINT
	- [Inteligencia de fuentes abiertas, entrada de Wikipedia](https://es.wikipedia.org/wiki/Inteligencia_de_fuentes_abiertas), [OSINT framework](https://osintframework.com/)
	  
	    5. Ingeniería social
		- Infiltrar, engañar, nada les parece demasiado. Pero nunca parecen así. No hay que caer en la paranoia ni confiarnos demasiado.
		  
		  ---
### Conclusiones


---
### Referencias
- [Guía de Defensa Digital para Organizaciones Sociales](https://lalibre.net/wp-content/uploads/2022/09/Guia-de-proteccion-digital.pdf)
- [Manual de autodefensa en la era de la digitalización forzada o Resistencia al capitalismo de vigilancia](https://codeberg.org/PrivacyFirst/Data_Protection/issues)