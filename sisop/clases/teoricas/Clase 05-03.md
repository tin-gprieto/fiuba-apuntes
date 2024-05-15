
Conceptos claves
 - Estructuras del SO para soportar threads
 - Estados
 - Implementation en Linux
 - Copy on Write

**Tasks**: entidad scheduleable 

(buscar task struct)

**TCB** (_Task Control Block_)

## Thread Groups

CLONE_THREAD -> clone(CLONE_THREAD) 

![[sisop-thread-group.png]]

En linux, el thread group es la forma de realizar un proceso.

## IPC: Interprocess communication

Conceptos claves:
- Tipos de IPC
- Shared memory

### IPC facilities

![[sisiop-ipc.png]]


**Crear memoria compartida**

`void* create_shared_memory(size_t size)`

(similar a pipes)

## Sincronizacion 

Gran problema: Entrelazamiento de varias cosas pasando al mismo tiempo

Conceptos clave:

- **Race condition** (condición de carrera):

Dos threads intentan acceder a la misma memoria, y el resultado depende de quien llega primero.

![[sisop-race-condition.png]]

- **Sección critica**: abstracción de código que debe ejecutarse con exclusion mutua (ejecutando en un solo thread - no debe ser accedido por mas de un thread )

## Locks

Tipo de dato abstracto/variable que permite sincronizar con **exclusion mutua**.

		Obterner(lock)
		...
		Codigo a ejecutar - Seccion critica
		...
		dejar(lock)

**Lock contention**: 

Los thread esperan a que un thread ejecute la seccion critica antes de pasar al siguiente. Si tenemos muchos locks en el codigo, gran parte de los hilos van a estar esperando.

### API

`pthread_mutex_t lock:
`int pthread_mutex_init(&lock,NULL)`
`int pthread_mutex_lock(lock)
`int pthread_mutex_unlock(lock)`

### Propiedades formales

- **Exclusion mutua**: como mucho un solo thread posee el lock a la vez.
- **Progress**: Si nadie posee el lock y alguien lo quiere, alguno debe poder obtenerlo
- **Bounded waiting**: Si hay varios procesos esperando el lock, eventualmente todos deberían acceder a el (Solución: FIFO)

### Spin-lock

Implementation de lock usando **"busy wait"**

**busy wait**: el proceso o hilo de ejecución espera activamente en un loop (while) a que ocurra un evento en lugar de dormirse o bloquearse.

Cuando se debe utilizar:

- Se utiliza cuando el tiempo del lock es corto !! (ms)

- Ideal cuando hay poca contention por el lock (pocos procesos tratando de obtenerlo)

- Cuando hay paralelismo real, es decir, varios procesadores o núcleos.

Implementacion:

![[sisop-spinlock.png]]

**Operaciones atómicas**: Se ejecutan de manera completa, no permite que se ejecute algo en el medio (no hay race condition error)

`type __sync_lock_test_and_set(type *ptr, type value, ...)`

`void __sync_locj_release(type *ptr)` -> Garantiza que escribir un cero es atómico

### Sleep lock

A partir del spin lock, duerme a todos los procesos (...)

![[sisop-sleeplock.png]]

Cuando se utiliza?
- Cuando hay una espera larga y no queremos bloquear
- Cuando hay un solo procesador


**Deadlock**





