
## Repaso

### Internet

Que es internet? Red de redes

Conexión por niveles

Tier 1 (Google, Facebook)
Tier 2 (Telefonica, Telecom)
...

### Conectividad

Comunicación _unicast_: fuente de emisión con un único receptor

Comunicación _broadcast_: fuente de emisión que cualquiera puede escuchar

Comunicación _multicast_: similar al broadcast pero limitando a un grupo reducido de receptores

### Modelo TCP/IP

Protocolo dominante

Modelo de capas: Las capas superiores solicitan servicios a las inferiores.

Cada capa tiene un TAP (?)
**5** capas: 

1 - **Aplicación** (DNS, HTTP, VPN, SSH, DHCP, CDN)

*DHCP*: Asignación dinámica de IP

2 - **Transporte** (TCP, SSL) (protocolos de control de transporte)
3 - **Red** (ICMP, IP)(direccionamiento)

-----------FÍSICO--------------

4 - **Enlace** (Ethernet, WIFI, Bluetooth)
5 - **Física** (fibra óptica, coaxial, UTP)

### Métricas de performance

#### Packet loss

Perdida de información 
#### Latencia

Retraso entre el estimulo y la respuesta -> ping

Importancia:
- Impacta en la UX
- Aplicaciones sensibles

Causas: 
- Latencia maxima del medio
- Estado actual: cantidad de trafico

Causas técnicas:

- _Tiempo de inserción_ 

	Tiempo en insertar en el canal (sin importar de la distancia) -> Velocidad de los enlaces

Ti = L/R (L: largo del paquete)(R: velocidad de serialization)
 
- _Tiempo de propagación_ (transmission delay)

	Tiempo de atravesar el canal

Tp = d/e (e: velocidad del medio / aire, fibra)(d: distancia entre extremos)

- _Tiempo de procesamiento_ (despreciable)

	Tiempo de procesamiento del paquete por parte del router: leer el header y tomar la decision de routeo


- _Tiempo de encolado_ (buffer) -> **IMPORTANTE**

Tiempo que espera un paquete en el router desde que llega hasta que es transmitido

Depende de: 
	Tasa de ocupacion del router
	Tamanio de la cola

A mayor trafico, mayor tiempo de encolado. Es decir _depende de la demanda del router_.

L: 
a:
R:

#### Round-Trip Time (RTT)

Tiempo que tarda un paquete de datos enviado desde un emisor en volver al mismo emisor habiendo pasado por el receptor (=ping)

ej: Radar

#### Throughput 

(tasa a la que se trasfieren bits entre transmisor/receptor)

Cantidad de datos que se pueden trasmitir en una red en un periodo determinado.

Diferencia entre el ancho de banda y el throughput? 

Máximo (el que te cobran) vs Real (el que te venden)

#### Jitter

Variación en el tiempo que tarde un paquete de datos en viajar desde su origen hasta su destino. Mide la fluctuación del retardo. -> IMPORTANTE PARA LLAMADAS


! EJERCICIO PARA LA PROXIMA

![[Screenshot from 2024-08-22 20-15-34.png]]





