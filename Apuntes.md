Metodologías Principales: 

OSSTMM (Open Source Security Testing Methodology Manual)
Pentesting
ISSAF (Information Systems Security Assessment Framework)
OTP (OWASP Testing Project)

Metodología a realizar: 

- Definición del alcance del pentesting
- Recopilación de Información
- Identificación y Análisis de Vulnerabilidades
- Explotación de las Vulnerabilidades
- Post-explotación
- Elaboración de Documento de Reporte

Herramientas útiles para recopilación de información:
- Whois: Es un comando en la terminal de Kali que enseña información sobre la página web que le pongas delante del comendo "whois", puede darte pistas sobre quien ha creado la página, su nacionalidad, donde vive, de que se trata la web, etc.
- Archive.org: Es una web que contiene todos los dominios del mundo y su recorrido, puede enseñar cuando se ha creado un página web, cuando se ha eliminado, el trayecto que ha tenido dicha página, etc.
- The Harvester: Viene instalado por defecto en Kali y sirve para obtener información sobre páginas web y diferentes dominios. Ejecutar "theHarvester -h" en la terminal para que enseñe todos los atajos y comandos que puede realizar The Harvester.
- Maltego: Probablemente la herramienta más últil para recopilación pasiva de información
- Wireshark: Herramienta de análisis de tráfico de red

Comandos más comunes pero útiles en Wireshark:

-- Filtros por Dirección IP
IP de origen específica:
ip.src == 192.168.1.10

IP de destino específica:
ip.dst == 192.168.1.20

-- Cualquier tráfico relacionado con una IP específica:
ip.addr == 192.168.1.30

-- Filtros por Puertos
Tráfico en un puerto específico (por ejemplo, puerto 80 para HTTP):
tcp.port == 80

-- Tráfico en un rango de puertos:
tcp.port >= 1000 && tcp.port <= 2000

-- Filtros por Contenido de Carga Útil (Payload)
Buscar palabras clave en paquetes HTTP:

http contains "password"

-- Filtrar paquetes que contengan una dirección específica o texto en cualquier protocolo:
frame contains "example.com"

-- Filtros para Conversaciones Específicas
Filtrar una conversación TCP:
Clic derecho sobre un paquete específico y selecciona "Follow TCP Stream".
Esto mostrará solo los paquetes pertenecientes a esa conversación.

-- Otros Filtros Útiles
Mostrar paquetes con errores o retransmisiones:
tcp.analysis.retransmission

-- Mostrar paquetes con ACK duplicados:
tcp.analysis.duplicate_ack

-- Mostrar solo paquetes con una longitud de datos específica:
frame.len == 128

-- Para ver el tipo de método que está utilizando:
   http.request.method
   http.request.method=="GET"
   http.request.method=="POST"

-- Ctrl + F:
   Ésta combinación de teclas siempre va a ser de ayuda al buscar palabras clave dentro de Wireshark y los paquetes que tenemos a la vista al comenzar el análisis de tráfico de red.

-- Búsqueda dentro del XML de las peticiones:
   xml.cdata contains "palabra clave". Muy útil para encontrar rápido cadenas de texto que buscamos.
