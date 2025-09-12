
TP0

- Como cerrar correctamente los hilos
- Utilizacion de load_bets() -> Generador de un iterador (leer de linea en linea) -> IMPORTANTE PARA NO CARGAR TODO EN MEMORIA -> Vulnerable
- Recoger los hilos que dejen de trabajar -> Liberar recursos (Garbage colection)
- No limitar la cantidad de hilo con un hilo por cliente -> No es tolerante a fallos 
- RAII (???) -> Liberar el recurso es como destruirlo


Librerias MOM ! -> Se pueden usar 

https://github.com/gcc-cdimatteo/Sistemas-Distribuidos-I-75.74/tree/Mainframe

# Request - Reply

![[Pasted image 20250909195232.png]]

- Mensaje con su respuesta 
- Es sincronico (bloqueante)
- Utilizado por el modelo CLIENTE-SERVIDOR 
- Mensajes estructurados: mssgID, rqstID, opID, args
- Que pasa con la perdida de mensajes !

# Producer-Consumer 

Producer: Emisor 
Consumer: Receptor

## ZeroMQ 

Sockets "con esteroides" para la comunicacion de tareas de un productor a un consumidor 


# Publisher-Subscriber

![[Pasted image 20250909195916.png]]

- Basada en Topicos (MQTT)
- Basada en Canales 
- Necesidad de un Broker que distribuya la informacion

![[Pasted image 20250909195952.png]]

# Pipelines 

! ES LO QUE HAY QUE HACER EN EL TP

- Los datos de entrada forman un flujo donde distintos _filters_ se conectan entre si para procesarlos de manera secuencia 
- Inspirado en patrondes de procesamiento de senales (Unix)
- Modelos de __procesamiento__
	- __Worker por Filter__ (uno por cada etapa del pipeline)
	- __Worker por Item__ (Se le asigna una unidad de procesamiento a cada item y el worker aplica cada filtro )
- Etapas secuenciales y paralelas
	- __Paralela__: Cada item a procesar es independiente de los anteriores y posteriores 
	- __Secuencial__: No se puede procesa mas de un item a la vez. Ya procesados, los puede retornar ordenados/desordenados

![[Pasted image 20250909202005.png]]

# DAGs (Direct Acyclic Graphs)

(! UPV - Compu Paralela o Concu ?)

- Se modela instrucciones mediante un grafo de flujo de datos 
- Los nodos indican tareas y las aristas el flujo de informacion 
- Aciclico -> No puede terminar e iniciar en el mismo nodo
- Permite calcular el trabajo total para cierta secuencia de tareas -> __Camino critico__ (mas largo hasta el final)

## Ventajas 

- Representacion natural para dataflows
- La carga de procesamiento se puede paralelizar 
- Adminte __Lazy Loading__ de las operaciones 