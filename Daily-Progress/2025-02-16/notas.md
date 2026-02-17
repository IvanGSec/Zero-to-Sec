
(12:05-15:02)

#################################### CONCEPTOS BASICOS POWERSHELL ##################################################

*Los comandos de powershell se les conoce como cmdlets.

*Siguen la constante Verb-Noun (Verbo-Sustantivo).Gracias a esto hace que sea fácil entender cada cmdlet.El "Verb" describe la accion y el "Noun" especifica el objeto al que se le realiza la accion.

Por ejemplo:

*Get-Content*: Recupera (obtiente) el contenido de un archivo y lo muestra en la consola.
*Set-Location*: Cambia (configura) el directorio de trabajo actual.

Para descubrir todos los cmdlets ,funciones, alias o scripts disponibles ejecutables en la seccion actual de PowerShell podemos usar *Get-Command* .

Ejemplos:

* Get-Command (Ver todos los comandos disponibles,todos los que PowerShell puede ejecutar)
* Get-Command Get-Process (Busca un comando por nombre.Dice que es,donde esta y que tipo es)
* Get-Command *service* (Busca comandos por palabra clave.En ese caso "service")
* Get-Command -CommandType Cmdlet (Para ver solamente cmdlets)
* Get-Command -CommandType Alias (Para ver solamente alias)

# Extra: Para ver informacion detallada de un comando.

* Get-Help Get-Process ( Get-Help Get-Process -Ejemplo )


# TABLA DE Get-Command – Usos esenciales

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Command` | Muestra todos los comandos disponibles en PowerShell. | `Get-Command` |
| `Get-Command <nombre>` | Busca un comando específico por nombre. | `Get-Command Get-Process` |
| `Get-Command *palabra*` | Busca comandos que contengan una palabra clave. | `Get-Command *service*` |
| `Get-Command -CommandType Cmdlet` | Muestra solo cmdlets. | `Get-Command -CommandType Cmdlet` |
| `Get-Command -CommandType Function` | Muestra solo funciones. | `Get-Command -CommandType Function` |
| `Get-Command -CommandType Alias` | Muestra solo alias. | `Get-Command -CommandType Alias` |
| `Get-Command -Module <nombre>` | Muestra comandos de un módulo específico. | `Get-Command -Module Microsoft.PowerShell.Management` |
| `Get-Command -Noun <nombre>` | Busca comandos por su “sustantivo” (segunda parte del nombre). | `Get-Command -Noun Process` |
| `Get-Command -Verb <nombre>` | Busca comandos por su “verbo” (primera parte del nombre). | `Get-Command -Verb Get` |

---

# Get-Help – Usos esenciales

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Help <cmdlet>` | Muestra la ayuda básica del cmdlet. | `Get-Help Get-Process` |
| `Get-Help <cmdlet> -Examples` | Muestra ejemplos reales de uso. | `Get-Help New-LocalUser -Examples` |
| `Get-Help <cmdlet> -Full` | Muestra toda la documentación completa. | `Get-Help Set-Service -Full` |
| `Get-Help <cmdlet> -Online` | Abre la documentación oficial en el navegador. | `Get-Help Get-Service -Online` |
| `Get-Help <cmdlet> -Detailed` | Muestra ayuda extendida con explicaciones. | `Get-Help Get-EventLog -Detailed` |

---

# Get-Service – Usos esenciales

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Service` | Lista todos los servicios del sistema. | `Get-Service` |
| `Get-Service <nombre>` | Muestra un servicio específico. | `Get-Service Spooler` |
| `Start-Service <nombre>` | Inicia un servicio. | `Start-Service Spooler` |
| `Stop-Service <nombre>` | Detiene un servicio. | `Stop-Service Spooler` |
| `Restart-Service <nombre>` | Reinicia un servicio. | `Restart-Service Spooler` |

---

# Get-Process – Usos esenciales

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Process` | Lista todos los procesos activos. | `Get-Process` |
| `Get-Process <nombre>` | Muestra un proceso específico. | `Get-Process chrome` |
| `Stop-Process -Name <nombre>` | Mata un proceso por nombre. | `Stop-Process -Name notepad` |
| `Stop-Process -Id <id>` | Mata un proceso por ID. | `Stop-Process -Id 1234` |
| `Get-Process` | Ordena procesos por uso de CPU. | `Sort-Object CPU -Descending`


---

# Comandos de Redes – Esenciales

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `ipconfig` | Muestra configuración IP. | `ipconfig /all` |
| `ping <host>` | Comprueba conectividad. | `ping google.com` |
| `tracert <host>` | Rastrea la ruta hacia un host. | `tracert 8.8.8.8` |
| `nslookup <dominio>` | Consulta DNS. | `nslookup microsoft.com` |
| `netstat -ano` | Muestra puertos y conexiones activas. | `netstat -ano` |
| `Get-NetIPAddress` | Muestra direcciones IP en PowerShell. | `Get-NetIPAddress` |
| `Test-NetConnection` | Diagnóstico avanzado de red. | `Test-NetConnection -Port 443 -ComputerName google.com` |

---

# PowerShell – Fundamentos para Principiantes

| Concepto | Descripción | Ejemplo |
|----------|-------------|---------|
| Cmdlet | Comando nativo de PowerShell (Verbo-Sustantivo). | `Get-Process` |
| Alias | Nombre corto de un cmdlet. | `ls` → `Get-ChildItem` |
| Variables | Guardan valores. | `$nombre = "Ivan"` |
| Listar archivos | Ver contenido de un directorio. | `Get-ChildItem` |
| Navegar directorios | Cambiar de carpeta. | `Set-Location C:\Windows` |
| Filtrar | Usar condiciones. | `Get-Process Where-Object {$_.CPU -gt 10}` |
| Ordenar | Ordenar resultados. | `Sort-Object -Property Name` |
| Exportar | Guardar datos en CSV. | `Get-Process Export-Csv procesos.csv` |




--------------------------------------------------------------------




################## NAVEGAR POR EL SISTEMA DE ARCHIVOS Y TRABAJAR CON ARCHIVOS #######################



Aqui aprendemos los comandos esenciales para moverte por el sistema de archivos,listar contenido,crear archivos y trabajar con ellos usando PowerShell.


# 1. Navegar por el sistema de archivos

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Location` | Muestra la ruta actual (equivalente a `pwd` en Unix). | `Get-Location` |
| `Set-Location <ruta>` | Cambia de directorio (equivalente a `cd`). | `Set-Location C:\Users` |
| `Set-Location ..` | Sube un nivel. | `Set-Location ..` |
| `Set-Location ~` | Va al directorio del usuario. | `Set-Location ~` |

---

# 2. Listar archivos y carpetas

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-ChildItem` | Lista archivos y carpetas (equivalente a `ls`). | `Get-ChildItem` |
| `Get-ChildItem -Recurse` | Lista contenido de forma recursiva. | `Get-ChildItem -Recurse` |
| `Get-ChildItem *.txt` | Filtra por extensión. | `Get-ChildItem *.txt` |

Alias útiles:  
- `ls`  
- `dir`  
- `gci`

---

# 3. Trabajar con archivos

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-Content <archivo>` | Muestra el contenido de un archivo (equivalente a `cat`). | `Get-Content notas.txt` |
| `Set-Content <archivo>` | Sobrescribe el contenido del archivo. | `Set-Content notas.txt "Hola"` |
| `Add-Content <archivo>` | Añade texto al final del archivo. | `Add-Content notas.txt "Nueva línea"` |
| `New-Item` | Crea un archivo o carpeta. | `New-Item archivo.txt` |
| `Remove-Item` | Elimina archivos o carpetas. | `Remove-Item archivo.txt` |

Alias útiles:  
- `cat` → `Get-Content`  
- `gc` → `Get-Content`  

---

# 4. Crear y gestionar directorios

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `New-Item -ItemType Directory` | Crea una carpeta. | `New-Item -ItemType Directory Logs` |
| `Remove-Item -Recurse` | Elimina carpetas con contenido. | `Remove-Item Logs -Recurse` |

---

# 5. Buscar archivos

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `Get-ChildItem -Recurse -Filter` | Busca archivos por nombre o patrón. | `Get-ChildItem -Recurse -Filter *.log` |
| `Get-ChildItem -Recurse | Where-Object` | Filtra por tamaño, fecha, etc. | `Get-ChildItem -Recurse | Where-Object {$_.Length -gt 1MB}` |

---

# 6. Resumen rápido

- `pwd` en Unix → `Get-Location`
- `cd` en Unix → `Set-Location`
- `ls` en Unix → `Get-ChildItem`
- `cat` en Unix → `Get-Content`
- Crear archivo → `New-Item`
- Borrar archivo → `Remove-Item`
- Añadir contenido → `Add-Content`
- Sobrescribir → `Set-Content`

Aqui aprendi como moverme dentro del sistema de archivos usando PowerShell.Use de referencia a Unix ya que me ayuda a relacionar mejor el uso de cada comando de PowerShell gracias a que tengo ya los conocimientos de Linux basicos.




-----------------------------------------------------------------------------------




########################## Datos de tuberías, filtrados y clasificación ##################################


Esta tarea enseña cómo encadenar comandos usando tuberías (`|`),cómo filtrar datos con `Where-Object` y cómo ordenar resultados con `Sort-Object`. Es uno de los pilares fundamentales de PowerShell.

------

## 1. Uso de tuberías (pipeline)

La tubería (`|`) envía la salida de un comando como entrada del siguiente.

| Ejemplo | Descripción |
|---------|-------------|
| `Get-Process \| Sort-Object CPU` | Ordena los procesos por uso de CPU. |
| `Get-Service \| Where-Object {$_.Status -eq "Running"}` | Filtra servicios que están en ejecución. |
| `Get-ChildItem \| Select-Object Name, Length` | Pasa archivos a un selector de propiedades. |

-------


## 2. Filtrar datos con Where-Object

`Where-Object` permite filtrar objetos según una condición sobre sus propiedades.

### Sintaxis general

Where-Object { $_.<Propiedad> -Operador Valor }

OPERADORES COMUNES:

Operador	                     Significado
-eq       	                      Igual
-ne	                            No igual
-gt	                            Mayor que
-lt	                            Menor que
-ge	                          Mayor o igual
-le	                          Menor o igual
-like	                Coincidencia con comodines (*)
-match	           Coincidencia con expresiones regulares

EJEMPLOS:

`Get-Process \	Where-Object {$_.CPU -gt 10}`	Procesos con más de 10 segundos de CPU.
`Get-Service \	Where-Object {$_.Status -eq "Running"}`	Servicios en ejecución.
`Get-ChildItem \	Where-Object {$_.Length -gt 1MB}`	Archivos mayores de 1 MB.
`Get-LocalUser \	Where-Object {$_.Enabled -eq $true}`	Usuarios locales habilitados.


-----


## 3. Ordenar datos con Sort-Object

* Sort-Object ordena resultados por una o varias propiedades.
Comando	Descripción

`Get-Process \	Sort-Object CPU`	Orden ascendente por CPU.
`Get-Process \	Sort-Object CPU -Descending`	Orden descendente por CPU.
`Get-Service \	Sort-Object Status, Name`	Ordena por estado y luego por nombre.
`Get-ChildItem \	Sort-Object Length`	Ordena archivos por tamaño.

-----


## 4. Combinar filtrado con ordenacion 

*Ejemplos tipicos:

* Get-Process `
    | Where-Object {$_.CPU -gt 5} `
    | Sort-Object CPU -Descending


* Get-ChildItem -Recurse `
    | Where-Object {$_.Extension -eq ".log"} `
    | Sort-Object Length -Descending


* Get-Service `
    | Where-Object {$_.Status -eq "Running"} `
    | Sort-Object Name


--------


 5. Resumen rápido

    | → conecta comandos (pipeline).

    Where-Object → filtra objetos según condiciones.

    Sort-Object → ordena resultados.

    PowerShell trabaja con objetos, lo que hace el filtrado y la clasificación mucho más potentes que en shells basados en texto.

Apuntes mayormente copiados y pegados usando la IA.La uso para buscar informacion mas rapidamente y copiar al repositorio.

FIN DE POWERSHELL POR HOY 
(12:05-15:02)

    --------------------------------------------------------------------------------------------------------------

(15:13-17:52)

########################### SHELLS LINUX #######################################

## Vamos a hacer un repaso de que son y que tipos de shells existen primero:

-Que es?:

* Una shell es un un programa que recibe comandos del usuario y los ejecuta.Es como un interprete entre yo y el sistema operativo.
* Una capa que permite hablar con Linux usando texto.
* Una interfaz para ejecutar programas,mover archivos,automatizar tareas,etc.

*********** 1.Tipos de shells Linux: **************

* bash : La mas tipica.Viene por defecto en la mayoria de distros.
* zsh : Mas moderna.Utilizada en macOS.Autocompletado avanzado.
* fish : Muy amigable.Sugerencias automaticas
* sh : Shell clasica,muy basica.
* ksh : Antigua pero potente,usada en entornos UNIX.

Resumen: La shell no es Linux ni es el terminal.Es el programa que corre por dentro del terminal.

[Usuario] (Yo)
   ↓
[Terminal] (Gnome,Teminal)
   ↓
[Shell] (Bash,Zsh,sh,cmd,powershell etc)
   ↓
[Sistema operativo (Ubuntu,Kali,Windows,macOS etc )]
   ↓
[Kernel Linux] (O kernel windows NT de windows,O kernel XNU de macOS)
   ↓
[Hardware: CPU, RAM, disco] (El pc)


-La mayoria de distribuciones de linux usan Bash (Bourne Again Shell).
-Con el comando echo $SHELL veriamos que shell estamos usando.
-Con el comando cat /etc/shells veriamos todas las shells disponibles en una lista.
-Con el comando chsh -s /usr/bin/[shell que queramos] convertiriamos esta shell en predeterminada.



(((((((((((((((((((((( Dato curioso,estoy buscando porque algunas shells se guardan en /usr/bin/ (zsh por ejemplo),y porque otras se guardan en /bin/ (como Bash por ejemplo).Al parecer es la manera de organizarse que tiene linux.La razon es funcional e historica.Linux (y UNIX antes),separa los binarios segun,cuando y como deben estar disponibles.Los binarios escenciales y los no escenciales.

# Binarios escenciales:
Son basicamente los programas que deben estar disponibles incluso si el sistema esta medio roto.Ejemplos tipicos de binarios serian:

* /bin/bash
* /bin/sh
* /bin/mkdir
* /bin/cp
* /bin/ls

Porque?Porque /bin esta en la particion raiz se siempre se monta al arrancar.Si el sistema entra en modo rescate,o si /usr no esta disponible,necesitas una shell funcional para reparar el sistema.Por eso Bash por ejemplo suele estar en /bin.

# Binarios no escenciales:
Aqui van los programas que no son criticos para arrancar el sistema.Ejemplos como:

* /usr/bin/zsh
* /usr/bin/fish
* /usr/bin/python3
* /usr/bin/vim

Estas shells y programas son opcionales asique no necesitan estar en modo rescate.Para terminar,la ubicacion de las shells puede cambiar dependiendo de la distro de linux que estes utilizando )))))))))))))))))))))))))))))))))))


Prosigo con las shells.
En esta imagen podemos ver un poco mas detallado las diferencias entre Bash,Fish y Zsh.

<img width="1254" height="622" alt="Captura de pantalla 2026-02-16 164145" src="https://github.com/user-attachments/assets/b17436f4-4e85-4b97-a34b-2ecaad4cc88b" />

(Es la primera vez que subo una imagen a GitHub.Espero que se pueda ver bien :,)





************ 2.Scriptings y componentes de Shell **********

-Un script de shell no es mas que un conjunto de comandos.Para una tarea repetitiva que requiera varios comandos por ejemplo,lo suyo es usar un script y no ir uno por uno.Para economizar el tiempo.Todos los shells de antes tienen capacidad de scripting.Antes de aprender sobre los scripts necesito saber que a pesar de que los shells tengan capacidad de scripting,no significa que solo pueda hacerlo en ese shell.Puede valer para varios lenguajes de programacion.
A diferencia de los otros comandos que existen en las otras shell,necesitamos un editor de texto para un script.Este archivo debe estar nombrado con la extension .sh ,que es la extension predeterminada para los scripts de Bash.
Por ejemplo:

user@hostname:~$ nano first_script.sh 

-Cada script (guion) debe comenzar desde el SHEBANG.
-Pero que es un SHEBANG?

*Es la primera linea de un script en linux que le dice al sistema que interprete debe usar para ejecutar ese archivo.Se escribe asi:

  #! /ruta/al/interprete   /// ese #! es el SHEBANG.

-Para que sirve?

*Sirve para que el sistema sepa con que programa ejecutar el script,sin que yo tenga que escribirlo manualmente cada vez.Por ejemplo:

  Si mi script empieza con    #! /bin/bash     ,entonces cuando ejecute    ./mi_script.sh     ,linux sabe que tiene que usar Bash para 
  interpretarlo:

  * Bash
  * Python
  * Zsh
  * Fish
  * Perl
  * etc

Sin el shebang,el sitstema usaria la shell por defecto del usuario (normalmente Bash),lo cual puede romper scripts escritos para
otro interprete.

Ejemplos:

1. Script en Bash:

    #! /bin/bash
    echo "Hola desde Bash"

2. Script en Python:

    #! /usr/bin/python3
   print ("Hola desde Python")

3. Script en Zsh:

    #! /usr/bin/zsh
    echo "Hola desde Zsh"


Porque se llama Shebang?Porque # se pronuncia "sharp" y ! se pronuncia "bang".Sharp-Bang --> Shebang.


# Variables.

-Ahora pasamos a las variables.Las variables almacenan un valor en su interior.Podemos guardar valores complejos,como una URL,una ruta de acceso
de archivos,etc,varias veces en mi script.En lugar de tener que memorizarlos y escribirlos todo el rato,lo guardamos dentro de una variable y
usar el nombre de la variable donde lo necesite.
Un ejemplo seria este:

[[[ #!/bin/bash (Shebang)

echo "Hola,cual es tu nombre?"
read name
echo "Bienvenido, $name" ]]]

Ese seria el contenido del script.El script seria ./[aqui nombre del script].sh . ./bicicleta.sh por ejemplo.No es obligatorio usar .sh o 
.[cualquier shell] pero si es importante ponerlo para tanto yo como cualquier persona sepa a que shell se refiere.

Aunque estes usando Bash,es importante hacer un shebang de      #! /bin/bash       porque,aunque para cualquier usuario que use Bash no note la
diferencia,para alguien que este usando otra shell como zsh,podria tener problemas.Asique lo recomendable seria especificar siempre el shebang.



(15:13-17:52)












