---
~
---

**Servidor proxy**: intermediario con el local. Ayuda con requerimientos frecuentes o de diferentes dispositivos en la misma red. Importante cuando los enlaces eran muy lentos.

## Capa de transporte

Permite a las aplicaciones conectarse. (comunicación de procesos)

#### best effort _- lo mejor que puede_

- Es heredado de la capa de red
- Facilita el diseño de equipos y protocolos _simples_
- Causa del crecimiento de internet


*protocolo*: Reglas en orden (similar a un algoritmo) que utilizan muchos para comunicarse. 

ex. Smart Contract en blockchain

### Servicio 

- **multiplexar y demultiplexar**
- verificación de errores _minima_
	- Proporciona **confiabilidad**
	- **control de flujo**: si el receiver no puede recibir, deja de enviar
	- **Seguridad**

	netstat : Comando 
		-an : flag

2^16 : 64k -> 0 a 65535 (max. de puertos)

| _source_ (fuente) | _dest_ (destino) |
| ----------------- | ---------------- |
| IP:PORT           | IP:PORT          |

_wellknow ports_: 0 a 1024


### UDP: User Datagram Protocol


RFC 768 (https://www.rfc-editor.org) STD XXXX 

(se declara como standard - los RFC sin STD también ofician como standard)

0-----------15--------31 (32 bits)

| Source port | Dest port |
| ----------- | --------- |
| Length      | Checksum  |
| Payload     | ...       |


_CHECKSUM_: Toma los IPs, suplanta el checksum por cero y calcula la suma = compara con el valor de checksum (si es igual no hay error, si es diferente hay error)

_CRC_: resistente a problemas de checksum (ejemplo de video)

**SE USA EL DNS POR VELOCIDAD**

Problema en la perdida de paquetes (_best effort_ -> sin acuse de recibo) 

Solución -> Repetición (redundancia)

Si la respuesta del DNS es mayor a 512B -> Se arma una conexión TCP -> Se hace para garantizar que un paquete tan grande no se pierda

### Principios de comunicaciones confiables

#### Conectadas vs No-conectadas

_UDP_: No conectada -> no puede identificar cada paquete (!= NO ES CONFIABLE)

_TCP_: Conectada -> Puede identificar los paquetes y por tanto el orden

#### Entrega asegurada

#### Orden asegurado

(NECESITA LA CONEXIÓN)

#### Integridad asegurada

NO se modifican los bits

*UDP*: Lo garantiza por el checksum (malardo)

#### Desempeño 

No es imprescindible 

_UDP_: Depende de la aplicación 

#### Control de flujo

Manejar si el receptor puede recibir los mensajes dado el flujo de mensajes que esta procesando

#### Comparte el canal EQUITATIVAMENTE

Para que no haya una conexión que acapare todo 

_UPD_: Se utiliza la velocidad que quiere

_TCP_: Se autoregula para no saturar el canal 

#### Seguridad


### Tipos de flujo

#### Stop & Wait (desempeño)

Se manda y espera a recibirlo

#### Continuo

Continua enviando a pesar de la respuesta 

! - Concepto de ventana deslizables
##### Go Back N

Cuando detecta que un paquete N no se envío, vuelve a enviar los paquetes >=N

TODO tiene que llegar ordenado

##### Selective repeat

Reenvia los paquetes que exactamente no recibieron acuse


### Resumen de las variables y los mecanismos de flujo confiable de datos

- Checksum o CRC
- Temporalizador
- Numero de secuencia
- Acuse de recibo (ACK)
- Acuse negativo de recibo (NACK)
- Ventana deslizante: para implementar un flujo de datos con _alto desempeño_

*Lectura*: Resto del capitulo 3 

