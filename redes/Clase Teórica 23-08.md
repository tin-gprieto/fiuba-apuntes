
## Capas (TCP/IP)

1. Aplicación (HTTP(S), SMTP, FTP, SSH, CDNs, DNS, VPN, DHCP, LDAP)
2. Transporte (TCP, UDP, SSL, QUIC)
3. Red (IP !)
4. Enlace (Ethernet, Wi-Fi, Bluetooth, NFC, cablemodem, ADSL)
5. Física (Fibra óptica, coaxial, UTP, aire)


*Modelos de 7 capas (OSI) - deprecated


## Capa de APLICACIÓN

Arquitecturas de aplicaciones:
- Cliente-Servidor (servidores centralizados en datacenters)
- P2P (ex. bit torrent)

### Transporte

Comunicación entre procesos: _socket_ (transporte)

Características del transporte: 
- Trasmisión confiable
- Caudal
- Sincronizar 
- Seguridad 
- Con/Sin perdidas
- Conectado vs Desconectado 

(Organismos normalizadores)
- IETF -> RFCs
- ITU (Reglamentar las frecuencias, código de teléfono)
- W3C

### Protocolo HTTP (HyperText Transfer Protocol)

Aplicación Cliente-servidor

Permite transmitir texto formateado, imágenes, multimedia, etc

Conexiones: No-persistentes vs persistentes

_Web Caching_ : necesita fecha de vencimiento

Servidores HTTP para hacer pruebas

HTTPS -> asegura la identidad del endpoint

Métodos: GET 

### DNS (Domain Name System)

Relación: Nombre <-> IP 

Base de datos jerárquica y distribuida:
- Sin punto de falla
- Multi consulta
- Administración distribuida

_Host aliasing_: mismo nombre != IP ()

_Mail server aliasing_

_Load distribution_

#### TLDs (Top Level Domains)

WWW.FI.UBA.AR.

WWW : HOST

FI.UBA.AR. : DOMAIN

. : root -> servidor root

AR: TLDs -> por normativa hay al menos 2 (REDUNDANCIA !)

UBA: Authorizer (Autoritativo)

Tipos de consultas a la DNS: recursivas vs iterativas

Pregunta al DNS local y espera a su respuesta (recursiva)

El DNS resolver local realiza consultas iterativas hasta obtener la IP y luego se lo devuelve. 

DNS Resolver local: resuelve mas rápido

*ejercicio no obligatorio*: consulta iterativo con dig (autorizada y verborragia) capturarlo con WireShark (no usar fi.uba.ar ni google)

*Lectura*: Hasta 3.4 inclusive para la teórica -> PARCIALITO (SOLO DEL 3)


#### Tipo de consultas

FALTA


