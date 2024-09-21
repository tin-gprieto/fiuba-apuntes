
## DHCP

Protocolo para la asignación de IP mediante un servidor DHCP

(...)

## NAT 

- Tabla de transcripción de IP privadas a puertos -> Reescribe el paquete del datagrama (modifica la IP origen/destino)

(10.x.x.x o 192.x.x.x)


_Envio_

IP PRIVADA -> PUERTO 

_Respuesta_

IP ROUTER/PUERTO -> IP PRIVADA

[[Drawing 2024-09-20 20.31.54.excalidraw]]


- Aprovechamiento de la cantidad limitada de IPs -> Limitación de los puertos  


## IPv6

- **Solución a la falta de direcciones** 
	- Solo funcionaba gracias a NAT
- Encabezados modulares
	- Intenta mejorar los defectos de IPv4
	- Vulnerable a ataques -> No pasan en la red
- Se prohíbe la fragmentacion de paquetes en los routers (solo en los host en los extremos)
- Auto-configuración 
	- Similar a DHCP
	- 2 estardares diferentes
- Tratamiento diferencial del flujo
- Sin checksum (obsoleto)

Video de IPv6 (!!!) - IEEE ComSoc 

![[technologies_white_paper0900aecd8054d37d-03.avif]]


## SDN

Software Defined Networks

- Data plane -> Lógica en router
- Control Plane -> Control de las tablas de routeo

Servidor que maneje el routeo (quita la responsabilidad del router)

Solo funciona de forma localizada (para un ISP)


Mas acciones ademas del routeo:
### OpenFlow

TCAM (Ternary Contents Addressable Memory)

_match and action_ -> Matchea el paquete en relación a sus campos por capa y ejecuta una acción:

- Control de admisión  


## Middle boxes

- NAT
- Firewalls
	- Filtra trafico por IP/Puertos 
	- Nadie puede conectarse al dispositivo de una red domestica
- DPI (Deep Packet Inspection)
- IDS (Intrusion Detection System)

_Lectura_: 5 hasta 5.3 (inclusive)