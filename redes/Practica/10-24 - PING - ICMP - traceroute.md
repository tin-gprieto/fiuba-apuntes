
## PING 


- ICMP Echo Request
- ICMP Echo Replay/response

Diagnosticar el estado, velocidad y calidad de una red

	ping [URL | IP]

Diagnostica el porcentaje de perdida

! - Puede cambiar la ruta por la que llegan/vuelven los paquetes


## ICMP 

Protocolo de la _capa de RED_ -> Comunicación entre los routers

Internet Control Message Protocol / RFC 792

De la familia de TCP 

### Error reporting

No se reportan errores si el paquete causante:
- Es ICMP
- Es de broadcast 
- Es un fragmento distinto al primero 

Para evitar:
 - loops 
 - Packet explosion 


## Traceroute 

Es una herramienta para descubrir redes entre un origen (src) y un destino (dst)

IP fue concebido como un protocolo end-to-end por lo cual los host desconocen la estructura de la red


## Wireshark 

- Filtrar por IP !


_TTL_ !


---

# Repaso Parcial 


## Ejercicio de Subnetting

![[image.png]]


1b -> 2
2b -> 4 -> mask 30
3b -> 8
4b -> 16
5b -> 32 -> mask 27
6b -> 64 -> mask 26
7b -> 128 -> mask 25

| Subnet | # Hosts | Tamano de bloque | prefijo           |                  |
| ------ | ------- | ---------------- | ----------------- | ---------------- |
| A      | 100     | 128              | 190.240.0.0/25    |                  |
| B      | 62      | 128              | 190.240.0.128/25  | 0.10000000 = 128 |
| C      | 100     | 128              | 190.240.1.0/25    | 1.00000000 = 1.0 |
| D      | 60      | 64               | 190.240.1.128/26  |                  |
| E      | 100     | 128              | 200.10.227.0/25   |                  |
| F      | 30      | 32               | 200.10.227.128/26 |                  |
| G      | 20      | 32               | 200.10.227.192/27 |                  |
| H      | 10      | 32               | 200.10.227.224/27 |                  |
| S13    | -       | 4                | 200.10.227.240/30 |                  |
| S23    | -       | 4                | 200.10.227.244/30 |                  |
| S34    | -       | 4                | 200.10.227.248/30 |                  |
| S35    | -       | 4                | 200.10.227.252/30 |                  |

## Tabla de routeo 

Mascara 

111...11.....000...00 
b de red	 b de hosts
/n             32-n

| Subnet | Prefijo           | Mascara         | Interfaz |
| ------ | ----------------- | --------------- | -------- |
| A      | 190.240.0.0/25    | 255.255.255.128 | IF1      |
| B      | 190.240.0.128/25  | 255.255.255.128 | IF1      |
| C      | 190.240.1.0/25    | 255.255.255.128 | IF2      |
| D      | 190.240.1.128/26  | 255.255.255.192 | IF2      |
| E      | 200.10.227.0/25   | 255.255.255.128 | IF3      |
| F      | 200.10.227.128/26 | 255.255.255.192 | IF3      |
| G      | 200.10.227.192/27 | 255.255.255.224 | IF4      |
| H      | 200.10.227.224/27 | 255.255.255.224 | IF4      |
| S13    | 200.10.227.240/30 | 255.255.255.252 | IF1      |
| S23    | 200.10.227.244/30 | 255.255.255.252 | IF2      |
| S34    | 200.10.227.248/30 | 255.255.255.252 | IF3      |
| S35    | 200.10.227.252/30 | 255.255.255.252 | IF4      |


## TCP

RFC 281 -> Fast recovery

