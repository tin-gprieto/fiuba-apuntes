
## Definiciones importantes

### Procesos

### Kernel

### Scheduler 

### Memoria 

API:
- *brk* -> sustituye la direccion del brk, que apunta al tope del heap (recibe * void)
- *sbrk* -> el parámetro 

### Concurrencia 

### File System 

Abstracción del sistema operativo que provee _datos persistentes_ con un nombre.

Virtual File System (VFS) esta compuesto por: 
- *Super bloque*: Representa todo un sistema de archivos
- *I-nodo*: Representa un determinado archivo dentro de un sistema de archivos 
- *D-entry*: Representa la entrada en un directorio (componente simple de un path)

Directorio compuesto por:
- path -> id del directorio
- root_directory -> raíz de los directorios ("~/")
- absolute_path -> desde la raiz
- relative path -> desde el directorio actual
- current directory -> directorio actual en el cual se ejecuta el proceso
- hard link -> 
