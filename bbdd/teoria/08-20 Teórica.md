## Introduccion

### Introducción a base de datos

Que es una base de datos? 

Es mas abarcativo que un sistema.(ej. fichero)

Datos: representacion de la información

"Conjunto de datos interrelacionados"

Dato: hecho que puede ser representado y almacenado que tiene un sentido implícito

Predicado: función que toma uno o as argumentos que devuelven un valor de verdad

*Base de datos no tradicionales*: tipos de datos particulares/avanzados

### Sistema de gestión de bases de datos (SGBD)

Conjunto de programas o software que gestiona y controla la creación, manipulación y acceso a la base de datos. Proporciona una abstracción de los programas para simplificar su utilización.


*Independencia de datos*: El cambio en su estructura no repercute en el funcionamiento de los programas que componen el SGBD


### Arquitectura de 3 capas ANSI/SCPARC

1. Nivel externo (vistas): como los usuarios utilizan los datos
2. Nivel conceptual: semántica de los datos
3. Nivel interno: implementacion física

### Funciones de un SGBD

1. Buscar, consultar, filtrar (_Almacenamiento y consulta_)
2. ABM (Alta, baja, modificar)
3. Proteger los datos: Quien accede a los datos (_Seguridad_)
4. _Recuperación_ ante una falla 
5. Restricciones (ej. id únicos) (_Integridad_)
7. _Concurrencia_ (Acceso simultaneo) 
8. Triggers (logica que se ejecuta ante cierto evento)
9. _Soporte transaccional_: Conjunto de operaciones que se realizan en su totalidad

## Diseño Conceptual

#### Modelo de datos

- Conjunto de objetos con propiedades e interrelaciones entre ellos que representa la estructura
- Conjunto de operaciones para manipular los datos
- Restricciones de los objetos
## Modelo Entidad-Interrelacion

Entidades, Interrelaciones y atributos

_relatioship_: Interrelacion != modelo relacional

### Definiciones

_Tipo de entidad_: tipo o clase de objeto en particular
	_Entidad_: instancia de un tipo de entidad

ej. Futbolista, país

_Atributo_: Propiedad que describe a la entidad

ej. Posición(futbolista), Población(país)

_Tipo de interrelación_: Conjunto de relaciones o asociaciones entre dos o mas tipos de entidades

ej. **Didier Drogba** nació en **Costa de marfil**
	(futbolista)     ->        (país)

#### Diagramas

![[Pasted image 20240820194953.png]]

#### Valor nulo

NULL: Valor desconocido o ausente para la propiedad de una entidad (ej. Futbolista sin cotización)

#### Atributos compuestos (!= simple)

Descomposición en sub-atributos

![[Pasted image 20240820195655.png]]

#### Atributos multivaluados vs Monovaluados

Mas de un valor en un mismo atributo (ej. Numeros de telefo de una misma persona (entidad))

#### Atributo derivado (!= almacenado)

Puede calcularse en base al valor de otro atributo

(ej. edad a partir de fecha de nacimiento)

![[Pasted image 20240820200235.png]]

#### Conjunto de entidades

Conjunto de instancias de un mismo tipo de entidad en un momento dado de la base de datos

#### Atributo clave o identificadores únicos

Necesariamente distinto entre cada una de las identidades.

Si no existe se debe crear uno -> ID 

Debe ser un conjunto minimal.

![[Pasted image 20240820201101.png]]

(SSN key)

### Interrelaciones

#### Binarias

_Cardinalidad_ 

Cantidades posibles en la relación

1:1, 1:N, N:1, M:N

(N: "muchos")

_Participación_: minima cantidad de instancias (un futbolista necesariamente nació en un país)

_Participación total o dependencia existencial_: se requiere de cierta instancia con relación para subsistir.

! _Relaciones estructurales_: cardinalidad + participación
	_Restricciones_: ej. (1,N) = (min, max)

(GRÁFICO PARA ENTENDER CUAL SE REFIERE A CUAL)

#### Atributos

ej.

relación: aprobar (alumno -> materia)
atributo: fecha

_Atributos clave_: la clave del vinculo puede ser algun atributo clave de las entidades que lo componen. DEPENDE DE LA cardinalidad

1:1 - Puede ser cualquiera

1:N o N:1 - La clave es del atributo muchos (Clave N)
(1 autor - N libros: clave de interrelacion=clave del libro)

M:N - La clave es ambos {Clave de M, Clave de N}


### Ejemplo: Librería "Jennifer"

! Por que genero es una entidad y no un atributo -> DEPENDE 

No hay una sola forma de modelar


#### Vinculo recursivos o unarios

Interrelaciones entre entidades del mismo tipo

### Entidades fuertes vs débiles

La débil depende de otra para poder ser identificado


![[Pasted image 20240820211227.jpg]]


_Discriminante_: Payment number

Clave de entidad debil: Clave enditidad fuerte + discriminante

### Interrelaciones n-arias

Cuando participan 3 o mas tipos de entidades distintos

cantande - puntua - ronda
             -
           jurado

! Como determinar cardinalidades

Minimo: casi siempre 0

Contras: siempre tienen que participar todas las entidades

SOLUCION;
### Agregacion

(Agregacion: cantante - participa en - ronda) - puntua -jurado

### Generalizacion y especificacion

Relacion: es un (categoria)

Clave del supertipo


