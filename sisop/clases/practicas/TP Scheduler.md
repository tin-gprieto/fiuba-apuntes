(clase 04-26)


Correr el proyecto:

 **Docker** -> Ubuntu 16

`./dock build` -> Compila la imagen de Docker

`./dock run` -> Corre la imagen de Docker
 
 **QEMU**
 
`make qemu - make qemu-nox

`make qemu CPUS=N` -> Correr el kernel con N cores

`make grade` -> pruebas
## 1. Cambio de contexto

De kernel a usuario, de usuario a kernel. Se inicia un timer, una vez se termina el tiempo, se desaloja el proceso del kernel.

- De usuario a kernel -> se llama a una syscalls
- De kernel a usuario -> se termina el tiempo de ejecución del proceso

Enviroment -> Process 

env_id = pid

No hay file descriptors porque no incluye el file system

**env_status** -> Runnable, ...



## 2. Scheduler - Round Robin

`make <target> USE_RR=1`

## 3. Scheduler - Sistema de prioridades

Lo determina el equipo -> INVESTIGAR POLÍTICAS 

`make <target> USE_PR=1`