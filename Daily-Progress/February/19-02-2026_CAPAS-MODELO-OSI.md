
Me queda pendiente conceptos basicos de PowerShell,que pienso dejar mas adelante por el dolor de cabeza que me dan.
Hoy me centrare mas en profundidad en conceptos de redes o en general Networking.

--------

## 1. NETWORKING CONCEPTS (CONCEPTOS DE REDES)

-Esta es la primera sala de 4 salas dedicadas a introducirme en conceptos de networking vitales y protocolos de networking
mas comunes:

* Conceptos de networking // Networking Concepts (que es esta sala 1)
* Redes escenciales // Networking Essentials
* Protocolos basicos de red /( Networking Core Protocols
* Portocolos seguros de redes // Networking Secure Protocols

-Los objetivos,y cuando termine esta sala,tengo que haber aprendido lo siguiente:

* Modelo de red ISO-OSI
* Direcciones IP,subredes y enrutamiento
* Numeros TCP,UPD y de puerto
* Como conectarse a un puerto TCP abierto desde la linea de comandos

-------

# Modelo OSI

-El modelo OSI (Open Systems Interconnection) es un modelo conceptual desarrollado por la ISO (International Organization for Standardization),que
describe como deben ocurrir las comunicaciones en una red informatica.En otras palabras el modelo OSI define un marco para comunicaciones de red
informatica.Aunque este modelo es teorico,es vital aprender y comprenderlo,ya que ayuda a comprender los conceptos de networtking en un nivel
mas profundo.El modelo OSI se compone de 7 capas:

* 1 . PHYSICAL Layer / Capa FISICA
* 2 . DATA LINK Layer / Capa de ENLACE DE DATOS
* 3 . NETWORK Layer / Capa de RED
* 4 . TRANSPORT Layer/ Capa de TRANSPORTE
* 5 . SESSION Layer / Capa de SESION
* 6 . PRESENTATION Layer / Capa de PRESENTACION
* 7 . APPLICATION Layer / Capa de APLICACION

<img width="608" height="466" alt="Captura de pantalla 2026-02-19 121213" src="https://github.com/user-attachments/assets/84f808bd-a1a1-4c95-829b-c1df38efc558" />

Vamos a resumir cada capa.

# CAPA 1. PHYSICAL (FISICA)

* TRANSMITE SEÑALES POR EL MEDIO FISICO.

-La capa 1,tambien llamada capa fisica o physical,se refiere a la conexion fisica entre dispositivos.Esto incluye el medio,como un cable Ethernet,y la definicion de
los codigos binarios 0 y 1.No entendi muy bien esto de los 0 y 1 asique estuve investigando.Resulta que la capa 1 trabaja con señales fisicas reales.En otras palabras:

"La capa fisica decide que señal fisica significa 0 y cual significa 1"


* 1- En el cable de Ethernet (cobre):
Los bits se representan mediante variaciones de voltaje.
Un cierto nivel se interpreta como 1 y otro nivel de voltaje como 0.No es siempre tan simple como “alto = 1, bajo = 0”,porque Ethernet usa codificaciones más complejas
(como Manchester o PAM-5) pero la idea base es esa:

    "La capa física define qué voltaje significa cada bit"


* 2- En fibra optica:
No hay voltaje,sino luz. (Pulso de luz 1 ,ausencia de luz 0)
O en codificaciones mas avanzadas,diferentes intensidades o fases de la luz representan distintos valores


* 3- En Wi-Fi (Inalambrico) :
Los bits se representan mediante ondas de radio.Cambios de amplitud,frecuencia o fase,representan 0 o 1. Y la capa fisica es la que define
exactamente que cambio en la señal corresponde a cada bit.

# CAPA 2. DATA LINK (ENLACE DE DATOS)

* CONECTA DISPOSITIVOS DENTRO DEL MISMO SEGMENTO

-La capa fisica es la encargada de proporcionar el medio por el cual viajan las señales.Ya sea un cable,fibra optica o el aire en el caso del
wifi.La capa de enlace de datos (tambien llamada la capa 2 o DATA LINK),define las reglas que permiten que los dispositivos que estan conectados
al mismo medio puedan comunicarse entre si.Dicho de forma simple,la capa 2 establece un acuerdo entre todos los dispositivos que comparten un
mismo segmento de red para que sepan como enviarse informacion sin interferencias.

-Un segmento de red es simplemente un grupo de dispositivos que utilizan el mismo canal de comunicacion,por ejemplo,una oficina con diez
computadoras conectadas a un mismo switch forma un segmento de red.

-Entre las tecnologias que funcionan en la capa 2 se encuentra Ethernet (802.3) y wifi (802.11).Tanto Ethernet como wifi utilizan 
direcciones de 6 bytes llamadas "direcciones MAC" (Media Access Control).Estas direcciones suelen escribirse en formato hexadecimal,separando
cada byte con dos puntos.Por ejemplo:

* AA:BB:CC:DD:EE:FF

-Los primeros 3 bytes de la direccion identifican al fabricante del dispositivo.

<img width="1089" height="570" alt="Captura de pantalla 2026-02-19 174032" src="https://github.com/user-attachments/assets/6a6842ec-c823-44c1-90ad-a85aa4f381cf" />

(11:30-14:50)
(18:05)

-Esperamos ver dos direcciones MAC en cada trama en comunicacion de red real a traves de Ethernet o Wifi.El paquete en la siguiente imagen
muestra:

* La direccion de enlace de datos de destino (direccion MAC) resaltada en amarillo.
* La direccion de enlace de datos de origen (direccion MAC) resaltada en azul.
* Los bits restantes muestran los datos que se envian.

<img width="1261" height="437" alt="Captura de pantalla 2026-02-19 184945" src="https://github.com/user-attachments/assets/e1152ce3-0e21-4b71-ac97-6b29772cd1f4" />

# CAPA 3. NETWORK (REDES)

* ENCUENTRA RUTAS Y MANEJA DIRECCIONES IP

-La capa de enlace de datos (DATA LINK capa 2),se encarga de que los dispositivos dentro del mismo segmento de red se comuniquen correctamente
entre sí.Sin embargo,cuando necesitamos enviar informacion entre redes diferentes (por ejemplo,entre oficinas ubicadas en distintas ciudades o 
paises) entra en juego la capa de red,es decir,la capa 3.Esta capa se ocupa de manejar direcciones logicas,como las direcciones IP,y de encontrar
un camino adecuado para que los paquetes viajen de una red a otra.En otras palabras,la capa 3 decide por donde deben pasar los datos para llegar 
a su destino,incluso cuando existen varias rutas posibles.Imagina que una empresa tiene oficinas en diferentes ciudades o paises: la capa 3 es la
responsable de conectar esas oficinas entre si.En un ejemplo tipico,dos computadoras pueden eestar en redes diferentes pero conectadas a traves de
varios routers,la capa 3 elige la mejor ruta para que los paquetes lleguen correctamente.Entre los protocolos que pertenecen a esta capa se 
encuentran IP, ICMP, y tecnologias de VPN como IPSec o SSL/TLS.

<img width="943" height="440" alt="Captura de pantalla 2026-02-21 133219" src="https://github.com/user-attachments/assets/a05f7bfd-399d-4e3e-b6f0-5a19708733fe" />

# CAPA 4. TRANSPORT (TRANSPORTE)

* ENTREGA DATOS FIABLES ENTRE APLICACIONES

-Capa 4,la capa de transporte,,se encarga de que dos aplicaciones que estan en dispositivos distintos puedan comunicarse directamente entre si.
Por ejemplo,cuando uso mi navegador web para conectarme a un servidor,esa comunicacion de extremo a extremo ocurre gracias a esta capa
de transporte (4).Esta capa se ocupa de funciones importantes como controlar la velocidad a la que se envian los datos,dividir la informacion
en partes mas pequeñas para poder transmitirlas,y corregir errores si algo se pierde o llega dañado.Los protocolos mas conocidos son TCP
que garantiza que los datos lleguen completos y en orden,y UDP que es mas rapido pero no realiza comprobaciones tan estrictas.Gracias a
la capa 4,las aplicaciones pueden intercambiar informacion de manera confiable o rapida segun lo necesiten.

# CAPA 5. SESSION

* MANTIENE Y COORDINA LA COMUNICACION ENTRE APLICACIONES

-La capa de sesion,tambien llamada capa 5,se encarga de iniciar,mantener y coordinar la comunicacion entre aplicaciones que estan funcionando 
en dispositivos distintos.Establecer una sesion significa que dos aplicaciones comienzan a comunicarse y el como lo haran.Ademas ofrece mecanismos para recuperarse si ocurre un fallo durante la transmision.Gracias a la capa de session,las aplicaciones pueden mantener una conversacion organizada sin perder el hilo.Algunos ejemplos de tecnologias que funcionan en esta capa son NFS, que permite acceder a archivos remotos como si fueran locales,y RCP,que permite que un programa ejecute funciones en otro equipo como si estuvieran en el mismo sistema.
Bunos ejemplos serian:

* RCP (Remote Procedure Call): Permite que un programa en un ordenador ejecute funciones o procedimientos en otro ordenador como si fuesen locales.
* NFS (Network File System): Te permite acceder a archivos que estan en otro ordenador como si estuvieran en el tuyo.

# CAPA 6. PRESENTATION (PRESENTACION)

* CONVIERTE,CODIFICA Y PREPARA LOS DATOS.

-La capa de presentacion,tambien llamada capa 6,se encarga de transformar los datos para que la aplicacion que los escribe pueda entenderlos sin problemas.Esta capa maneja tareas como la codificacion,la compresion y la encriptacion.Por ejemplo cuando hablamos de codificacion de caracteres,usamos estandares como ASCII o Unicode para que todos los sistemas interpreten las letras y los simbolos de la misma manera.Tambien interviene cuando guardamos o enviamos imagenes usando formatos como JPEG,GIF o PNG.Ademas,cuando adjuntamos un archivo a un correo electronico,se utiliza un estandar llamado MIME,que convierte archivos binarios en texto ASCII para que puedan viajar correctamente por sistemas que solo aceptan ciertos tipos de caracteres.En resumen,la capa 6 adapta,convierte y prepara los datos para que la capa de aplicacion pueda trabajar con ellos sin importar el formato original.

# CAPA 7. APLICATION (APLICACION)

* OFRECE SERVICIOS DE RED A LAS APLICACIONES.

-La capa de aplicacion,tambien llamada capa 7,es la que directamente interactua con los programas que usa el usuario,como el navegador web,el correo electronico o las aplicaciones de mensajeria.Esta capa proporciona los servicios de red que esas aplicaciones necesitan para funcionar.Por ejemplo,cuando tu navegador solicita una pagina web,utiliza el protocolo HTTP,que pertenece a esta capa.Lo mismo ocurre cuando envias o recibes correos electronicos mediante protocolos como SMTP, POP3 o IMAP,o cuando un sistema necesita traducir un nombre de dominio a esta direccion IP usando DNS.La capa de aplicacion reune todos estos protocolos y servicios para que las aplicaciones puedan comunicarse a traves de la red sin que el usuario tenga que preocuparse por los detalles tecnicos de las capas inferiores.

<img width="1250" height="528" alt="Captura de pantalla 2026-02-21 140540" src="https://github.com/user-attachments/assets/7ed51acb-5bb8-4e92-8ffb-fa2d2370663c" />

------------------------------------
