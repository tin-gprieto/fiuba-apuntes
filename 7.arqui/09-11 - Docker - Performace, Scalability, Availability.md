
# Práctica

## NodeJs

(Clase pasada)

## Docker 

Reducir la carga administrativa y de computo de mantener varias computadoras o entornos.

Aislar los procesos -> entornos personalizados
- Seguridad para islar los procesos del file system y recursos compartidos


__CGroups__ -> Control groups -> Cotas de recursos para un grupo de procesos


Virtualización -> Virtualización de hardware

Containers -> Virtualización del sistema operativo -> Contenedor = proceso

Integración continua -> Pruebas sobre un docker
### Como usar Docker 

__Dockerfile__ -> Imágen -> Instrucciones para el deamon de Docker 

Diferencias entre una imágen y un contenedor 
	Imágen: Solo lectura
	Container: Lectura y escritura sobre la última capa de varias imágenes
#### Directivas para el Dockerfile 

- _FROM_ - Utiliza una imágen base () -> https://hub.docker.com 
	- FROM scratch -> Empty imagen
	- FROM node:(tag) -> Imagen base de node (tag de ejemplo: 22)
	- FROM linux -> Alpine (más básica y liviana -> Hay que instalar muchas cosas), debian, ubuntu

- _RUN_ - Ejecutar comandos ()
	- Ejemplo: RUN mkdir /opt/app
- _WORKDIR_ - Setea el directorio actual
	- Ejemplo: WORKDIR /opt/app
- _COPY_ - copia archivos del host en el container
	- ORIGEN (File system host) ... DESTINO (Fily system docker)
	- COPY app.js (host) ./ (virtual)
- _ENTRYPOINT_ - Comando al iniciar el docker - [comando, parametros]
	- Ejemplo: ["node", "app.js"]
- _EXPOSE_ - Puertos del contenedor que serán utilizados (documentación) 
	- Mappea de manera que no colisione con otro servicio corriendo en ese puerto del host

#### Crear la imagen dentro de docker

docker __build__ -t (mi imágen) mi-app:1.0 

Va creando contenedores temporales donde va instalando cada linea del Dockerfile hasta llegar a una última imagen que contiene todas las anteriores 

![[Pasted image 20250911185225.png]]


docker images -> Listado de imágenes creadas

#### Correr un container

docker __run__ (image tag)
- docker run -d
- docker run -p (host-port:vm-port) -> MAPEO DE PUERTOS

docker __ps__ -> Listado de contenedores corriendo
- docker __ps -a__ -> Listado de contenedores corriendo y PAUSADOS

docker __stop__ -t0 (docker name)

docker __logs__ (docker name) -> Muestra la consola del contenedor

### Crear redes dentro de Docker 

docker __network__ __create__ (network tag)

docker run -d --name (container name) __--network (nw tag)__ (image tag)

#### Load Balancer

Componente de red (fisico o por software) que balancea la carga, es decir, distribuya request entre diferentes hosts

(Ejemplo: NGINX)

Containers -> DOWNSTREAM

Servidores -> UPSTREAM

__nginx.conf__

app, app2 -> Dos contenedores en la misma red recibiendo desde el puerto 3000 del contenedor

upstream application{
	least_conn; -> Balancea al contenedor con menos conexiones abiertas
	server app:3000; -> weith n -> Peso para ponderar el balanceo
	server app2:3000;
}

server {
	listen 80;
	location / {
		proxy_pass http://aplication/; -> Balanceo por round-robin
	}

}

docker run -d --name nginx -p 555:80 -v ./nginx.conf:/etc/nginx/conf.d/default.conf --network (nw tag) nginx:1.27.4

- 555 puerto del host
- 80 puerto donde escucha nginx
- __-v__ -> Crear un __volumen__ -> Directorio local (./nginx.conf) mapeado a un directorio virtual (/etc/nginx/conf.d/default.conf)
- nw tag igual al resto de contenedores

! SEÑAL PARA RELEER LA CONFIGURACIÓN -> En el caso de que haya un cambio 


# Teoría 


Decisiones de diseño y Atributos de calidad (clase pasada)

## Performance, Scalability, Availability


__Atributo de calidad__: Propiedad mensurable o testeable del sistema que es utilizada para indicar cuan bien el sistema satisface las necesidades de sus stackholders

__Táctica arquitectural__: Decisión de diseño que influencia la consecución de un atributo de calidad 

## Red conceptual 

- Objetivos del negocio 
- Requerimientos del sistema 
- Propiedades de arquitectura: Funcionales y __Atributos de calidad__ 
- Tácticas : Determinan las relaciones, resposabilidades y roles de los elementos 
- Elementos : Módulos (estáticos) o Componentes/conectores/Datos (Dinámicos)
- Estructuras -> Arquitectura: Conjunto de estructuras
- Vistas: Representación de las estructuras 


### Performance 

![[Pasted image 20250911204021.png]]

Performance tactics:
- Control Resourse Demand -> Sobre la demanda 
- Manage Resource


### Scalability 

Cómo incorporar recursos adicionales de manera __efectiva__

Vertical (__Scale up__) -> Agregar recursos a la unidad física (más memoria, más cpu)

Horizontal (__Scale down__) -> Agregar unidades lógicas (más computadoras)

Tactics:
- Stateless 
- Scale out not up -> Menos costoso y más tolerante a fallos
- Avoid __hard-coded__ resource assumptions or limits 
- Design to be monitored 
	- Identificar servicios caidos 
	- Log files 
	- Evaluar los tiempos de respuesta de los usuarios
	- Auto diagnóstico 
- Async Design 
- Sharding 
- Design for multiple live sites

### Availability

Reparar o encubrir fallas de forma que el periodo fuera de servicio no exceda cierto valor

__Reliability__ -> Grado en que la arquitectura es suceptible a la fallas a nivel de sistema cuando se producen fallas parciales en componentes, conectores o datos

![[Pasted image 20250911212854.png]]

#### Detección de fallas 

- Ping/Echo
- Monitor 
- Heartbeat 
- Timestamp 
- Sanity Checking 
- Condition Monitoring 
- Voting 
- Exception Detection 
- Self-Test 

![[Pasted image 20250911214608.png]]


GUIA DE EJERCICIOS !!

Articulo para leer -> __Who Needs an Architect? - Martin Fowler__