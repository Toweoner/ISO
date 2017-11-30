Ejercicios de Repaso de UT2
===========================

 

Discos virtuales
----------------

1.  Crear un disco virtual en diskpart de 4GB

2.  Expándelo a 7 GB

3.  Redúcelo a 1GB

4.  Compáctalo

 

\* Escribe todos los comandos realizados en un fichero de texto

 

Crea una instalación de Windows en un disco virtual
---------------------------------------------------

-   Crea un disco virtual de 20GB e instala el Windows

-   Modifica el arranque para que el boot manager tenga “WinBase” y “WinNueva”,
    siendo este último label la Windows instalada recientemente.

-   Cambia el orden

-   Exporta un backup del bootmanager a
    c:\\windows\\usuario\\Desktop\\copiabcd.txt

 

Crea en un dispositivo externo una unidad de arranque por usb de Windows 10
---------------------------------------------------------------------------

 

-   Escribe los comando realizados y el usb realizado.

 

Volúmenes con Diskpart
----------------------

-   Crea un disco físico en tu MV de 11 GB

-   Conviertélo a mbr

-   Conviételo a gpt

-   Hazlo dinámico

-   Crea un volumen dinámico de 5GB

-   Bórralo, y crea otra de 3GB

-   Crea otro volumen con el resto de espacio

-   Formatea un volumen en fat32 y otro en ntfs

-   Convierte el de fat32 a ntfs

 

Gestión de discos con Powershell
--------------------------------

-   Cuáles son los discos físicos de tu sistema

-   Añade tres discos de 11 GB, averigua los discos que tienes disponibles.

-   Formatea ambos discos: uno en ntfs y otro en refs

-   Cámbiales los labels a “disco1” y “disco2”.

-   Formatea el que tiene refs a ntfs.

-   Visualiza las particiones, volúmenes y discos

-   Limpia el disco

 

Creación de espacios de almacenamiento
--------------------------------------

-   Añada 6 discos de 11 GB a tu MV

-   Crea un espacio de almacentamiento llamado “STO1”

-   Crea un disco virtual llamado “v1” realizando un espacio simple

-   Crea otro espacion de almacenamiento llamado “STO2”

-   Crea un disco virutal llamado “v2” realizando un mirror doble.

-   Borra ambos espacios.

-   Crea otro espacio “STO3” y lo pones en paridad

-   Borra dicho espacio y crea otro “STO4” y lo pones como mirror triple.

 
