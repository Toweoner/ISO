# Lab 1.2
## Visualización de estados de los hilos
* En este lab vamos a realizar una práctica con el monitor de recursos de MS Windows.

* Los hilos en Windows tienen las transiciones y estados que se adjuntan como figura.

* En este lab vamos a visualizar algunos estados de hilos mediante la herramienta de monitorización de rendimiento de Windows.

### Realizamos la siguiente práctica guiada para ver los estados de un hilo

* Observa y analiza el diagrama de estados que se adjunta como imagen en la carpeta de Labs llamado *estados.png*. Haz lo mismo con el de *transiciones.png". 

---

* Ejecutamos el monitor de rendimiento en el cuadro de Búsqueda.
* Selecciona la vista Gráfico mediante Clic derecho + Propiedades.
* Selecciona como máxima escala 7. (Esto tiene que ver con la selección de estados de un hilo en Windows).
* Si observas abajo está el % tiempo de procesador y una casilla de verificación para mostrar o no las gráficas. Puedes deseleccionarla para que no interferir en el resto.
* Agregamos un contador y elegimos *Subproceso+Estado de Subproceso* (en inglés Thread/ThreadState).
* Selecciona *Mostrar descripción".* Fíjate que así sabemos qué es cada item.
* Selecciona *Estado de subproceso (ThreadState)*.
* En *Todas las instancias* buscas el *notepad/0* y lo agregas.
* Identifica el estado en que aparece. ¿Señaña a qué estado corresponde y su identificación?
* Ahora escribe algunas palabras en el notepad. ¿Qué ocurrió?
* Cierra el notepad. ¿Qué paso?
* Prueba con otro proceso que quieras y realiza lo mismo.



### Entregables:

* Informe con capturas y explicaciones.