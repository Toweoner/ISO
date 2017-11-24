
# Ejercicios de Labs

* Los siguientes ejercicios se realizarán en clase. A modo de guión se pondrán aquí todos los procesos para que los alumnos puedan consultar los conocimientos de forma más sencilla.
* En los pdfs en **Contenidos** se muestran varias capitulos que, a modo de extensión, podéis consultarlos porque es un libro bastante interesante y el que se usa para la **certificación MCSA**.
* Se utilizará un VM de Windows 10 Enterprise como base.
* Es necesaria una ISO de la W10 Ent y una iso de debian.
* Al final se hará un lab de repaso general si hay tiempo.
* Para el examen de la Unidad 2, será práctico y se partirá de una Windows 10 Enterprise limpia, a lo sumo con las VMware tools instaladas.
* En el examen se pedirá una serie de comandos y acciones basados en los siguientes ejercicios.
* Se entregará una parte de papel y otra digital con capturas.
* No habrá conexión a internet.
* La ayuda del sistema será el único material, además de la propia MV.



### Ejercicio 1. Activar la característica Hyper-V

Client Hyper-V  permite ejecutar máquinas virtuales con Windows 10. Hay varias razones para querer hacer esto, que incluyen:

* Client Hyper-V  permite ejecutar máquinas virtuales en su computadora con Windows 10. Hay varias razones para querer hacer esto, que incluyen:

  - Querer ejecutar múltiples sistemas operativos en una sola computadora. computadora.

  - Admite aplicaciones antiguas que no funcionan correctamente cuando se ejecutan de forma nativa en Windows 10. cuando se ejecutan de forma nativa en Windows 10.

  - Creando un ambiente de prueba o entrenamiento que no afectará su máquina de producción. máquina de producción.

  - Básicamente es como un VMWare Workstation o un Oracle VM, pero en su versión Microsoft.

 **Instalación del rol de Client Hyper-V**

* Abra el Panel de control, haga clic en Programas y características, y luego haga clic en Activar o desactivar las características de Windows.

* Seleccione la casilla de verificación de Hyper-V y haga clic en Aceptar. Los archivos se copian Debe reiniciar su computadora antes de poder administrar la máquina virtual.

* También puede usar el siguiente cmdlet de Windows PowerShell para instalar la función Hyper-V:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```
* Ahora se está preparado para configurar MVs


### Ejercicio 2. Instalar una iso en VHD en VMWARE.

* Crear y configurar un VHD de arranque nativo
* Crear y configurar un VHD de arranque nativo
Los pasos necesarios para preparar un VHD deben realizarse con cuidado; de lo contrario, el VHD no estará presente durante el proceso de instalación. Para preparar un VHD de inicio nativo, primero créelo y configúrelo para que Windows se instale en él.

Realice los siguientes pasos.

1. Escriba diskmgmt.msc en el área de búsqueda o haga clic con el botón derecho en el botón Inicio y haga clic en Administración de discos.

2. En Administración de discos, haga clic en Acción y luego haga clic en Crear VHD.

3. En el cuadro de diálogo Crear y adjuntar disco duro virtual, proporcione los parámetros para su VHD.

Un ejemplo de VHD es:

Imagen Ubicación C: \ VHD \ Windows10vhd.vhd.

Imagen Tamaño del disco duro virtual: 40 GB.

Imagen Formato del disco duro virtual: VHD.

Imagen Tipo de disco duro virtual: tamaño fijo.

4. Haga clic en Aceptar para crear su VHD.

Debido a que se seleccionó el tipo fijo, esto podría tomar varios minutos para completarse, y verá el progreso de la creación en la esquina inferior derecha del cuadro de diálogo Administración de discos. Su nuevo VHD debe conectarse automáticamente al sistema. Si no es así, puede usar Administración de discos para adjuntarlo.

Use Disk Management para conectar un VHD
Su nuevo VHD se debe conectar automáticamente al sistema, de lo contrario, use Administración de discos para conectar el disco de la siguiente manera.

1. Haga clic en Acción y luego en Adjuntar VHD, busque su nuevo VHD y elija el VHD que desee adjuntar.

2. Si prefiere usar la línea de comando, también puede usar la herramienta DiskPart y escribir create vdisk file = C: \ VHD \ Windows10vhd.vhd maximum = 40960 type = fixed para lograr el mismo resultado.

3. Deje la unidad VHD en el estado No inicializado; esto se actualiza cuando Windows se instala en él.

Windows ahora puede instalar en el archivo VHD.

Instalar Windows dentro de un VHD
Para instalar Windows dentro de su archivo VHD, siga estos pasos.

1. Inserte su medio de Windows (o ISO si está usando una máquina virtual) en su computadora y arranque desde allí.

2. Siga las indicaciones en pantalla, proporcionando la información adecuada hasta que aparezca la pantalla Dónde desea instalar Windows.

3. Presione Shift + F10 para abrir una ventana de símbolo del sistema administrativo.

4. En la ventana del símbolo del sistema administrativo, escriba DiskPart .

5. En DiskPart, escriba List disk .

6. Ubique el disco VHD que ha creado y escriba

**Resumiendo comandos:**

* Creación de un disco virtual VHD/VHDX: el siguiente ejemplo crea de forma dinámica un disco expandible de tipo VHD en un fichero llamado ```test.vhd```. El tipo puede ser ```expandible``` y ```fixed```. El primero se puede modificar y el segundo no y además es el valor por defecto.


```
create vdisk file=c:\test.vhd maximum=20000 type=expandable
```

* Montaje de VHD/VHDX (attach): el siguiente ejemplo muestra cómo seleccionar y montar el VHD. También se ven los pasos del particionamiento, formato y asiganción de letra de la unidad al disco montado.


```
select vdisk file=c:\test.vhd
attach vdisk
create partition primary
format fs=ntfs label="Test VHD" quick
assign letter=v
```

* Desmontaje de disco VHD


```
select vdisk file=c:\test.vhd
detach vdisk
```
**Estos pasos se pueden realizar en el Administrador de Discos de la MMC**

**También es necesario realizarlo mediante el comando diskpart en el CMD de Windows***

```
c:\DiskPart
diskpart>
```


- Este comando expande o extiende el tamaño del disco duro virtual VHD. Para que esto funcione el disco debe estar seleccionado, desmontado (detach) y no direfenciado (que no tenga un backup hijo, que no hemos visto). De otro modo, encontrarás errores de corrupción de datos en VHD. mientras lo intentes crear.
```
expand vdisk maximum=<size in mb>
```


- Compacta un disco VHD seleccionado para reducir el tamaño. Sólo puede ser utilizado con VHDs que son *expandable* y también desmontados, o montados en modo lectura.

```
compact vdisk
```

* Después de poder crearlo debe reiniciar el sistema de modo que la BIOS/UEFI pueda reconocer una ISO de Windows 10 Enterprise desde un dispositivo extraíble. 
* Desde la VMWARE, se para la máquina (Power Off) y se arranca desde la BIOS: Power On Firmware.
* Se seleccion las opciones de arranque el dispositivo extraíble donde esté la ISO y se inicia la MV.
* Después, en el arranque de instalación de Windows 10, se procede a la instalación y se pasa a la fase donde están los discos para instalar. Se pulsa ```Shift+F10```  t aparcerá la consola de comandos. 
* Pasa a la unidad donde estén los discos virtuales y entre en la aplicación ```Diskpart```.

```

select vdisk file = D:\VHD\Windows10vhd.vhd .
```

(Tenga en cuenta que la letra de la unidad ha sido modificada).

7. En DiskPart, escriba attach vdisk y presione Enter.

8. Escriba Salir para cerrar DiskPart y luego cierre la ventana del símbolo del sistema administrativo.

9. En la página Dónde desea instalar Windows, haga clic en Actualizar.

Su disco VHD debería aparecer ahora.

10. Seleccione la unidad VHD y permita que Windows se instale normalmente.

Después de reiniciar la máquina, debería ver la posibilidad de elegir un sistema operativo durante el tiempo de arranque, como se muestra


### Ejercicio 3. Modifcar arranque con BCDEDIT


* El comando **BCDEDIT** tiene como función modificar el arranque de sistemas Windows. 
* Se necesita iniciar el CMD con privilegios de Administrador.

- Para visualizar la ayuda del comando:

```
bcdedit /?
```

- Para visualizar todas las entradas del boot manager:

```
bcdedit /v
```

- Para ver la ayuda de la opción */createstore*:


```
bcdedit /? /createstore
```

- El siguiente comando crea un orden que consiste en dos Windows, identificado por GUID y por la etiqueta ntldr, que la utilizan sistemas operativos Windows más antiguos que Vista
:

```
bcdedit /displayorder {802d5e32-0784-11da-bd33-000476eba25f} {cbd971bf-b7b8-4885-951a-fa03044f5d71} {ntldr}
```


- El siguiente comando pasa el GUID que tenga la instalación del Windows al último lugar. También puede ser al primer lugar.


```
bcdedit /displayorder {802d5e32-0784-11da-bd33-000476eba25f} /addlast

bcdedit /displayorder {802d5e32-0784-11da-bd33-000476eba25f} /addfirst
```

- Si se necesita cambiar la descripción que se va a imprimir en el boot manager al iniciar Windows:

```
bcdedit /set {802d5e32-0784-11da-bd33-000476eba25f} description "Windows 10 Lab1"
```

- Si queremos poner un tiempo en el que permanecerá disponible las opciones del boot manager (en segundos):


```
bcdedit /timeout 30
```

- Si queremos poner por defecto que arranque un determinado sistema:

```
bcdedit /default {cbd971bf-b7b8-4885-951a-fa03044f5d71}
```

* **BCDEDIT** no es un boot manager para sistemas Linux y, en principio, no es compatible, pero sí que se puede utilizar haciendo un simple workarround que añade un arranque UEFI desde una partición que se pueda acceder a la imagen de Linux. Aunque es recomendable utilizar **Grub2** cuando ya se tienen sistemas Windows y Linux coexistiendo. Esto se verá en la parte de Linux, segundo trimestre.

### Ejercicio 4. Preparar un USB con diskpart para instalación.

- Reemplaza x por la unidad de la unidad Flash USB:

```select disk x ```

```clean # Esto elimina o limpia el contenido de la unidad Flash```

```
create partition primary  # Creamos una partición

list partition 			  # Listamos la partición

select partition 1  	  # Seleccionamos la partición 1

ative 					  # Marcamos la actual partición como activa

format gs=ntfs quick 	  # Formateamos la partición

assign letter=H           # Asignamos la letra H, si sólo escribimos assign el sistema asigna una libre.

exit
```

Luego entramos en la unidad g:

```
g:
cd boot
bootsect /nt60 h:   # donde h: es la unidad del pendrive

```

- Copiamos los ficheros:

```
g:\xcopy g:\*.* /s /h /f h:\
```


- Una vez hecho esto, ya tenemos cualquier sistema Windows arrancable desde Flash USB.

- Existe otra opción, que es utilizar **Rufus**, una aplicación que vale para casi cualquier sistema operativo. Pero es gráfica.
### Ejercicio 5. Gestión discos:

#### Particiones MBR y GPT

* MBR (Master Boot Record): creado durante el particionado del disco y ubicado en su primer sector, su emplazamiento
soporta cuatro particiones principales, pero el ordenador solo arrancará desde aquella definida como activa (partición
del sistema) y contendrá el gestor de arranque. Es posible definir más de cuatro particiones, designando una (o más)
de las particiones principales como extendidas y atribuirle así particiones lógicas para almacenar los datos. La BIOS
del ordenador requiere cierta tecnología para arrancar Windows 10. En caso de que la tabla MBR se corrompa, el
sistema no podrá arrancar. **El tamaño máximo de las particiones MBR es de 2 TB.**

* GPT (GUID Partition Table): disponible en los ordenadores UEFI, la tabla de particiones GPT resuelve las restricciones
vinculadas a los discos MBR. A diferencia de la estructura anterior, que contiene las referencias LBA (Logical Block
Address) codificadas en 32 bits, una partición GPT tiene sus referencias definidas en 64 bits. Además, una partición del
sistema ESP (Extensible Firmware Interface System Partition) se almacena en cada disco arrancable, al igual que una
partición MSR (Microsoft Reserved Partition). La tecnología GPT está disponible con Windows Vista, Windows 7,
Windows Server 2008, Windows Server 2012, Windows 8.1 y Windows 10.

Una BIOS en un sistema de 32 o 64 bits se encarga de la lectura de datos de una partición GPT. En una arquitectura
de 64 bits con un sistema UEFI, es posible utilizar una partición GPT para arrancar Windows 10.

Un disco GPT gestiona hasta 128 particiones principales y ofrece una redundancia para un tamaño de volumen
máximo de 18 EB (exabytes).

Durante la instalación de Windows 10 en un disco de arranque GPT, este último crea tres particiones:

  - ESP: con un tamaño variable, esta partición contiene el gestor de arranque necesario para ejecutar Windows 10. arranque necesario para ejecutar Windows 10.
  - Sistema operativo
  - MSR: partición oculta que no posee ninguna letra de unidad, reservada para el funcionamiento de Windows 10. No
debe estar encriptada.

Tres herramientas permiten administrar las particiones utilizadas por Windows 10: Consola de administración de
discos, PowerShell y DiskPart.

Por ejemplo, es posible convertir de forma sencilla una partición MBR en una partición GPT y viceversa, empleando la
herramienta DiskPart.


# Ejercicio 5. Creación de Volúmenes:

**NOTA Importante**: Añadir discos a la VMWARE es sencillo. Pero actualmente sí que nos funciona hacerlo con la instancia encendida (no como lo dije en clase, parando la máquina). Eso nos permite realizar operaciones con discos de forma rápida y sencilla. 

- Botón derecho sobre la instancia y seleccionar *Settings*
- Añadir Hard Disk + SATA ó SCSI + Create new virtual disk + Tamaño elegido. El resto de opciones por defecto y finalizar.

* Visto esto vamos a crear volúmenes. 

## Referencias y Enlaces

* Desactivar el Windows Update: <https://4sysops.com/archives/disable-windows-10-update-in-the-registry-and-with-powershell/>
