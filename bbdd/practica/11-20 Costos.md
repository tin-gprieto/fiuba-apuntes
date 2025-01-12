
Optimizar la memoria utilizada en las consultas

Quien se encarga? El sistema de gestión de base de datos

## Objetivos

- Comprender como se realizan eficientemente las consultas
- Estimar costos operativos

## Procedimiento

SQL (Declarativo) -> Parsear y traducir -> Expresion de algebra relacional (Imperativo)

Optimizar expresión de AR -> _Plan de ejecucion_

Optimizar => _ACCESO A DISCO_ (muy costoso)

SQL -> Declarativo (Que es lo que quiero, sin saber como se hace)
	!= Imperativo 
	!= Funcional

## Indices

### Indice de Clustering

Sobre campos de ordenamiento del archivo fisico pero no es clave

_Indice primario_: Indice de clustering sobre el campo de clave primaria


### Indice secundarios

Sobre campos que no son de ordenamiento 


## Operadores 

![[Pasted image 20241120194302.png]]

Del algebra relacional: 

### Selección  

Sin indice -> Búsqueda secuencial (lectura total del archivo) = B(R)

Con indice de clustering -> Height(I(A;R)) + [B(R) / V(A,R)]

Con indice secundario -> Height(I(A;R)) + [n(R) / V(A,R)]

n(R) =  Cant. de tuplas

V(A,R) : Variabilidad 

Con indice  primario -> Height(I(A;R)) + 1

#### Selecciones complejas 

_Conjuncion_ / _Disyuncion_

### Proyección 

La proyeccion en algebra elimina los repetidos (en SQL solo si se dice DISTINCT)

1. Si es superclave: B(R) todo el archivo
2. Si no es SK -> Hay que eliminar duplicados
	1. Se ordena (2.B(R).[logM-1(B(R))] - B(R)
	2. Hashearlo (B(R) + 2 (B^PiX(R))

### Operaciones de conjunto

#### Union e intersección

### Join 

Diferentes métodos:
- Loops anidados por bloque
- Único loop
- Sort-merge
- Junta hash

#### Loops anidados por bloque

- Por cada bloque de R se lee todos los bloques de S (o viceversa):
- cost(R * S) = min(B(R) + B(R) ⋅ B(S); B(S) + B(R) ⋅ B(S))

Ejercicio:

Multas
B(m) = 400
n(m) = 1600

Propetarios-Matriculas
B(p)=50
n(p)=150


min (50 + 50 * 400; 400 + 50 * 400) = 2050

Con M como # matriculas joineadas, calcular el costo para:
- M=2:
- M=11:
- M=51:

#### Único loop

Conviene tener un indice de clustering sobre la tabla de Matriculas

▪ Si el índice es _primario_, el costo será: 
	cost(R S) = B(S) + n(S) ⋅ (Height(I(A,R)) + 1) 

▪ Si el índice es de _clustering_, puede haber más de una coincidencia: 
	cost(RS) = B(S) + n(S) ⋅ (Height(I(A;R)) + [ n(R) / (V(A,R) ⋅ F(R)) ] 

▪ Si el índice es _secundario_: 
	cost(R S) = B(S) + n(S) ⋅ (Height(I(A;R)) + [ n(R) / V(A,R) ]

Mismo datos: 

_!_ Como calcular _V(A,R)_: variabilidad y _F(R)_: frecuencia

Altura de indice = 4

1. Que indice necesito para aplicar el mismo
2. Calcular costos con indice de clustering y con secundario
	1. 

