# Lab11 - Unidad 1

### Se realizará lo siguiente:

* Los hilos y procesos se administran de manera muy parecida en **Windows** y **Linux**.

* En este Taller de Laboratorio ( o Lab, más brevemente) vamos a ver algunos detalles de los procesos e hilos tanto en Windows como en Linux, viendo determinadas herramientas que se necesitan utilizar para averiguar los estados del proceso/hilo o información referica al **PCB (Process Control Block)**. 
* La práctica de este Lab va a consistir en probar los comandos y opciones en dos equipos preparados en Máquinas Virtuales (Windows y Linux). 

* Se ejecutarán los comandos y se realizarán capturas o copia de las salidas realizadas y se pondrán en un documento comentando qué se ha realizado.

### En Linux/Debian

* Abrir la MV y escribir los siguientes comandos. 

```

	ps 
	ps -ef
    ps -ef | more

```

Como has podido observar, se imprimen los procesos mediante unas columnas. Cada proceso tiene un identificador llamado PID. Anota el PID del proceso que quieras.

* Ahora haz lo siguiente:

```

 	ls /proc/PID

    cd /proc/PID

    cat status | more
    cat sched

```

Siendo PID el número del proceso que has elegido.

Averigua en qué estado está el proceso y cuántos hilos tiene asignados.

### En Windows/10/7

* En este caso utilizaremos también ps, ya que nos vale también en Windows.
* Ejecutamos la consola Powershell en Buscar programas escribimos ```Powershell``` y ejecutamos la consola. Existe la Consola ISE y la x86, pero utilizaremos la que sólo dice *Windows Powershell*.

```

	ps
	Get-Process
	$process=[System.Diagnostics.Process]::GetProcessById(<PID>)
	$threads=$process.Threads
	$threads | select Id,ThreadState,WaitReason
```
