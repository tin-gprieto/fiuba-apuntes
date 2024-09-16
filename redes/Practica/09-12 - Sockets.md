
Que es un socket?

Es una puerta para la comunicación entre procesos

Se implementa como una _tupla_ de (dirección, puerto) del destino 

### Socket UDP - Socket TCP

#### TCP

![[Pasted image 20240912190716.png]]

Socket mode: visit -> Server (esperando conexion)

_Linux_: file descriptor (implentacion)

_socket_ (addr_famiy, type)
- addr_family: AF_INET (IPv4)
- type: **SOCK_STREAM** (TCP)
 
_socket.bind_ (addr) -> asocia el socket con una dirección
- addre: IP+PORT  propio

_socket.listen_ () -> Indica que debe aceptar conecciones
- _SERVER_

_socket.accept_ () -> bloqueante hasta recibir una nueva conexion TCP
- _SERVER_

_socket.connect_ (addr) -> bloqueante = que socket.accept()
- _CLIENT_
- addr: IP+PORT del server

_socket.send_ (data)
- data: bytes (.encode())

_socket.recv_ (buff_size)
- buff_size: cantidad de bytes a recibir \
- Devuelve los bytes recibidos (.decode())

_socket.close_ () -> Cierra el socket (server/client)

#### UDP

![[Pasted image 20240912190757.png]]

_socket_ (addr_famiy, type)
- addr_family: AF_INET (IPv4)
- type: **SOCK_DGRAM** (UDP)

_socket.bind_ (addr) -> asocia el socket con una dirección
- addre: IP+PORT  propio

_socket.sendto_ (data, address)
- data: bytes (.encode())
- address: IP+PORT dest

_socket.recvfrom_ (buff_size)
- buff_size: cantidad de bytes a recibir \
- Devuelve los bytes recibidos (.decode())

_socket.close_ () -> Cierra el socket (server/client)

### TP

- Implementar sobre UDP un protocolo de _Go Back N_ y _Stop and Wait_


