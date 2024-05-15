
## File system (vol. 2)

### VFS (Virtual File System)

- Super bloque (SB)

- I-nodo

Estructura principal de un archivo en sistema

- File
- Dentry


### Unix File System calls (API)

#### open()

`int open(const char* pathname, int flags)`

FDT -> file descriptor table 

FDT (in process) -> OFT (open file table) -> I-node Table

| user space | kernel space       |
| ---------- | ------------------ |
| 0          | [file system data] |
| 1          | [file system data] |
| 2          | [file system data] |
| 3          | [file system data] |
| ...        | [file system data] |

#### read()

`ssize_t read(int df, void* buf, size_t count)`

! Nada garantiza que lea lo que se le pida.
Hace un attempt -> lee una cantidad de bytes determinados(_count_) y los escribe en el buffer (_buf_)

#### write()

#### lseek()

Te desplaza hacia un lugar 

`oof_t lseek(int fd, pff_t offset, int whence)`

Tipos de _whence_:
- SEEK_SET
- SEEK_CUR
- SEEK_END

#### dup()

(...)

#### link()


Elimina el nombre de un archivo en el sistema de archivos.

Tipo de files: I-nodo file type
- file (link)
- hard link 
- soft link 


#### dirent.h
lib para trabajar con directorios

`struc dirent {
	`int * file_name 
	`char[256] d_name (nombre del directorio)
}`
* hacer un ls -> codigo!
* hacer una shell
##### opendir()

##### readdir()

##### closedir()

##### stat()

Metadata del I-Nodo

##### access()

##### chmod()

Cambia los bits de modo de acceso

##### chown()

Cambia el id del propietario del archivo y el grupo de un archivo

### Very Simple File System

! Super bloque: describe al sistema de archivos -> guardado en el primer bloque de la partición (cada partición tiene su propio FS)

Organización general : Un bloque -> 4 KB

SB (_super-block_) + BI (_i-node bitmap_) + BBLK (_blocks bitmap_) + 4 blocks de i-nodos (64 i-nodos) + DB (_data-blocks_)

*Bloques -> 16 i-nodos por bloque (de tamaño 256 B)

Offset del primer i-nodo = 3 * 4096 (primeros 3 blocks)

*Data blocks* -> Donde se almacenan los archivos

*i-nodos* -> Meta data de los archivos (apunta a una cierta cantidad de bloques)

### FAT (File allocation table)

Lista enlazada 

## EJERCICIO DE PARCIAL

(ejercicio de bruno)

*mkdir* -> crea un directorio
*touch* -> crea un archivo vacío (si existe le cambia la fecha de cambio por la actual)
*stat* -> metadata

`STAT /dir/s/w/x`

- Leo el i-nodo 43 -> Busco la d-entry "dir" en el bloque 1 -> esta en el i-nodo 45 (por ejemplo)

- Leo el i-nodo 45 -> Busco la d-entry "s" en el bloque 2 -> esta en el i-nodo 15 (por ejemplo)

- Leo el i-nodo 15 -> Busco la d-entry "w" en el bloque 3 -> esta en el i-nodo 5 (por ejemplo)

- Leo i-nodo 5 -> busco el file "x" en el bloque 4 (not found) -> si lo encontrara, haría una nueva lectura de i-nodo (metadata que busca STAT)

! `STAT /dir/s/w/` -> stat del directorio

(dibujo)

!hacer con CAT -> leer 