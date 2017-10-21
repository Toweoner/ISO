1. Asumiendo los siguientes procesos:


| Proceso | Tll | Ts | Prioridad |
|---------|-----|----|-----|
|    A    | 0   | 8 |   1  |      
|    B    | 2   | 13  |  2   |      
|    C    | 4   | 3  |   3  |     
|    D    | 4   | 6  |   4  |     
|    E    | 6  | 8  |   5  |      
|    F    | 6  | 3  |   6  |      

* Desarrolle la representación gráfica de cómo el despachador les asignaría
el CPU, y la tabla de análisis, bajo:

* RR con q = 1
* RR con q = 3
* SJF (Proceso más corto a continuación)
* FCFS

Compare el rendimiento, uso del procesador, media de tiempo de retorno, respuesta, etc. bajo cada uno de estos esquemas. ¿Qué ventajas presenta cada uno?

2. Investigación:

* Haz una comparativa e investigación de los algoritmos de planificación utilizados en la actualidad en Linux, Windows, Unix y OSX.

* Debes explicar qué tipos de algoritmos se utilizan para cada uno de estos sistemas y explicarlos.

* Haz un estudio de cuál es la forma de configurar las planificaciones de CPU para Windows y Linux.

## Referencias:
* <https://en.wikipedia.org/wiki/Scheduling_(computing)#Windows>

* <http://recoverymonkey.org/2007/08/17/processor-scheduling-and-quanta-in-windows-and-a-bit-about-unixlinux/>
* <https://www.microsoft.com/mspress/books/sampchap/4354c.aspx>
* <https://technet.microsoft.com/library/Cc976120>
*

### Anotaciones sobe este laboratorio

#####  En primer lugar las prioridades resultan ser una forma más de controlar la planificación de la cpu. Lo que quiero es que veáis el funcionamiento de las prioridades sobre ciertos algoritmos. Aunque voy a pasar a aclarar la forma de trabajar en esta práctica.

*  En ```Round Robin (RR) con prioridades``` existen dos estrategias que vamos a tratar. Existen muchas, pero trataremos las siguientes para el RR:

* La primera es cuando acaba el proceso su quantum, dicho proceso no se cuenta para evaluar con el resto en cuanto a su prioridad, pero al siguiente instante ya puede ser evaluado según su prioridad. Si por ejemplo tenemos el siguiente momento del algoritmo de planificación con RR, q = 1. El proceso A llegó en el instante 0, el B y el C en el 2. La prioridad de el A es 1 (mayor), la del B es 2 y la del C es 3.

| Ejecución | A | A | B | A |
|-----------|---|---|---|---|
|           | 0 | 1 | 2 | 3 |
| COLA      | A | A | B | A |
|           |   |   | C |C   |
|           |   |   |   | B |



En el instante 2, A finaliza su quantum y B inicializa su ejecución. Como A tiene mayor prioridad debería continuar otra vez, pero el RR, cuando acabas tu quantum, esperas al siguiente para ser elegible.  En el instante 3 se vuelve a meter el A en ejecución al tener mayor prioridad.

* La segunda forma de RR con prioridades es evaluar la cola con prioridades aunque el proceso haya finalizado su quantum. Siempre entrará el que mayor prioridad tenga. Así, en el ejemplo de arriba en el instante 2, entrará el A otra vez al tener mayor prioridad.

* En cuanto al ```SJF y FCFS``` las prioridades se tratan a nivel de cola en caso de empate. Es decir, siempre el algoritmo manda o prevalece sobre la prioridad. Pero en caso de empate en la cola, se utilizan prioridades.


#### Dicho esto lo que quiero que hagáis en la práctica es utilizar el RR con prioridades poniendo algún ejemplo de cada versión para que veáis cómo funciona. El resto de algoritmos son más sencillos. También podéis analizar cómo pueden funcionar cambiando las prioridades. Lo que se pide es que analicéis los algoritmos y veáis cómo funcionan ante prioridades y utilización de estrategias diferentes.

Realmente la segunda parte de la práctica es analizar unos links que yo os he dado. Pero me parece más importante que realicéis primero la parte de analítica de algoritmos. Y luego hagáis el resto de la práctica.
