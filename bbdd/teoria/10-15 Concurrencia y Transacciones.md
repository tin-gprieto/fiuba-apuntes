
## Transacciones

### Propiedades ACID 

- _Atomicidad_
- _Consistencia_
- _Aislamiento_
- _Durabilidad_

### Mecanismos de recuperación 

_begin_

_commit_

_abort_

## Anomalías 

### Lectura sucia (dirty read)

### Lectura no repetible (unrepeatable read)

### Escritura sucia (dirty write)

### Fantasma (Phantom)


## Serializabilidad 

_Solapamiento_:

_Solapamiento serializable_:

### Grafo de precedencias


## Control de Concurrencia

### Control basado en locks 

Enfoque _pesimista_: Busca garantiza que no se produzcan conflictos

El SGBD utiliza locks para bloquear a los recursos -> Son insertados por el SGBD, no hay una instrucción para utilizarlos.

Resuelve el problema de la _exclusion mutua_

_Locks de escritura_ / _Locks de lectura_

_Deadlock_: un conjunto de transacciones quedan bloqueadas a la espera de recursos que otra de ellas posee 

_Inanición_: Una transacción no logra ejecutarse por un periodo de tiempo indefinido 

_Index locks_ 

#### Protocolo de lock de dos fases (2PL)


### Control basado en timestamps

Enfoque _optimista_: "Deja hacer" transacciones y deshace (rollback) si descubre un conflicto en la fase de validación.

Se asigna un timestamp a cada transacción Ti

Esta determina el orden serial respecto al cual el solapamiento deberá ser equivalente.

- Cuando una transacción Ti quiere ejecutar un R(X):
	- Si una transacción posterior Tj modifico el item, Ti deberá ser abortada (_read too late_)
	- De lo contrario, actualiza _read_TS(X)_
- Cuando una transacción Ti quiere ejecutar un W(x):
	- Si una transacción posterior Tj leyó o escribió el item, Ti deberá ser abortada (_write too late_)
	- De lo contrario, actualiza _write_TS(X)_


### Snapshot isolation 

Cada base de datos visualiza un _snapshot_ correspondiente al instante de su inicio.

Ventajas: mayor solapamiento
Desventajas: 
- Requiere de mayor espacio en disco o memoria porque tiene que mantener muchas versiones de los mismos items
- Ocurren conflictos de WW


## Niveles de aislamiento

	SET TRANSACTION INSOLATION LEVEL 
	READ UNCOMMITED | READ COMMITED | REAPEATABLE READ | SERIALIZABLE

Serializable: evita todas las anomalías

_Dirty write_: NUNCA DEBE OCURRIR






