## Introducción

### Que es un sistema operativo?

Maquina de Turing vs **Maquina de John Von Neuman** -> Paradigma actual de una computadora

**Kernel** (núcleo) -> Procesos - Concurrencia - Memoria - File system

Distribución = Kernel (Linux) + Apps (GNU) -> Aplicaciones de usuario

**Rol del SO**:

- Proveer un conjunto de servicios útiles para que varios programas utilicen los recursos (hardware) de la computadora
- Maneja y abstrae el hardware -> Protección 

**Forma de utilizar los servicios del SO**

_System calls_: Interfaz de usuario para acceder al kernel. El SO (o kernel) funciona de capa entre los recursos físicos de la computadora y el usuario (programas).

### Funciones de un sistema operativo

#### Referee (Scheduler)

Gestiona los recursos compartidos entre diferentes aplicaciones. Frenar la ejecución de un programa para iniciar la de otro. Se protege a si mismo y los programas, por lo tanta, aisla sus ejecuciones. Determina que recursos utiliza un programa y cuando los utiliza/ deja de utilizar.

#### Ilusionista (Virtualization)

Abstracción del hardware (CPU, MEM) para simplificar el diseño de las aplicaciones. Les hace creer a los programas que tienen utilización completa del hardware.
#### Pegamento (system calls)

Serie de servicios comunes que facilitan el intercambio de info entre apps. Brinda uniformidad en la utilización de recursos.

### User - Kernel mode

![[sisop-user-kernel.png]]

**User mode**: Espacio donde viven todos los programas y aplicaciones de usuario.

**Kernel mode**: Espacio donde se ejecutan funciones restringidas del kernel (SO) que manejan los recursos (abstraídos por software - virtualization). 

*Trap-mode* (bit): Switch entre user-mode y kernel-mode  
## Filosofía de Linux

Sistemas UNIX-like, no están estrictamente basados en UNIX pero lo utilizaron como inspiración. 

### Conceptos

- Cada programa hace bien un SOLA cosa. (No sobrecomplejizar agregando funcionalidades)
- Salida de un programa -> Entrada de otro programa (pipe)
- Diseñar y construir software para probar rápido
- Usar herramientas en lugar de ayudas no especializadas


## Procesos

**Proceso**: programa en ejecución. Se ejecutan en un contexto aislado (sus propios recursos), restringido (recursos limitados) y protegido. Todos los procesos, exceptuando el kernel, viven en user-land.

![[sisop-proceso.png]]

**Ciclo de un programa**: 

1. Fetch: Se obtiene la instrucción, incrementando el _Program Counter (PC)_
2. Decode: Se decodifica la instrucción 
3. Execute: Se ejecuta la instrucción 

### Process Table

Información de cada proceso (asociado al _PID - Process Identifier_)

![[sisop-process-table.png]]
### File Descriptors

Archivos asociados al proceso

- `fd = 0` => stdin - lectura
- `fd = 1` => stdout - escritura
- `fd = 2` => stderr - escritura

## System calls (API)

- **fork()** -> crea un proceso y devuelve su id
	- pid = 0 => proceso hijo (copia exacta del padre)
	- pid > 0 => proceso padre
	- pid < 0 => error
- **wait()** -> espera a un cambio de estado en el proceso hijo
- **getpid()** -> obtiene el pid del proceso actual
- **exec(filename, argv)** -> carga un archivo (binario) y lo ejecuta pasando los parámetros (mantiene su pid)
- **dup()** -> duplica un file descriptor y lo agrega a las process table
- **pipe()** -> Crea un buffer en el kernel expuesto a dos procesos mediante sus file descriptors