# Lab11 - Unidad 1

### Se realizará lo siguiente:

* Los hilos y procesos se administran de manera muy parecida en **Windows** y **Linux**.

* En este Taller de Laboratorio ( o Lab, más brevemente) vamos a ver algunos detalles de los procesos e hilos tanto en Windows como en Linux, viendo determinadas herramientas que se necesitan utilizar para averiguar los estados del proceso/hilo o información referida al **PCB (Process Control Block)**. 
* La práctica de este Lab va a consistir en probar los comandos y opciones en dos equipos preparados en Máquinas Virtuales (Windows y Linux). 

* Se ejecutarán los comandos y se realizarán capturas o copia de las salidas realizadas y se pondrán en un documento comentando qué se ha realizado.

### En Linux/Debian

* Los procesos en ejecución se pueden averiguar mediante el comando ```ps``` entre otras utiidades. Vamos a ejecutar la MV y escribir los siguientes comandos. 

```

	ps 
	ps -ef
    ps -ef | more

```

Como has podido observar, se imprimen los procesos mediante unas columnas. Cada proceso tiene un identificador llamado PID. Anota el PID del proceso que quieras.

El directorio ```/proc``` es un directorio especial que está relacionado directamente con el PCB. Linux guarda en un ```task struct``` (una estructura de datos) la información del PCB. El PID (Process IDentification) es el *número identificativo unívoco* del proceso. Debajo del directorio ```/proc``` están las carpetas con los procesos organizados mediante su PID.

+ Ahora haz lo siguiente:

```

 	ls /proc/PID

    cd /proc/PID

    cat status | more
    cat sched

```

Para averiguar datos sobre el **estado del proceso** suele venir en los ficheros (```status```, ```sched```, ```stat```, ```schedstat```).

1. Siendo PID el número del proceso que has elegido. Averigua en qué estado está el proceso y cuántos hilos tiene asignados.
2.  ¿Puedes ver los tiempos de planificación del mismo?

### En Windows/10//8/7

* En este caso utilizaremos también ps, ya que nos vale también en Windows. Aunque realmente también lo haremos mediante la consola PowerShell con el comando ```Get-Process```.

* Ejecutamos la consola Powershell en Buscar programas escribimos ```Powershell``` y ejecutamos la consola. Existe la Consola ISE y la x86, pero utilizaremos la que sólo dice *Windows Powershell*.

```

	# Para saber los procesos
	ps  
	Get-Process

	# Puedes capturar el estado del proceso winlogon y ver el resultado de los threads.

    $p= Get-Process -name winlogon
    $p.threads
    
	#También puedes ver los Threads de esta forma, por pid.

	$process=[System.Diagnostics.Process]::GetProcessById(<PID>) 
	$threads=$process.Threads
	$threads | select Id,ThreadState,WaitReason
```

1. Elige un proceso y averigua cuántos hilos tiene, su prioridad actual, su ID y su estado.
2. Elige el proceso chrome, ¿qué ocurre?


## Entregables
*  Entregar un informe con capturas de código y/o imágenes comentando lo que se ha realizado. 