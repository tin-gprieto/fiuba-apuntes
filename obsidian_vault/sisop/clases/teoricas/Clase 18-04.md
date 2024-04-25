## Memoria
### Malloc/Calloc

Asignar espacio en memoria dinamica (HEAP).

devuelve un puntero void*  -> direccion de memoria virtual 
punteros: p, bp

Implementacion desde user

 _*  Kernel: tiene acceso a la memoria fisica en ciertos momentos
_* CPU virtualizada y user: tiene solo acceso a la memoria virtual

### brk / sbrk

brk: se pasa una direccion de memoria (puntero) y la libera al final del heap (? repasar)

## Scheduling

Que hacer primero cuando hay multiples cosas para hacer

**time slice / time quatum** : tiempo que tiene un proceso para usar el procesador. Cuando se termina ese tiempo se tiene que elegir un nuevo proceso para ejecutar. Lo determina el Scheduler apenas llega la tarea.

### Utilizacion del CPU

Operaciones E/S son bloqueantes

Cuanto gasta un proceso ? -> Probabilidad de que N procesos esten haciendo operaciones E/S = P(N) -> Utilizacion: 1 - P(N)

Accesos a memoria -> Jerarquizacion 

### Planificador

"Referee del procesos" 
Forma parte del kernel -> se encuentra en todo contexto del kernel (ej. micro kernel)

### Politicas para procesadores monocore

*Workload* : carga de un proceso corriendo en memoria -> determinar para la politica

**Supuestos**:
	- Cada proceso se ejecuta la misma cantidad de tiempo
	- Todos los jobs (proceso) llegan al mismo tiempo para ser ejecutados
	- Una vez empieza un proceso se ejecuta hasta completarse
	- Todos los procesos usan solo CPU (no hya operaciones ES)
	-  (...)
	- !! Conocemos el costo de los procesos

**Turn around time** (Taround): Tiempo de ejecucion(T completion) - Tiempo de arribo (T arrival)

Minimizar turn around time -> mejor

#### Politicas

- **FIFO**  (_first in, first out_) -> cola
	- Es simple y es util segun las suposiciones
	- Que pasa si el primer proceso es exageradamente mas costoso (mayor Turn around time) que los demas? -> PROBLEMA -> Efecto convoy (agarrar un camion en la ruta)
- **SJF** (_shortest Job first_)
	- El mas chico se ejecuta antes -> prioridad por costo
	- Imporante: tienen que llegar todos al mismo tiempo para comparar correctamente los procesos
- **STCF** (_shortest time to completion_)
	- Frena la ejecucion cuando llega un nuevo proceso, si este tiene menor Taround, deja de ejecutar el anterior para ejecutarlo despues, y ponerse a ejecutar el mas corto

**Tiempo de respuesta** (otra metrica): T response = Tiempo cuando se ejecuta (T run) - Tiempo de arribo (T arrival)

- *Round Robin* : Tiempo definido para correr un proceso, una vez termina el tiempo hace un _context switch_ (- ctx swt) y ejecuta otro proceso. En la realidad, lo que hace es cambiar de modo (entre user a kernel y viceversa) -> No es un politica en si, sino que es parte de varias politicas

 ** time interrumpt -> buscar

- **MLFQ**(_Multi Level Feedback Queue_):
	- Intenta optimizar el Taround (sin saber a priori cuanto va a tardar)
	- Busca que la tarea mas corta se ejecute primero
	- Minimiza el tiempo de respuesta
	- **Comportamiento**:
		- Prioridades (colas Q1, Q2...QN) 1 tiene > prioridad que N
		- **Regla 1**: Se ejecuta el proceso que esta en mayor prioridad
		- **Regla 2**: Si ambos procesos tienen misma prioridad (ambos pertenecen a Qi), se hace _Round Robin_
		- **Regla 3**: Cuando una tarea entra en el sistema, se pone en la cola de mayor prioridad
		- **Regla 4a**: Si una tarea usa todo su time slice mientras se ejecuta, su prioridad se reduce una unidad (Qi -> Qi-1)
		- **Regla 4b**: Si una tarea renuncia al uso de CPU antes de un time slice completo, se queda en el mismo nivel de prioridad
		- **Regla 5**: Cada cierto tiempo se hace un  _boost_ -> se suben todos los procesos de prioridad. Si un proceso utiliza CPU lo considera iterativo y lo deja en prioridad alta
	-  Solucionar el problema de _gaming_ (ventajeo): cede la utilizacion de CPU antes de terminar su time slice.  -> Solucion: se agrega contabilidad(sabe cuanto se ejecuto un proceso en cierta prioridad)
		- **Regla 4**: Una vez un proceso utiliza todo su tiempo dado (se le asigna por el scheduler) baja de prioridad (REFORMULACION DE LA REGLA)
	- Feedback -> Va aprendiendo en base a los procesos que va ejecutando 

** Un buen planificador debe decidir rapidamente quien sigue -> algoritmo de decision tendiendo a O(1)

--------------------------------------------------------------



