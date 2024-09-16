
## Capa de red

### Diferencias con el resto de capas vistas
- No se ejecuta únicamente en los extremos de la comunicación

![[Pasted image 20240913194104.jpg]]

### Modalidades

- Centralizada
 
 _SDN_ (Software defined networking) -> Controlador remoto

- Descentralizada

En cada router


### Direccion IP

|   RED   |    HOST   |

- La parte de red es la mas importante que utilizar el router para determinar la salida
- El limite es _móvil_

### Clases 

IP and mask: red
IP and ~mask: host

_Clase A_: 0  (1B-3B)

mask: 1111 1111 0...0

0 a 126

_Clase B_: 10 (2B-2B)

mask: 1111 1111 1111 1111 0...0

128 a 191

_Clase C_: 110 (3B-1B)

mask: 1...1 0000 0000 

192 a 223


---

_Clase D_: 1110 (4B-0B)

Multicast

_Clase E_: reservado 

--- Host y Broadcast locales 

0.0.0.0 -> this -> Identificación del host

255.255.255.255 -> Broadcast -> _lo desecha el router_

---

0.0.0.255 -> Broadcast en la red

255.0.0.0 -> Broadcast en todas las redes

---

127.0.0.0 localhost

---
Direcciones Privadas

(A) 10.0.0.0 
(B) 172.16.0.0/8
	127.32.0.0/16
(C) 192.168.0.0
### Prefijos

IP + Mask vs Prefijo -> Puerto de salida

### Routers

#### Plano de control

Quien "escribe los carteles" -> determina el prefijo

#### Plano de datos

Hacia donde va ("Que camino toma") los datos

Función de hash que determina la salida -> O(1)

_Conocido_: lo determina el puerto de entrada -> Cache

_Desconocido_: lo determina el procesador central -> Aplica las mascaras y compara con los prefijos -> O(N)

**Switching fabric**: Entramado de conmutación 

_Random early detection_:
- Buffer 50% : elimina un paquete aleatorio
- Buffer 75% : elimina 10 paquetes aleatorios


### Datagrama IP

- Version: 4 o 6
- IP origen y destino
- Protocolo: TCP/UDP  (que tipo de encapsulacion tiene)
- Tipo de servicio (no esta implementado)
- Checksum
- TTL (_Time to live_) -> cuando es 0 se descarta (se descuenta cada vez que pasa por un router) -> determinado por SO
- Header size 
- Opciones
- Fragmentacion (ID, flags, off-set)
- Datos

### Fragmentacion

_MTU_: Maximium Transfert Unit -> de la capa de enlace

Partición del paquete por el procesador central del router

Dist. maxima en internet: 32 saltos por router


_Tarea_: 

Capturar la salida de un comando ping durante al menos 2 horas y graficar su distribución en escala lineal y después en log-log. Informe PDF.

- Histograma (eje y y eje x log base 2 - 1,5)


_Lectura_: TODO el capitulo 4