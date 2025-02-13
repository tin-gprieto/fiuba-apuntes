
_TPT_: No hay presentaciones 

## Datos curiosos

_Problemas para migrar protocolos_

- IPv4 vs IPv6
- TCP vs QUIC

Por lo general es mas común y fácil crear un nuevo protocolo que conviva con protocolo activos que actualizarlos ya que modificarlos de manera global es altamente costoso.

Nueva version de IP ??? 

_DTN_ (Delay tolerant network) 

Redes con demoras grandes o con desconexiones -> No funcionan solo con TCP/IP

_Fragmentacion de la red_ 

Riesgo de fragmentarse por las CDN


## LANs

Red de area local -> Comparten el medio (broadcast)

Cableado o inalambrico


_IPX_ : Tecnología anteriormente popular para implementar LAN 


### Direccionamiento 

_MAC_ (Medium Access Control): Direcciones locales (~= IP)

48 bits 
3 B -> Fabricante (varios x fabricante)
3 B -> ID 

!= RED - HOST de IP 

Dirección reservada -> Broadcast -> FF:FF:FF:FF:FF:FF

_Rangos de vendors_

### ARP (Address Resolution Protocol)

- Protocolo de red para obtener MAC addrs 
- Pregunta al broadcast la dirección MAC del dest. a partir de la IP
- El dest. devuelve su MAC mediante unicast 

| Mac_origen | FF...FF | IP_origen | IP_dest |

_Default Gateway_

## Switch 

!= _HUB_: Lo que se conecta va hacia todos lados (hay colisiones) - DEPRECATED 

Comunicación directa entre puertos de los hosts 

! - No hay colisiones 

L2 (Layer 2) - Capa de enlace 

_Cable UPT_: 2 pares (emisión - receptor)

_Store and forward_

_Bridge_: Conecta dos subredes. Aisla dominios de colisión (en teoría duplica la capacidad). Realiza un listado de src/dest y aprende de como están conectados.

_Switch_: similar pero con mas cantidad de puertos. Contiene una tabla con las MAC address. 

(en teoria no necesita capa de red, pero hubo avances en el filtrado de trafico donde utiliza una ip para conectarse a la red y poder ser configurado - administrable)

### STP

_Spanning Tree Protocol_: Crea un árbol para poder administrar las conexiones entre diferentes switches en una red y no haya bucles en la trasmisión.

RSTP (Rapid ...)


## Ethernet

## Wireless

(Próxima clase)

## Cableadas

IEEE 802.3

- Trasmite una secuencia de bits -> 1010101  (7B) -  0
- Responde con 1010101  (7B) - 1 (SDF). Sirve para sincronizar las frecuencias (de los relojes) entre emisor y receptor

_bit stuffing_

---- no esta en WireShark

- 6B dest. addr -> Lectura rápida para el dest. 
- 6B src. addr 
- 2B length/type (2 versiones distintas)
- 46-1500 datos (minimo 64B - trama minima)
- 4B 



## Otras tecnologías 
### VLANs (extra)

Red LAN virtualizada. Permite aislar las subredes LAN dentro de una misma red LAN. Cada puerto de un switch esta conectado a una VLAN distinta.

Si dos host estan dentro de un mismo switch, necesita de un router para hablarse entre si.

(Cada LAN esta asociada a una direccion de red.)


### IEEE 802.1Q - el protocolo colector (trunk)

Bytes antes de IP

Puerto de VLAN: 4096

Protocolo de soporte para las VLANs ???

### MPLS (_Multiple-Path Label Switching_)

Protocolo de red 

Bytes antes de IP

Etiqueta: _Flow label IPv6_

Tipos de trafico: prioritario/no prioritario/ etc.

Routers que solo realizan forwarding por etiquetas (no hacen rounting) -> Solo para red internas (empieza y termina en el mismo operador)

Utilizado para realizar QoS 

_Time to live_ (TLL) -> robustez a la red

Si TLL=0 forwardea hasta el ultimo router y ese es el encargado de avisar por ICMP que el paquete murió


## REPASO 

_Como se ejecuta en cada una de las capaz una solicitud de una pagina web ?_

---
Configuración previa 

 
Consulta DHCP -> Obtiene su direccion IP y la mascara, IP del DNS local, IP default Gateway (en LAN)

--- 
Aplicación

(suponemos que no tenemos la IP)

Consulta DNS -> www. (...) -> DNS local (tipo A) -> Obtiene IP destino

(PTR - si es de IP a nombre)

HTTP:GET 

--- 
Transporte

UPD -> < 512B (sino TPC)


---
Red 

IP src: DHCP 
IP dest: DNS local

Routing

Consulta en la cache -> sino en la tabla de enrutamiento

--- 
Enlace 

MAC origen: OK
ARP -> Obtener la MAC dest. (sino la tiene la cache ARP - 3s antes del refresh)

Ethernet -> MAC dest. => broadcast 



1. DHCP (IP src)
2. ARP del DNS (MAC addr del DNS local)
3. DNS request (IP dest)
4. TCP SYNC / UDP (ya casi no hay para HTTP)
5. Routing -> tabla de routeo (sino esta lo manda a Default Gateway) -> BGP
6. ARP del Host de destino (MAC addrs del Host)
7. TCP ACK del dest. (Conexion establecida)


_Lectura_: Hasta el 7.3 inclusive

