! - checkrepeat -> Corregir un error en diferentes branchs

Docker -> Retorno diferente a 0 dentro de docker compose -> onerror restart (establecer una cantidad de reintentos maxima)

# Paralelizacion

## Objetivos

- Reducir el tiempo de computo de una tarea (_Latencia_)
- Incrementar a la cantidad de tareas que se pueden realizar en paralelo (_throughput_)
- Reducir la energia consumida al realizar todas las tareas

__Camino critico__ -> Maxima longitud de secuencia a computar (mejor rendimiento conseguible)

## Ley de Amdahl

Hasta que punto es rentable seguir paralelizando -> agregar mas procesadores para la parte paralela

Speedup -> ts / tp

Maximo speedup alcanzable -> 1 + tp/ts

### Ley de Gustafson

Corolario: Aumentar el paralelismo permite modificar el tamano del problema original para ejecutar mas trabajo

Por lo tanto, __aumenta el Speedup__

## Modelo Work-Span 

Modelo mas cercano a la realidad para estimar las optimizaciones que el usado por Amdhl proveyendo una cota inferior y superior para el Speedup

__Hipotesis__
	- Paralelismo Imperfecto -> No todo trabajo es paralelizable 
	- Greedy scheduling -> A proceso disponible = tarea ejecutada
	- Tiempo de acceso despreciable
	- Tiempo de comunicacion entre procesos despreciable


T(work) -> Tiempo en ejecutar con un solo proceso

Tinf(Span) -> Tiempo en ejecutar el camino critico

Cota Speedup Superior -> min(P, T1 /Tinf) Se obtiene P en escenarios de Speedup lineal. 

Cota Speedup Superior Inferior-> (T1 -T∞ )/P +T∞ El trabajo se puede dividir en perfecta e imperfectamente paralelizable

![[Pasted image 20250826201711.png]]

f ?? -> Fraccionamiento

## Estrategias de paralelizacion

- Descomposición funcional
- Particionamiento de datos

Depende de la naturaleza del problema

## Patrones de procesamiento

- Fork-join
- Pack/Split
- Pipeline -> Output de un proceso es el input de otro proceso
- Map 
- Reduction


# Multi Processors

! - Manejo de Signals

## Taxonomia de Flynn

Clasificacion de sistemas de acuerdo a la cardinalidad de los flujos de intracciones (procesadores) y datos (memoria)

CISC (x86) vs RISC (ARM, GPUs) -> Conjunto de instrucciones

- SISD (Single instruction single data) -> Sin paralelismo
- SIMD (Single instruction multiple data) -> Paralelismo masivo (GPU)
- MISD -> No tiene sentido -> data-pipelines
- __MIMD__ -> Se divide en dos modelos:
	- _Multiprocessors_ -> Memoria compartida
		- Symmetric multiprocessing vs Asymmetric Multiprocessing
		- Acceso a memoria
			-  ![[Pasted image 20250826212733.png]]
			- Uniform Memory Access (UMA == no-NUMA)
			- Non Uniform Memory Access (NUMA)
	- _Multicomputers_ -> Memoria distribuida
		- Cada computadora tiene su memoria local
		- Cada computadora puede fallar independientemente
		- Cada PC tiene un clock diferente
		- Requieren comunicacion -> Networking (LAN, MAN, WAN)

### Nombres y direccionamiento

- __Naming__ (DNS) -> Permite identificar a una identidad dentro de un sistema (permiten _abstracción_)
- __Addresing__ (IP) -> Mappeo de un _nombre_ con la _dirección_ -> la dirección cambia, el nombre no

#### Ejemplos 

- IP Addres (_name_) -> Ethernet address (_Addr_)
	Protocolo ARP/IPv4

- Domain name (_name_) -> IP address (_Addr_)
	Protocolo DNS -> Top Level Servers (.com, .net, .org, .edu, ...)

- Service (_name_) -> Endpoint (host:port) (_Addr_)
	Service Decovery (Zookeeper, Istio, Linkerd) -> Similar a Java RMI (servidor de nombres - rmiregistry)


# Documentación y Diagramas


_Arquitectura_ -> "Aquellas decisiones de importancia, medidas de acuerdo al coste de modificarlas"

_Diseño_ y _Documentación_ -> Evolutivo -> Adaptación

## Modelos de Documentacion


### Vistas de Arquitectura 4+1

- Vista _Lógica_ (Clases - Estados) -> Estática
- Vista de _Desarrollo_ (Componentes - Paquetes)
- Vista de _Procesos_ (Secuencia - Actividad) -> Dinámica 
- Vista _Física_ (Despliegue - Robustez) -> IMPORTANTE para distro
--
- Escenarios -> __Casos de Uso__ -> Objetivo del sistema


## Tabla de contenidos

1. Scope
2. Architecture Overview
3. Architectural Goals & Constraits -> Motivaciones de las decisiones tomadas
4. Scenarios -> Casos de Uso
5. Logical View 
6. Process View 
7. Development View 
8. Physical View
9. Size and Performance 
10. Quality Appendices
	1. Acronyms and Abbreviations
	2. Definitions 
	3. Design Principles

## C4 Model 

- Code 
- Component 
- Container 
- Software System (???) -> Contexto 

Una especie de Zoom In -> Arbol 


## Diagramas

Arte -> Balanceo, se destaca lo importante, elegantes

Contexto -> Titulo, parrado (previo a la realización)

Información relevante

Principio de Miller: __7 +/- 2 elementos__  -> Captar la atención del publico que los ve

Ejemplos

