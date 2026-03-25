
# Escalabilidad 

Se puede adaptar de tamaño
Incremento respecto:

- del Tamaño -> agregar usuarios o recursos a controlas
- de la Distribución geografica -> Dispersion
- de los objetivos administrativos del sistema -> Servicios ofrecidos

## Caracteristicas de las plataformas 


- Plataformas de alta concurrencia 
	- Aplican patrones ta conocidos y probados 
	- Escalamiento automático (con ciertos limites)
	- Vinculación fuerte con la infraestructura o producto

Infraestructura ->

- Arquitecturas Ad-Hoc y Personalizadas -> Cloud
	- Necesidad de configuración y soporte
	- Escalamiento manual o automatizado por humanos 
	- Posibilidad de migraciones a distintas plataformas
	
Arquitectura -> decisiones dificiles de revertir 


## Patron de carga de Aplicaciones web

- Predictable Burst
	- Predecir cierto pico de demanda 
	- Respuesta -> Sumar recursos (alquiler)
- Unpredictable Burst 
	- Aumenta de manera impredecible
	- Respuesta -> Escalar de forma automatica -> __Elasticidad__
- Periodic Processing 
	- Hay momentos sin actividad
	- Respuesta -> Hacer tareas de mantenimiento o tareas asincronicas
- Start Small, Grow Fast
	- Demanda explosiva luego de un arranque lento
	- Respuesta -> Plantear una arquitectura escalable

Utilizacion de los recursos disponibles
	-> 80% - 20% en caso de sobre carga


## Limitantes 


- _Datos_: Volumen, Velocidad, Veracidad, Variedad
- _Arquitectura y Algoritmos_: Diseño
- _Presupuesto_: Transversal a todos los limitantes !
- _Red_: Latencia y ancho de banda
- _Restricciones de Negocio y Legales_

## Tecnicas 

- __Verticalmente__ -> Recursos a un nodo
- __Horizontalmente__:
	- Redundancia 
	- Balanceos de carga 
	- Proximidad geografica 
- __Fragmentacion de datos__  
	- Fraccionar para optimizar 
	- Mnatener juntos datos cercanos 
- __Componetizacion__ -> Separar servicios 
- __Optimizar Algoritmos__
	- Performace
	- Mensajeria 
- __Asincronismo__ 
	- Mantene sincronico solo lo estrictamente necesario
	- Limitado por el negocio


# Elasticidad 

El sistema va a poder escalar solo en base a la carga que tenga el sistema 


## Cloud 

Kubernetes: Orquestador de containers

AWS: Servicio cloud

- Application Load Balancer 
	- Direccionamiento de carga
	- Servicios / instancias nuevas que reciben trafico
	- Servicios / instancias dados de baja que dejan de recibir trafico 
- Autoscaler
	- Scale In/Scale Out e funcion de las metricas recolectadas 
	- Scale out: Incrementar instancias
	- Scale In: Decrementar instancias
- Monitoring Automatico 
	- Metricas sobre el CPU, mem, I/O, networking


# Alta disponibilidad

Aunque haya ciertos componentes que fallen, el sistema debe estar "siempre" disponible 

## Calculo de 9's

Ese siempre depende en realidad de la __probabilidad__:

 P (system available) < 1 -> Definir su cercania a 1
 
- 0,9 -> 36 dias al ano -> MUY MALO 
- 0,999 -> 8,76 horas al ano -> MUY BUENO

### Calculo para conjunto de servicios

- Sistema anidado 

_Web server_ (P(a) = 0,9) - _DB server_ (P(a) = 0,9) - _Report server_ (P(a) = 0,9)

P del sistema -> 0,9.0,9.0,9 = 0,729 -> 4 MESES AL ANIO 


- Sistema replicado 

3 nodos replicados con P(a) = 0,9 -> No es un caso comun, al menos necesita un load balancer 

P del sistema -> 1 - 0,1.0,1.0,1 = 0,999


_SLA_: Service Level Agreement 
- Contrato con el proveedor de cloud (Google/Amazon: Dan Availability de 0,999)

SLO: Objetives 

SLI: Indicators

# CAP Theorem 

Solo se puede garantizar uno de los 2 siguiente atributos:

- __Consistencia__ (Consistency): Todos los nodos responden de la misma manera
- __Disponibilidad__ (Avaliability)
- __Tolerable a particiones__ (Partition Tolerance): Capacidad de de formar subgrupos dentro del sistema 

![[Pasted image 20250923220026.png]]