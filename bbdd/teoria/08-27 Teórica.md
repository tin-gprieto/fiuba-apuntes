
## Vinculación de Modelo ER con una BD

Ejemplo: Librería de Jennifer


**Libros**

| Nombre             | ISBN |
| ------------------ | ---- |
| Intro a DB         | 1111 |
| HP: Cáliz de fuego | 2222 |

**Autores**

| Nombre     | Pais | Id. Autor |
| ---------- | ---- | --------- |
| Jk Rowling | UK   | 1         |
| Navathe    | USA  | 2         |
| Elmasri    | CAN  | 3         |

**Relación Libro-Autor**

| ISBN | Id. Autor |
| ---- | --------- |
| 1111 | 2         |
| 1111 | 3         |
| 2222 | 1         |

## Modelo logico-relacional

### Diseño lógico

Entre el modelo conceptual y el modelo interno (Arq. ANSI/SPARC)

_Base de datos relacionales_ (SQL) 

Modelo Relacional: modelo lógico introducido en 1970 basado en el concepto _relación_

#### Definiciones:

- _Dominio_

Conjunto de  valores homogéneos

- _Producto cartesiano_

AXB -> conjunto de pares (a,b) tal que a pertenece a A y b pertenece a B.
- _Relación_

Subconjunto de un producto cartesiano.

- _Esquema de relación_

Nombre de una relación con una lista de atributos

R (A1, A2, .. An)

Ex. Película (nombre, anio, director, cant_oscars)

- _tupla_

Un elemento de Relación

ex. (kill bill, 2003, Tarantino, 0) -> tupla de película
 
*!!!*: No existe dos tuplas distintas que coincidan en los valores de todos sus atributos (son unicas) 

#### Clave natural

- _superclave_: permite identificar

- _clave candidata_: subconjunto minimal de superclaves

- _clave primaria_: clave candidata elegida para ser clave

#### Clave sustituta

Si no se puede conseguir una clave candidata se crea una _clave sustituta_ ("ID") 

_Implementacion_: Incremental o UUID (numero aleatorio demasiado grande)

_Desventaja_: costo de obtención (teórico -> ya es muy eficiente)

_Ventaja_: previene si hay cambios en las _claves naturales_ 


### Esquemas de base de datos relacional

Conjuntos de Esquemas de Relacion

Cine = {Películas, Actores, Actuaciones}

**!!!** Actuaciones: referencias cruzadas (un actor puede tener muchas películas, y una película muchos actores: Cardinalidad N-N)

#### Reglas de integridad:

- _Dominio_: Los valores de atributos de una tupla son homogeneos

- _Unicidad_: Las tuplas son unicas

- _Restricción de integridad de entidad_: La clave primaria de una relación no puede tomar el valor nulo. 

- _Restricción de integridad referencial_: Cuando un conjunto de atributos FK de una relación R hace referencia a la clave primaria de otra relación S, entonces para toda tupla de R debe existir una tupla de S cuya clave primaria sea igual al valor de FK, a menos que todos los atributos de FK sean nulos.

#### *FK*: Clave foránea

Sean R(A1, A2, ..., Ar) y S(B1, B2, ..., Bs) dos esquemas de relación.

FK ⊂ (A1, A2, ..., Ar) hace referencia a S, cuya clave primaria es PK ⊂ (B1, B2, ..., Bs). 

Entonces: 

∀t ∈ R : t[FK] ̸= NULL → ∃s ∈ S : s[PK] = t[FK].

ex. FK: {nombre-pelicula}{nombre-actor}

!= PK (primary key) = {nombre-pelicula, nombre-actor}

## Pasaje de modelo conceptual a modelo relacional

### Operaciones 

#### Consulta 

No modifican ninguna relacion, no tienen restricciones

#### Inserción 

El SGBD debe rechazar la inserción si no cumple con cualquiera de las reglas de integridad

#### Eliminación 

Solo puede afectar la _integridad relacional _

Estrategias: 

- Rechazar la eliminación
- Eliminar en cascada
- Poner NULL en el atributo referencial dentro de la tupla

#### Modificaciones 

- Modificación de _clave primaria_

rechaza si no cumple con todas las Restricciones

- Modificación de _clave foranea_

Rechaza la operación si la modificación no coincide con las referencias


#### Transacción 

Conjunto ordenado de operaciones que deben ejecutarse por completo o no ejecutarse. Si no se ejecutan todas, debe volver al estado anterior.


### Principios para el pasaje

#### Atributo multivariado

Tomar al atributo como una relación -> Crear un esquema de Relacion

Ex. Medico: Nombre, Legajo, TelefonoS, emailS

Medico(Legajo, Nombre)
Telefonos (Legajo, Telefono)
Emails(Legajo, email)

*!!!* Se puede tener medico sin emails o telefonos (pero no telefonos o mails sin medico)
#### Atributo compuestos

Guardar "las hojas" de la composición (subatributos mas simples). Se puede recomponer.

#### Atributo derivado

No almacenarno, calcularlo

(excepción: saldo de cuenta bancaria, requiere demasiado calculo)

#### Interrelación N:M

Alumno aprobó Materia:

Aprobaciones(padrón, cod. materia, fecha)

_FK_: {padrón}{cod. materia} = _PK_

#### Interrelación 1:1

Gerente dirige departamento

Dirige(nombre_gerente, codigo_departamento)

CC (Claves candidatos): {nombre_gerente}{codigo_departamento}
_PK_: {nombre_gerente}
_FK_: {nombre_gerente}{código_departamento}


_Alternativa_ (rara)

Poner todo en un único esquema 

#### Interrelación 0:1

_Estrategia de clave foranea_

Gerente (nombre, teléfono, email, cod. departamento)

Departamento (código, nombre)

(Si o si un gerente dirige un departamento, un departamento puede no tener un gerente)

*!!!* - NO PONER EN AMBOS LADOS la clave foranea

#### Interrelación 1:N

Futbolista juega en club 

(muchos futbolistas juegan en un club, un futbolista juega en un solo club)

Club(nombre, pais, division)
Futbolista(nombre, pais_nacimiento, fecha_nacimiento)

_PK_: {nombre_futbolista}
_FK_: {nombre_futbolista}{nombre_club}


#### Entidades débiles

Estrategia de clave foranea (relación 0:1)

ex. Habitaciones (n_habitacion, nombre_hotel, capacidad)

(depende de Hotel(nombre, dirección))

#### Generalización/especificación


(FALTA)

#### Ternarias

Si o si _tabla de referencia cruzada_

Difícil: **Asignación de clave primaria**