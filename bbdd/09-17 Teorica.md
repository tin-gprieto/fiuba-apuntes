
## Repasar 

- GROUP BY 
	- HAVING != WHERE
- JOINS
- Operaciones de conjuntos 

## ABM

### INSERT

INSERT INTO (table) VALES (values)

INSERT INTO (table) SELECT (consulta)

### UPDATE

UPDATE (table) SET columna1 = expresion1
[, columna2 = expresion2]
[WHERE ...]

### DELETE

DELETE FROM (table) WHERE (condition) (!!!)

### TRANSACCIONES

BEGIN TRANSACTION; [F5]
(comando) [F5]
...
COMMIT;  <- Recién impacta cuando se ejecute [F5]


## Vistas 

Es una tabla _virtual_. Sus datos surgen como una consulta a una o mas tablas

	CREATE VIEW (nombre de vista)
	[(columna1, columna2,..., columnaN)]
	AS consulta_SQL

### Uso  

- Seguridad
- Reducción de complejidad (atajo para una consulta)
- Cambios de representación de datos (usar versiones viejas)

### Actualización de datos

Algunos motores no dejan actualizar.

Otros motores tiene restricciones:

- Solo una tabla del FROM 
- No usa operaciones de conjunto, ni de agrupamiento
- No limita la cantidad de resultados

_WITH CHECK OPTION_

No deja actualizar datos que no se incluyan en la condición de la vista.

(No deja agregar una nota menor a 4 en una vista de notas_aprobadas)

## WITH y WITH RECURSIVE


_Common Table Expression_

Usar con cuidado - uso Opcional

Se utiliza como una subconsulta auxiliar a utilizar en una consulta

Evita el copy/paste de consultas

~ create VIEW

	WITH (alias1) AS (subconsulta)
	consulta_principal

Ex.

WITH aprobados AS  (SELECT * FROM notas WHERE notas.nota >= 4)
SELECT *
FROM aprobados 
...


### WITH RECURSIVE

Subconsulta que se referencia así misma hasta que no haya nuevos resultados

ex. Escalas de vuelos

## DCL - Data Control Language

- No accede a todas las tablas
- No accede a todas las columnas
- No accede a todas las filas

- Acceso -> Lectura o Edición -> Roles 

### CREATE USER 

	CREATE USER (name) WITH PASSWORD (pssw)
	CREATE USER (name) WITH LOGIN PASSWORD (pssw)


### CREATE ROLE

	CREATE ROLE (nombre_role)

### GRANT 

Alta

	GRANT (nombre_rol) TO (user_name)

	GRANT privilegio1, (...) (SELECT, DELETE, INSERT...) ON (table) TO nombre_rol

### REVOKE

Baja

	REVOKE (nombre_rol) FROM (user_name)


Uso de _vistas_ para restringir acceso


## SQL avanzados

- Stored Procedures y Triggers
- Funciones de ventanas
- Vistas materializadas (se crea como tabla)
- EXPLAIN - plan de ejecución de una consulta -> Problemas de performance 
- Tipos de dato y funciones custom 
- Uso de JSON y XML (!!! - BPBA)


## Valores NULOS 

NULL -> Desconocido (no admite operaciones)

### Problemas 

#### Consultas negativas 

Ex. Alumnos que no se recibieron de tal colegio -> NULL ???

Para que las consultas sean complementarias:

	OR nombre_colegio IS NULL

_COALESCE_

Reemplaza el valor nulo

Ex.

	SELECT padron, COALESE(nombre_colegio, "SIN_COLEGIO")

#### Funciones de Agregación

Son ignorados -> Ex. AVG()

#### Ordenamiento

NULL -> menor de los valores (por defecto)

_NULLS LAST_

#### NOT IN

Ex. Encontrar los colegios sin egresados

Alumnos -> (ORT, ILSE, NULL)
Instituciones -> (ORT, ILSE, CNBA)

Resultado -> NULL

(7) Repasar -> Lo interpreta como desconocido -> Explicitar como interpreta el NULL

#### COUNT( * ) de filas con valores nulos








