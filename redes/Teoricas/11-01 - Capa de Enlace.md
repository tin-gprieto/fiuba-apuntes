
## Generalidades de la capa de enlace

### Tipos 

- Conexiones punto a punto
- Conexiones multiples

### Servicios 

- framming (separacion de datos)
- MAC (Medium Access control) -> acceso al enlace 
- Entrega confiable 
- Detección y corrección de errores (EDC) -> Alta probabilidad de errores 
	- Generacion de errores por el medio fisico (desperfecto en emitir o recibir las senales por cable o inalambricas)
	- 
## Medidas Físicas

- Potencia y atenuación (producto de la distancia)
- _BER (Bit error rate)_ -> #bits errados / #bits totales 
	- Wifi: 10^-3
	- Fibra óptica: 10^-9
- Detección y corrección de errores (EDC):
	- Verificación de paridad (_Checksum_):
		- Unidimensional
		- Bidimensional-> de dos dimensiones (matriz)
	- _CRC (Cycle redundancy check)_ -> Mucho mas efectivo 

## Protocolos de Acceso Multiple

- Medios de difusion (broadcasting)
- Formas de administrar el uso del canal
	- Partición del canal (TDM, FDM, CDMA)
	- Acceso aleatorio (ALOHA, CSMA/CD, CDMA/CA)
	- Por turnos

### TDM 

Time Division Multiplexing 

### FDM

Frequency division multiplexing

### CDMA 

Division en canales por clave

Muchas situaciones ocurriendo en el mismo canal

*XOR*
0: Pasa la información
1: No pasa 

-> Utilizado para criptografia

### ALOHA

Literalmente hawaiano

### CSMA/CD

! Colisiones en la conexión -> Collision detection


### CSMA/CA

Collision Avoidance

## Wi-Fi

LAN inalambrico 


## Token Ring, Token bus

Competencia de Ethernet 



_Lectura_: Resto del capitulo 6

