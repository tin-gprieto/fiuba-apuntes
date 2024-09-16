
## Clase pasada

Capaz del protocolo

Latencia y sus componentes (inserción, trasmisión, transporte y encolado)

## Niveles de aplicaciones

### Cliente 

### Servidor 

## Protocolos de aplicación 

(ej. MQTT)

Mensaje de petición y respuesta 

Sintaxis de mensajes

_Campos_ - función, tamaño y delimitacion

Procesamiento en el envió de mensajes y sus respuestas

#### HTTP Request 

Sirve para el envío de archivos

(*telnet -> conexión remota (similar a SSH pero sin protección)*)

	telnet fi.uba.ar 80


#### DNS
delimitacion
Servicio proveedor de nombres a IPs (nic.ar)

No es protegido (!= eDNS y ECS)

Resuelve el IP -> Se requiere y lo busca (iterativa/recursivamente)

_Herramientas_: dig

**Zona directa**

Funciona de manera autónoma pero depende del servidor DNS a donde este conectado (el primer punto para ir a buscar)

La base de datos distruibuida de DNS guarda _resource records (RR)_

RR -> tupla de 4 elementos (Name, Type, Value, TTL)

Name: google.com
Type: A, AAAA, CNAME, MX
Value: 190.192.8.64 (type A)
TTL: ???

_Servicios de DNS_:
- Host aliasing
- Mail aliasing
- Load balancing

_Local resolver_: Servicio iterativo (utiliza cache local)

#### DOH




