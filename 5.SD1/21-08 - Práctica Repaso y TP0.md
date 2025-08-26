
Prácticas no obligatorias -> Quiz para quienes participan

# Repaso
## Docker


(insertar cheetsheet)

- docker ps -> Ve qué contenedores hay corriendo o existen en docker
	- -a
	- -aq
- docker run ( image) (( cmd )
- docker volume
	- Ver/crear volumenes de almacenamiento para containers
 
### Docker Compose 

Crear varios servicios que funcionen en simultaneo

## Modelos de Multiasking

![[Pasted image 20250826155617.png]]

### Multi-threading

Hilos de ejecución livianos corriendo un mismo programa que comparten un heap de memoria

- Sincronización:
	- Soporte del SO -> pthread-mutex, etc.
	- Soporte del runtime -> Hilos de Java, .Net, etc
	- Inter Process Communication (IPC)
- Característica:
	- Sencillo para compartir información
	- Alto acoplamiento entre componentes del sistema
	- Escasa escalabilidad -> 1 thread defectuoso afecta a todo el sistema 
### Multi-processing

Comparten el mismo código -> Code Segment (read-only)
No comparten memoria !

Sincronización -> IPC (Signals, Pipes, Queues, Shared Memory, Semáforos, Locks, Sockets)

Características:
	-  No es trivial compartir información entre procesos
	- Componentes separados y más simples
	- Más escalable y estable que multi-threading
	- Sin tolerancia a fallos de HW, SO, etc.
### Multi-computing

No hay recursos compartidos
Sincronización -> Envío de mensajes

Características:
	- Comunicación de red -> Limitaciones de ancho de banda, latencia, y pérdida de mensajes
	- Comunicación entre procesos: compleja y central al diseño del sistema
	- Alta escalabilidad y tolerancia a fallos

## Programas Concurrentes

Propiedades:

- Safety properties (Obligatoriamente verdadera)
	- Exclusión mutua
	- Ausencia de deadlocks
- Liveness (Eventualmente verdaderas)
	-  Ausencia de Starvation -> Que los hilos esten haciendo tareas
	- Fairness -> Que los hilos reciban el mismo tipo de tareas (balance de carga)

Como asegurar las propiedades:
### Basado en Algoritmos

- Busy-waiting
- Spin-lock -> While(flag)
- Algoritmos de espera (Dekker, Lamport, Peterson) 
### Basado en Abstracciones
- Operaciones atómicas (Actualizar variables sin utilizar métodos de sincronización)
	- Contadores de tipo POD (int, char, double, etc)
	- CAS (Compare and Swap) -> IMPORTANTE para actualizar contenedores de forma segura en ambientes de multi-threading
- Semáforos
	- Variable que permite el paso o no a una sección critica
	- Signal (P) / wati(V) : Incrementar/Decrementa el valor de S
	- Mutex (S = {0.1})
- Monitores -> Ideal en performance para Read/Write
	- Mecanismo que regula el acceso a variables compartidas mediante una cola de espera
- Variables condicionales (ejemplo práctico de un monitor)
	- Mutex para realizar la operación
	- wait 
	- notify / notify_all
- Barreras 
	- Contador para administrar una cantidad exacta de procesos
	- Esperan en la barrera hasta que lleguen todos
- Rendezvous
	- Pasar un mensaje de un proceso a otro -> Blocking Queue

### IPCs

Permiten la comunicación entre dos o más procesos y están provistos por el SO

![[Pasted image 20250826165906.png]]


- Signals !!! -> importante
- Shared Memory -> Mecanismo provisto por el SO (Linux)
- File locks -> Según sean read o writes
- Pipes/FIFOs
	- ![[Pasted image 20250826170306.png]]
	- mkfifo -> queda abierto a nivel de SO
- Message Queues
	- Escriben/reciben un bloque de memoria
	- Una vez se leen se retiran de la cola
	- Buffer size definido en la creación !!!


## comunicaciones

### Modelo TCP/IP

- Aplicación -> Aplicaciones de usuario 
- Transporte -> Comunicación punto a punto -> TCP/UDP
- Internet (Capa de red) -> Lógico de transmisión de datos sobre la red
	- Forwarding and Routing
- Network Access (Capa de enlace y física) -> Transferencia física confiable

## Modelo OSI

![[Pasted image 20250826172845.png]]

## Estructura de paquetes

- IP

![[Pasted image 20250826173003.png]]

- TCP/UDP

![[Pasted image 20250826173203.png]]

TCP -> Fiable y orientado a conexión
UDP -> best-effort sin garantías


### Sockets

### Primitivas

- socket (domain, type, protocol)
- bind (fd, addr, addrlen)
- listen (fd, backlog) -> TCP
- accept (fd, addr, addrlen) -> Acepta una conexion listen
- connect (fd, addr, addrlen) 
- send (fd, buf, buflen, flags) 
- receive (fd, buf, buflen, flags)
- close (fd)
### TCP
![[Pasted image 20250826173618.png]]

### UDP

![[Pasted image 20250826173821.png]]

### Async

![[Pasted image 20250826173845.png]]

Sincrónico --> Se bloquea esperando la respuesta
- Camino crítico -> Necesito la respuesta para avanzar
- Latencia baja y acotada, y el usuario espera respuesta 
- Necesitas consistencia inmediata y respuesta determinista 
- Queres simplicidad y el volumen es esperado 
- SLOs estrictos

Asincrónico --> Sigue en ejecución
- Importa la experiencia de usuario
- La tarea es lenta/variable o de alta latencia 
- La tarea no bloquea la completitud principal o puede diferirse 
- Queres desacoplar y proteger el sistema 
- Podes tolerar la consistencia eventual y diseñar con idempotencia y reintentos 

### Throughput -> Prueba de carga

Evaluar la congestión de red


# TP0

Parte 1 :  Docker

Parte 2 : Comunicaciones

Parte 3 : Concurrencia