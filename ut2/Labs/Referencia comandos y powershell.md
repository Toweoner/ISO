## El Símbolo del sistema

La línea de comandos Windows, que antes se ejecutaba en una máquina virtual llamada VDM (Virtual Dos Machine), comunica, desde Windows 7, con el núcleo del sistema operativo por medio del proceso padre conhost.exe. Para abrir una ventana de Símbolo del sistema en Windows 10, siga las siguientes instrucciones.

1. Ejecutar el Símbolo del sistema

Existen dos formas de lanzar el Símbolo del sistema en Windows: ya sea en modo estándar (con un token de usuario) o como administrador.

En Windows 10, dispone de varios métodos de acceso al Símbolo del sistema:

   - En la zona de búsqueda de la barra de tareas, introduzca directamente la palabra clave cmd o Símbolo del sistema. directamente la palabra clave cmd o Símbolo del sistema.

	- También puede hacer clic en el menú Inicio y a continuación en el enlace Todas las aplicaciones. Vaya hasta la carpeta Sistema de Windows y haga clic en esta carpeta. Verá el icono de la aplicación.

 A continuación, tanto en Windows 8 como en Windows 10, haga clic con el botón derecho en el icono Símbolo del sistema y a continuación, en la barra de comandos, seleccione la opción Ejecutar como administrador. El control de cuenta de usuario le pide autorizar la ejecución de la aplicación. Haga clic en Sí.
En la práctica, siempre deberá ejecutar el Símbolo del sistema como administrador.

*Hay una consideración importante que debemos tener en cuenta: si quiere modificar archivos de sistema desde el Símbolo del sistema, deberá activar la visualización de archivos y carpetas ocultos en el Explorador de Windows.*


---

2. Utilizar el Símbolo del sistema

- En la ventana de Símbolo del sistema introduzca: help o el nombre del comando seguido del modificador: /?. 

- Si desea obtener la sintaxis completa del comando clip, introduzca lo siguiente: clip /?.

- Si la salida de pantalla sobrepasa la dimensión de la ventana, introduzca: dir /? | more.

- Para desplazarse dentro de los árboles de directorio, utilice el comando cd. Puede acceder directamente a una 
unidad introduciendo la letra de esta seguida de dos puntos: e:, f:, etc.

- Podemos encontrar la carpeta principal utilizando el comando: cd\.

- Puede dejar que el sistema complete los comandos que usted ha introducido. Teclee: cd d y, a continuación, pulse la tecla [Tab] del teclado. El sistema le mostrará todos los directorios que empiezan por la letra D (por ejemplo, en Windows Vista, la carpeta Documentos). También funciona con los archivos, sea cual sea su extensión.

	* El método abreviado de teclado [Ctrl]+C le permitirá anular el comando en todo momento.
	* El método abreviado de teclado [Ctrl]+S le permitirá pausar un comando.

Pulse cualquier tecla para volver a iniciar la ejecución del comando en curso.

- En Windows 10, la arquitectura del Símbolo del sistema se ha renovado profundamente por primera vez desde hace mucho tiempo. El modo de edición también se ha mejorado para aportar una buena experiencia de usuario y una mejor interactividad con, por ejemplo, la implementación de las teclas de edición. Este nuevo modo de funcionamiento, que carga una nueva DLL en la ejecución del proceso conhost.exe, se puede activar o desactivar a través de la ventana de configuración de las propiedades de la consola. Para ello, active o desactive la opción Usar la consola heredada en la pestaña Opciones.

- En esta ventana, dispone de otras opciones para personalizar el comportamiento de la consola como por ejemplo el control de la opacidad de la consola en la pestaña Colores.


--- 

3. Utilizar las variables de entorno

Cuando introduce un comando, se efectúan tres operaciones:

Si el comando señala la ubicación de un archivo ejecutable, el intérprete de comandos comprobará si el archivo ejecutable existe en el directorio especificado. En caso de que no sea así, se encontrará con este tipo de error: "’Nombre del programa’ no se reconoce como comando interno o externo, un programa o un archivo por lotes ejecutable".

Si el comando no contiene la ubicación exacta del archivo ejecutable introducido, el intérprete de comandos comprobará si el archivo ejecutable existe en el directorio actual. Si no es el caso, intentará encontrar el programa en todas las ubicaciones definidas por la variable de entorno "Path" y en el orden asignado en los datos de este valor. Cada vez que descarga una herramienta, puede optar por guardar el archivo ejecutable en una de las ubicaciones ya establecidas por la variable de entorno "Path", o bien añadir esta nueva ubicación a la misma variable de entorno. Algunos programas lo hacen automáticamente. De lo contrario, el procedimiento a seguir es el siguiente:

- En el Panel de control, en la sección Sistema y seguridad, seleccione la opción Sistema/Cambiar configuración.
 Haga clic en el vínculo Opciones avanzadas y a continuación en el botón Variables de entorno.

- En el apartado Variables del sistema, haga clic en Path y después en el botón Editar.
 Escriba las diferentes ubicaciones de los archivos ejecutables.

Tenga en cuenta que es más fácil crear un directorio exclusivo. Cada comando debe separarse por punto y coma.

Por defecto, existen variables creadas por el sistema operativo. Hay dos tipos de variables:

	- Las variables de usuario que corresponden a la cuenta en la cual abre sesión.
	- Las variables de sistema que se aplican al conjunto de usuarios del ordenador.

* Para llegar a un directorio de sistema directamente es posible utilizar el nombre de la variable. Abra un Símbolo del sistema y a continuación ejecute uno de los siguientes comandos: explorer %windir% o explorer %userprofile%.

* ¿Cuál es la función de las variables? Una variable permite efectuar una operación sin importar el contexto de usuario o equipo en los que se ejecuta. Veamos dos ejemplos: la variable %USERPROFILE% se dirigirá al directorio de usuario, sea cual sea el usuario conectado: C:\Users\Juan o C:\Users\Isabel.

La variable %windir% remitirá al directorio de Windows, sin importar la letra de la unidad en la que esté instalado el sistema operativo: C:\Windows, D:\Windows, etc.

--- 
---

## Introducción a Windows PowerShell v5

* PowerShell es la nueva interfaz en línea de comandos y el nuevo lenguaje de scripts dedicado a la administración de sistemas Windows. PowerShell está orientado a objetos y utiliza el framework Microsoft .NET para la ejecución de herramientas de línea de comandos llamadas cmdlets o commandlets. Estos comandos permiten administrar los sistemas Windows locales o remotos. El formato abierto de PowerShell permite desarrollar y añadir cmdlets de terceros en forma de módulos portables para enriquecer el entorno estándar. Microsoft pone igualmente a su disposición numerosos ejemplos de scripts PowerShell desde el sitio https://code.msdn.microsoft.com/

* Windows 8 y Windows Server 2012 integran de forma nativa la versión 3.0 de PowerShell.
* Windows 10 integra de forma nativa la versión 5 de Microsoft PowerShell

1. Ejecución de PowerShell

Para ejecutar el anfitrión PowerShell, introduzca el comando Windows Powershell en el cuadro Buscar a la derecha del menú Inicio.

* En los resultados, haga clic
 en Windows PowerShell. Observe la presencia de Windows PowerShell ISE; este entorno gráfico, que aparece con Windows 7, permite escribir, ejecutar y probar scripts de PowerShell.

* En Windows 8, la herramienta PowerShell ISE está disponible en las herramientas de administración del sistema. En el Panel de control, sección Sistema y seguridad. Para visualizar las herramientas desde la interfaz de usuario, consulte el capítulo Mantenimiento del sistema.

* PowerShell asegura la compatibilidad con los comandos DOS a través de los alias, la lista de los cuales está disponible ejecutando el comando Get-Alias. Puede utilizar PowerShell para la ejecución de comandos DOS estándar, como por ejemplo el comando DIR.

2. Utilización de los cmdlets estándares

El cmdlet, llamado ”Command-let”, es un comando batch especializado en la ejecución de una funcionalidad única para el contexto de la interfaz de comando activa. La ejecución de un cmdlet no crea de nuevo procesos en el sistema anfitrión.

El cmdlet get-command permite retornar la lista de los cmdlets. No podrá recordar todos los cmdlets disponibles para el entorno de ejecución PowerShell, ya que son demasiados. Por el contrario, debe poder encontrarlos y determinar la sintaxis principal. Los principales cmdlets que debe conocer son los siguientes:

	- get-command: este comando lista el conjunto de cmdlets disponibles en el entorno de ejecución de PowerShell. El comando get-command -noun process permite listar los cmdlets relativos a la gestión de procesos.

	- get-help: este comando permite obtener información detallada sobre la utilización de cmdlets, como el nombre y la descripción de la sintaxis del cmdlet. El comando get-help ls permite listar la información detallada del cmdlet que hace referencia al alias ”ls”.

	- get-member: este comando permite obtener información sobre los objetos y listas de objetos de los cmdlets. 

La lista de comandos siguientes permite listar los objetos adjuntos a un objeto del sistema operativo, como el directorio Windows, y visualizar el contenido de un objeto de tipo propiedad.
Observe que se puede acceder al histórico de comandos con la tecla [F7] y con el comando ```history```

3. Ejemplos de comandos para solucionar problemas con PowerShell

	* Si aprende los muchos comandos PowerShell, ganará mucho tiempo en las tareas de mantenimiento habituales que a menudo suelen ser repetitivas.


	* Por ejemplo, puede visualizar los errores del diario de eventos Application con el siguiente comando:


```
Get-EventLog -LogName "application" -Newest 20 -EntryType error | 
fl EntryType,Category,CategoryNumber,Source,Message

```

También puede volver a desplegar las aplicaciones descargadas desde Windows Store con el siguiente comando:

```
Get-AppXPackage -AllUsers | Foreach {Add-AppxPackage  
-DisableDevelopmentMode -Register  
"$($_.InstallLocation)\AppXManifest.xml"}

```

Este comando es útil si una o varias aplicaciones descargadas desde la tienda Windows Store tienen problemas de funcionamiento o de arranque en su entorno.


Otro comando interesante es el comando repair-volume, que equivale al comando chkdsk.
Por ejemplo, puede ejecutar el siguiente comando para escanear el disco c:\

```
Repair-Volume c -Scan
```

Observe que Windows 10 integra nuevos comandos PowerShell para la gestión de paquetes de aplicaciones o, por ejemplo, para administrar Windows Defender.

En la web TechNet de Microsoft puede encontrar los cientos de comandos PowerShell para la gestión y la administración de los sistemas Windows. Puede acceder a esta lista en la siguiente dirección: https://technet.microsoft.com/en-us/library/mt156946.aspx
