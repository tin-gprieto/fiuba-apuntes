
# Prácticas

## Docker compose

Herramienta de orquetación -> de containers

Incluido en docker (antes docker-compose)

De más alto nivel -> Hecho en python y utilizar docker

Se describe una estructura de container y su configuración

Containers -> _SERVICIOS_

### Sintaxis

__FORMATO YAML__

	name: ...
	
	services: ...
	
	(service name):
		image: (image name) -> dockerfile
		volumens:
		ports:
		links:
		network:
	
	(2nd service name):
	...
	

Ejemplo:

name: 

services:
	app:
		image: mi-app:1.0
	nginx:
		image: ngninx:1.27.4
		volumes:
			- ../ngnix/nginx.conf:__/etc/nginx/conf.d/default.conf:ro__
			(ruta de host):(ruta del container-> path en documentación de nginx)
		ports:
			- 5555:80
		links:
			- app


image o __build__

	build: app/

Donde haya app/Dockerfile
### Comandos

Levantar todos los contenedores del compose (= build) -> Crea la infraestructura

	docker compose up

Destruir la infraestructura

	docker compose down 

Destruir la infraestructura eliminando los volumenes 

	docker compose down -v 

Parar/empezar la ejecución de los contenedores 

	docker comṕose stop 
	docker compose start

Ver información de lo que está corriendo

	docker compose ps


Levantar __N__ instancias de app

	docker comose up -d --scale app=N

(o dentro del docker-compose.yml - DEPRECATED - Solo en el caso de necesitar algo fijo) -> scale: N 

Correr un comando dentro de un contenedor

	docker exec -it (contenedor) (comando)

Ejemplos:
- Ejecutar bash
	
		docker exec -it clase2-ngninx-1 /bin/bash
	
- Refrescar el archivo de configuración nginx

		docker exec -it clase2-ngninx-1 /ec/init.d/ngninx reload 


# TP 1


Entrega: __9/10__

Wallet digital 

Arreglar el sistema de intercambio de monedas


## Análisis de la arquitectura:

- Determinar y justificar cuales son los QA clave
- Pruebas de carga
	- Graficar métricas relevantes para tener un panorama
- Realizar un diagrama de __Composnents and connectors__ -> CLASE CON GUILLE (???)

## Pedidos adicionales
	
- Obligatorio .> volumen y neto operador
- Opcional -> Parte del TP2 -> almacenar la info en un .json 

## Desarrollo

! README

Postman en directorio doc/

.env -> Variable de entorno

Grafana -> Dashboards

https://github.com/fiuba-arq-soft/2c2025-tp-1


# QA - parte3


## Availability 


### Recovery 


Recuperar un sistema en un estado inválido

! rollback


### Prevention 


Prevenir situaciones de caida del sistema

! Transacciones ACID 


## Ejercicio Transcoder

! C&C

- Load balancer entre nodos de transcoder
- CDN -> Acceder a contenido por ubicación geografica


## Ejercicio 16 - Sistema web de procesamiento de imágenes

! C&C

Replicación
- Web server -> Activa -> Todos aceptan las consultas mediante un load balancer
- Base de datos -> Pasiva -> Una copia primaria y varias de backup