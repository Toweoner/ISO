# Ejercicios de Labs

## Los siguientes ejercicios se realizarán en clase.

* Se utilizará un VM de Windows 10 Enterprise
* Es necesaria una ISO de la W10 Ent y una iso de debian.
* Dichos ejercicios se realizarán en clase
* Al final se hará un lab de repaso general si hay tiempo.


### Ejercicio 1. Activar la característica Hyper-V

Client Hyper-V  permite ejecutar máquinas virtuales con Windows 10. Hay varias razones para querer hacer esto, que incluyen:

* Client Hyper-V  permite ejecutar máquinas virtuales en su computadora con Windows 10. Hay varias razones para querer hacer esto, que incluyen:

  - Querer ejecutar múltiples sistemas operativos en una sola computadora. computadora.

  - Admite aplicaciones antiguas que no funcionan correctamente cuando se ejecutan de forma nativa en Windows 10. cuando se ejecutan de forma nativa en Windows 10.

  - Creando un ambiente de prueba o entrenamiento que no afectará su máquina de producción. máquina de producción.

  - Básicamente es como un VMWare Workstation o un Oracle VM, pero en su versión Microsoft.

### Instalación del rol de Client Hyper-V

* Abra el Panel de control, haga clic en Programas y características, y luego haga clic en Activar o desactivar las características de Windows.

* Seleccione la casilla de verificación de Hyper-V y haga clic en Aceptar. Los archivos se copian Debe reiniciar su computadora antes de poder administrar la máquina virtual.
* También puede usar el siguiente cmdlet de Windows PowerShell para instalar la función Hyper-V:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```
* Ahora se está preparado para configurar MVs


### Ejercicio 2. Instalar una iso en VHD de Hyper-V y en VMWARE.

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

6. Ubique el disco VHD que ha creado y escriba select vdisk file = D: \ VHD \ Windows10vhd.vhd . (Tenga en cuenta que la letra de la unidad ha sido modificada).

7. En DiskPart, escriba attach vdisk y presione Enter.

8. Escriba Salir para cerrar DiskPart y luego cierre la ventana del símbolo del sistema administrativo.

9. En la página Dónde desea instalar Windows, haga clic en Actualizar.

Su disco VHD debería aparecer ahora.

10. Seleccione la unidad VHD y permita que Windows se instale normalmente.

Después de reiniciar la máquina, debería ver la posibilidad de elegir un sistema operativo durante el tiempo de arranque, como se muestra

### Ejercicio 3. Modifcar arranque con BCDEDIT

<https://www.computerhope.com/bcdedit.htm>
### Ejercicio 4. Preparar un USB con diskpart para instalación.

### Ejercicio 5. Gestión discos:
* Configure disks, volumes, and file systems
* Create and configure virtual hard disks
* Create and configure Storage Spaces
* Configure removable devices


* Creating a VHD
The example below creates a 20GB dynamically expanding VHD called "test.vhd" and places it in the root of the C: drive.  Note that the type parameter is optional and the default type is fixed.

```
create vdisk file=c:\test.vhd maximum=20000 type=expandable
```

* Attaching a VHD
The following example shows how to select and attach the VHD.  It also provides steps for partitioning, formatting and assigning a drive letter to the attached VHD.

```
select vdisk file=c:\test.vhd
attach vdisk
create partition primary
format fs=ntfs label="Test VHD" quick
assign letter=v
```

* Detaching the VHD
To detach (i.e. unmount) the VHD, use the following example:

```
select vdisk file=c:\test.vhd
detach vdisk
```

Note: All 3 of these VHD actions can also be performed in the Disk Management Console of Windows 7.

In addition, below are some other DiskPart commands that can be used to manage VHDs:

```
create vdisk file=c:\testdiff.vhd parent=c:\test.vhd
```

– This will create a differencing "child" VHD (testdiff.vhd) so that the existing parent VHD (test.vhd) is not modified.  Useful when you have an image on the parent VHD that you don’t want modified.  When needing to go back to the default image, only the differencing VHD would need to be replaced.  The differencing VHD typically starts out very small – usually less than a megabyte.  

As a result, it is easy to back up and replace.

```
expand vdisk maximum=<size in mb>
```

– This expands the maximum size on a VHD.  For this to work, the virtual disk must already be selected, detached and be a non-differencing VHD.  In addition, if you do have a differencing VHD and expand the parent VHD, you will need to create a new differencing VHD.  Otherwise you will encounter a VHD corruption error when trying to select/manage the differencing VHD.

```
merge vdisk depth=1
```

– Merges a child VHD with its parent.  This command can be used to merge one or more differencing ("child") VHDs with its corresponding parent VHD.

```
compact vdisk
```

– Compacts a selected VHD to reduce the physical size.  Can only be used on VHDs that are type expandable and are either detached, or attached as read only.
