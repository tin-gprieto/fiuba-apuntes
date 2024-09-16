## SQL

Structured Query Language (1979-Oracle)

Es _declarativo_ != procedural (algebra relacional)

Se basa en el calculo de tuplas

CORE -> ISO/IEC 9075-2 / 11

SQL es abierto pero no gratuito

## Definición de datos -- DDL (Data Definition Language)

### CREATE SCHEMAS

### CREATE TABLE 

! Definir siempre un PK

(columna1 _tipo de dato_ [RESTRICCIONES], ...)

#### Tipo de dato

- Numérico
- String
- Date/Time 
- BOOLEAN
- CLOB/BLOB (archivos) 
- UUID (Clave sustituta)

#### Restricciones 

- NULL o NOT NULL
- UNIQUE 
- DEFAULT (value)
- CHECK (condition)
- PRIMARY KEY 
- FOREIGN KEY (key_name) REFERENCES table_name(key_column)
	- ON DELETE / ON UPDATE SET
	- NULL | RESTRICT | CASCADE | 

#### Claves sustitutas

Depende del SGBD

PostgresSQL -> SERIAL y BIGSERIAL (4B y 8B respectivamente)

### ALTER TABLE

ADD COLUMN

RENAME COLUMN

### DROP TABLE

### INDEX 

Sirve para agilizar consultas

CREATE INDEX (name) ON (table)

## Manipulacion de dato -- DML (Data Manipulation Language)

### SELECT 

SELECT (columna1, ...) FROM (tabla1, ...) WHERE (condition)
        _proyección_        _tabla1 X ..._      _selección_

! - DISTINCT no se devuelven filas repetidas 

(x default no se comporta como algebra relacional)


### IS NULL / IS NOT NULL

No funciona con = o <>, solo con IS o IS not

### Conversion de datos

- to_char ()
- EXTRACT (DAY FROM date)
- CAST ( codigo AS CHAR)
- Numericas: ABS, ROUND, TRUNC, LN, LOG, EXP, SQRT
- Strings: UPPER, LOWER,

### LIKE 

Parecido a _grep_

(ILIKE -> case sensitive)

### CASE

Parecido a _if_

CASE WHEN (condition) THEN value1 END

### WHERE 

Selección por condición
### AS

Alias para renombrar tablas

### ORDER BY

Ordenamiento

### FETCH FIRST 

FETCH FIRST (n) ROWS ONLY

### OFFSET 

Paginado 

OFFSET (filas_saltear) ROWS


### JOINS

![[Pasted image 20240911203713.jpg]]
#### INNER JOIN / JOIN

FROM (table1) INNER JOIN (table2) ON (condition)
FROM (table1) INNER JOIN (table2) USING (column) -- columnas de mismo nombre

...


### Conjuntos  


![[Pasted image 20240910205509.png]]


### Consultas Anidadas

- Utilizar queries como tablas

#### Operadores 

_ANY/SOME - ALL_
	WHERE padrón = ANY (SELECT )

_IN_
	 Similar a un OR

_EXIST_

### Agregación

_MAX / MIN_

_SUM / AVG_

_COUNT
- *  Cantidad de filas
- (column) Cantidad de filas con dicha column distinta de NULL
- (DISTINCT column)