

## Caracterizacion del paradigma actual

![[Pasted image 20250819210222.png]]

- Caducidad de la Ley de Moore por perdida de performance -> Solución -> Multiprocesamiento
- Internet como medio integrador indiscutido -> Globalizacion (Cama Botnet Census)
- Próximo factor multiplicador de conexiones a internet -> IoT (!) 

## Arquitecturas

- Cliente - Servidor
- peer-to-peer (p2p)
- SD Heterogeneo -> Diferentes dispositivos, con diferentes SO, CPU, comportamientos, funcionalidades

## Sistema distribuido

"Colección de computadoras independientes que para el usuario ve como un solo sistema coherente" - Tanenbaum

"Sistema de computadoras interconectadas por una red que se comunican y coordinan sus acciones intercambiando mensajes" - Coulouris

__"Aquel que en el fallo de un computador que ni siquiera sabes que existe, puede dejar a tu computador inútil" - Lamport__

### Definiciones
- Colección de computadoras -> Multiprogramacion
- Independientes -> Autónomos
- Un solo sistema -> el usuario no conoce su distribución
- ...


### Principios

- Transparencia -> No me doy cuenta como esta hecho -> Diferentes tipos de transparencias
- Acceso a recursos compartidos
- Sistemas distribuidos abiertos (Interfaces, Interoperability, Portability) -> Ecosistema
- Escalabilidad
- Tolerancia a fallos (Avaliability, Reliability, Safety, Maintainability)

### Variantes de la multiprogramacion

- Multi-threading
- Multi-Processing
- Multi-Computing -> Procesos en computadoras independientes

### Diferencias entre paralelo y concurrente 

Paralelo -> Procesos independientes sin competir por el uso de computador

Concurrente (Competidores) -> Procesos que se disputan el uso de CPU y memoria

### Centralizado vs Distribuido

Centralizado
	- Dificiles de escalar
	- Control -> Efectivo y eficiente
	- Homogeneidad
	- Consistencia ->de Información y monitoreo de estado global
	- Seguridad -> Menos superficie de ataque

Distribuido
- Disponibilidad
- Escalabilidad
- Reducción de Latencia
- Colaboración 
- Movilidad
- Costo

### Descentralizar vs Distribuir

__Centralizar__: Concentración de la autoridad a nivel lógico
__Descentralizar__: Transfiere la toma de decisiones a eslabones inferiores de la organización
__Distribuir__: Modelo descentralizado de control para coordinar actividades con una coherencia dada


### Pensamiento distribuido

"Cualquier organización que diseñe un sistema, inevitablemente producirá un diseño cuya estructura sera una copia de la estructura de comunicación de la organización" - Ley de Conway

## Virtualizacion

- Necesidad de independencia real de los recursos
	- Seguridad en el acceso
	- Diferenciacion entre las intrucciones con privilegios vs sin privilegios
- Hypervisor (Virtual Machine Monitor)
	- Manager de VMs
	- Emulacion de Hardware
- Container Engine ! -> Docker

### DOCKER

Desarrollado en goland

Arquitectura de cebolla
- Docker deamon
- Docker REST API
- Docker CLI

Kubernetes, AWS, GP, Axure, etc. -> Soportan Docker

- Namespaces (NET, PID, MNT, IPC, USER)
- Cgroups
- Union Mounts

__TODOS LOS TPS SE ENTREGAN CON DOCKER__

Conceptos:
- Dockerfile -> intrucciones para crear la imagen
- Imagen -> Bloques estaticos
- Docker -> Instancia de una imagen
- Volume -> Sistema de directiorios compartidos entre el Host OS y el container

Docker Compose -> Utilizar varios contenedores, formar una red, etc.