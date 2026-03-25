
# Practica: Traffic Lights Violations Detectors


● Se requiere un sistema de detección de infracciones para la ciudad.
● Se cuenta con las imágenes de las patentes capturadas por las cámaras en
cada semáforo.
● Los semáforos a su vez emiten señales que indican su estado como verde,
amarillo o rojo.
● Se debe emitir una infracción a ser enviada al propietario del vehículo y al
ente regulador para su procesamiento.
● Las infracciones deben soportar su inspección y administración por parte
del personal del gobierno.

1. Casos de usos
2. Endpoints -> Información
3. Analisis de volumen -> Saber ordenes de magnitud -> Comprender el impacto en el sistema
	1. Cantidad de cámaras
	2. Cantidad de autos que pasan por cámara por minuto
	3. Cantidad de fotos que saca por auto -> Segun el tiempo que esta en rojo
	4. Cantidad de infracciones por autos -> 0,1%
	5. Conclusion -> Flujo de cantidad de datos
4. Diagrama de arquitectura 
## Endpoints

Outbound -> Salida (POST)
Inbound -> Entrada (GET)

POST/mails

POST/infracciones

GET/patentes

POST/photos -> Size ? Qty?
	 Body {
		 - image
		 - timestap
		 - id
	 }


- gestion
	-POST 
	-GET

# Shared Code Snippets


Compartir codigo entre usuarios
- Acceso publico mediante conocimiento de la ruta de acceso
- Texto del codigo y lenguaje
- Codigo almacenado por tiempo indefinido
- Gran cantidad de accesos diarios -> Para el mundo? No especificado -> Se asume porque es un large scale system 
- Sistema de disponibilidad constante 