**Virtualizadores**

- Memoria: VM
- CPU: Scheduler -> Particion temporal
- I/O: Filesystem 

	 Objetivo: simplificar el manejo de recursos por parte de los procesos para que crean que tienen completa disponibilidad de las computadoras.

## Concurrencia

**Procesos** : Se ejecutan aisaldamente entre si, pero, que pasa si necesitan comunicarse entre si?

Manejar paralelamente la ejecucion de varios procesos

### Threads

Hilos de trabajo: secuencia independiente de instrucciones ejecutandose en un solo proceso. Comparten memoria entre si

Abstraccion: la unidad minima de paralelizacion de procesos

Ejecucion en **mononucleo** :
-   importancia de la velocidad del clock (Hz)
-  Impedimento fisico: llego a un limite en poder reducir transistores y obtener mas velocidad sin tener estrangulamiento termico
Ejecucion en **multinucleo**:
-  Ejecucion en paralelo: cuantos mas cores y mas optimizados esten, va a ser mas veloz sin tener que aumentar el clock


Dificultades de la concurrencia:
- Integibilidad
- ...
- ...

Composicion del thread:
	-  Thread id
	-  Valores de registros
	- Stack propio
	- politica y prioridad de ejecucion
	- propio errno
	- Datos especificos del thread (...)

(insertar grafico de single-thread process y multi-thread process)

! Diferencia entre thread y fork -> No estan aislados entre si, comparten memoria

### Thread Scheduler

Cada thread corre en un procesador virtual dedicado y exclusivo con una velocidad variable

!! **Entrelazamiento** :

Posibles ejecuciones de :

`x = x + 1`
`y = y + x`
`z = x + 5y`

Los thread se relacionan entre si:
	- Multi threading cooperativo: no hay interrumpcion a menos que alguien se lo solicite
	- Multi threading  preemptivo: Mas usando en la actualidad. Un thread en estado running puede ser movido en cualquier momento 

### Creacion

C: bibliotecas externas con syscalls
Java / Rust: con la lib standard

// Crea un hilo para que empiece a ejecutarlo
`int pthread_create(pthread_t * thread, const pthread_attr_t* attr,void * start_routine (void *), void * arg);

thread: puntero al thread
attr:
start_routine: funcion por parametros -> `void* my_function(void* arg)`
arg: argumento para la funcion

// Espera a que se ejecute el thread para obtener el resultado
`int pthread_join(pthread_t thread, void** value_ptr)`

### Estructura

TCB: Threads Control Block -> informacion del thread (como la table del proceso)

Metadata del thread:
	Id
	Prioridad del scheduling
	Status (init, ready, running, waiting, finished)(insertar grafico)
	
Estado Per-thread

! saber cuanto se ejecuta cada thread dentro del proceso

### Diferencias  con los procesos

| Comparte               | Thread | Proceso |
| ---------------------- | ------ | ------- |
| Memoria                | si     | no      |
| File descriptors       | si     | no      |
| Contexto de filesystem | si     | no      |
| Manejo de senales      | si     | no      |

### Modelo en Linux

#### Creacion

- LinuxThreads
	`clone(CLONE_VM | CLONE_FS | CLONE_FILES | CLONE_SIGHAND, 0)
- fork()
	`clone(SIGCHLD, 0)`
- vfork() -> padre no ejecutable
	`clone(CLONE_VFORL | CLONE_VM | SIGCHLD, 0)`

*Dentro del kernel no hay distincion entre proceso y thread

COW (_Copy on Write_)

Como se comparte la memoria (heap) entre threads: 
Se duplican las tablas de memoria:
	Con fork: writable=0 (Flag para negar la escritura de una pagina) -> Lo unico que tiene que hacer

vfork() -> No hace COW porque no lo necesita

vfork() + exec() -> Mas optimo (si fuese fork() copiaria las tablas y el exec las borraria para reemplazarlas)

threads -> no copia toda la memoria -> lightweigth process

Thread Group