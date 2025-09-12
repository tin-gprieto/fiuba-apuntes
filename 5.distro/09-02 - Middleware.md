
# TP0

!!!
Se puede hacer con threads e igual con procesos -> No son operaciones cpu intesive (TP0)

Se puede usar multiprocessing

Problema con el mutex de python para threads

SE PUEDE USAR LIBRERIA THREADING DE PYTHON

 
## Defensa

- Tener lista los tests
- Como manejar batching
- Como manejar la concurrencia
- README !
- Se tienen hasta las 23:59

# Grupos, Middlewares y MOM

## Grupos de comunicacion 

Procesos con cierta afininidad -> GRUPO

Que necesitan comunicarse entre si

Un proceso tiene _pertenencia_ a cierto grupo

## Difusión de mensajes 
### Uno a Uno 

_Unicast_ -> Punto a punto

_Anycast_ -> Uno solo del grupo recibe el mensaje

### Uno a muchos 

_Multicast_ -> Uno a varios

_Broadcast_ -> Uno a TODOS

## Centralizada vs Descentralizada

Centralizada: Uno se encargar de ir mandando a cada uno

Descentralizada: Delega la difusion a medida que va mandando

## Topologia 

- Anillo 
- Punto a punto 
- Jerarquico (arbol)

## Atomicidad de mensajes 

2PC - 2 phase commit - https://es.wikipedia.org/wiki/Commit_de_dos_fases

-> SUPUESTOS ! -> El commit no puede fallar 

Algoritmo de consiliacion -> Mainframe bancario

3PC - 3 phase commit ! -> Bajar la probabilidad de fallo

- Los mensajes llegan a todos o a ninguno 



# Middleware 


Software que proporciona un servicio de ___conectividad/comunicacion___ entre un sistema distribuido que garantiza cierto funcionamiento entre equipos heterogeneos (altamente independientes).

## Beneficios 

- Transparencia
- Tolerancia a fallos
	- Comunicacion en todos lados
	- Seguridad
	- Realibility
	- Safety 
	- Manteniability 
- ACCESO A RECURSOS DISTRIBUIDOS
- Sistema distribuidos abiertos 
	- Unifica el tipo de comunicacion -> Homogeniza a los componentes de la red
- Comunicacion de grupos (lo facilita)
	- broadcasting - multicasting


## Diposicion
- Centralizado a nivel logico-fisico: Servicio dentro de un servidor - clientes con una biblioteca para acceder al mismo de manera caja negra (RMI - rmiregistry)
![[Pasted image 20250902210544.png]]
- Centralizado a nivel logico (middleware) pero distribuido
![[Pasted image 20250902210627.png]]

## Clasificacion

### Orientacion a transacciones (Transaction procedure)

- Garantiza transaccionalidad de operaciones respecto de datos
- Conectan muchas fuentes de datos y permiten un acceso transparente al grupo
- Poseen politicas de reintentos y retencion de datos frente a caidas internas

### Orientado a procesamientos (Procedure Orieted)
- Servidor de funciones a invocar
- Los servicios se puede exxplorar y ejecutar pero no presentan estado para futuras invocaciones
![[Pasted image 20250902211914.png]]
	
### Orientado a objetos
- Ejemplo: RMI 
- Mensajes hacia objetos distribuidos
- Los objetos viven dentro del middleware 
- Esquema de 'marshalling' para transimitir la informacion 
![[Pasted image 20250902211141.png]]
### Orientado a mensajes - MOM (Message Oriented Middleware) 
- Ejemplo: JMS
- Funciona como un sistema de mensajeria 
- Pueden enviarse mensajes bajo cierto topico para que aquellos interesados lo reciban
- Pueden utilizarse mensajes con un destinatario definido (_Queue_)
- ![[Pasted image 20250902212602.png]]
- Centralizado vs distribuido
![[Pasted image 20250902215423.png]]
- Bus de informacion vs Colas de mensajes 
![[Pasted image 20250902215451.png]]
- Brokers

### Reflective Middleware (de configuracion dinamica)

Ejemplos:
- Remote method invocation (RMI)
- Java Message Service (JMS)


# TP 1: Diseño 

Cofee Shop Analisys

- Requerimientos funcionales
- Kaggle -> Resultados esperados

Diseno de COMO RESOLVER EL SISTEMA 

Realizar un documento de arquitectura -> 16/09 (12 DIAS)

Documento impreso -> Presencial -> Validacion 

NO SE EVALUA CODIGO

Division de tareas para cada miembro del grupo



