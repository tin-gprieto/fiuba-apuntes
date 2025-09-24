

1. Casos de uso
2. Usuario 
3. Como se procesan los datos
4. Como se almacenan
# Web Crawler 

Casos de uso:
- CU1: Analizar la URL que se pasa 
- CU2: Obtener los documentos 
- CU3: Obtener multimedia
- CU4: Monitorear constantemente sobre un archivo de texto 

Boundaring (entrada/salida del sistema distribuido) - Control (computo) - Entity (Informacion persistente - Almacenamiento)  


# Shopping Cart


Orden de compra con varios productos -> Varios productos y solo se puede hacer si estan todos 

Transaccion atomica 

Robuztez:

__Request handler__ 
	-> Divide el pedido por producto y manda esa informacion al nodo correspondiente
	-> Guarda en el storage de transacciones el pedido realizado -> IN PROGRESS

__Nodo por producto__
	-> Maneja el stock de un solo producto, recibe el request y corrobora si tiene stock y resta la cantidad del pedido. Envia esa informacion al joiner y espera su respuesta para ver si necesita volver atras con el stock
	-> Replicacion en varios nodos -> Se divide la data y hay un nodo coordinador que sabe la disponibilidad de cada nodo (pseudo load balancer)

__Joiner__ 
	-> Recibe el request y espera a que cada nodo le mande el OK de stock en cada producto
	-> Si recibe todos los OK, les devuelve una respuesta para que impacte en el stock y actulaiza el storage de transacciones para avisarle al usuario

Casos de uso:
- CU1: Cliente quiere comprar un producto 
- CU2: Administrador ingresa productos al stock
