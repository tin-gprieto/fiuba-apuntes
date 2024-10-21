# Diseño Relacional

Miércoles 2/10 -> Clase virtual (grabada)

## Normalizacion

Aplicar reglas/seguir estandares 

Esquema universal 

### Problemas 

- Incapacidad de almacenar ciertos hechos
- Redundancia 

*Solucion* -> Particionar

(Contraproblema: se puede perder informacion al particionar)

"Hechos distintos deben almacenarse en objetos distintos"

### Dependencia funcional

Brindan un conocimiento de como se relaciona la información

Simplificado: Conjunto de informacion que permite conocer otra

(ej. DNI -> Nombre y Apellido )
(ej. Equipo, numero de camiseta -> jugador)

#### Redefiniciones

_Clave_

_Superclave_

### Ejercicio 

Esquema relacional: S(A,B,C,D) 

Conjunto de dependencias funcionales: F:{A->B; B->C}

Utilizando operadores del algebra relacional, escribir una expresión que devuelva como resultados todos los datos de las tuplas de la relación que violen el conjunto de dependencias funcionales F.

Concepto: "Buscar que para un mismo A, haya diferentes B"

Producto cartesiano y seleccionar

sigma B = B2 (sigma A = A1 (A) X B) ???

_Solución_: sigma (A = A1 y B != B1) (S X S)
 
! Identificar dependencias funcionales

Ejemplos: 

Requerimientos y conseguir dependencias funcionales

- Prestamos de libros
- Stock de supermercado
- Goles de jugadores


!!! - Estilo de ejercicio de parcial


### Implicacia de las dependencias funcionales

#### Axiomas de Armstrong (RAT)

- **Reflixibilidad**

Si Y esta incluido en X, se puede infererir X -> Y

- **Aumento**

Si X->Y, entonces XW->YW

- **Transitividad**

Si X->Y e Y->Z, entonces X->Z

#### Clausuras de F

Todas las dependencias no triviales que se puede llegar debido a un conjunto de dependencias

R(A,B,C,D,E), F = {C->E, C->B, B->A, A->D}

F+ = {C->E, C->B, B->A, A->D} U { B->D, C->A, C->D }

_Clausura de un conjunto de atributos_

X_Fx

R(A,B,C,D,E), F = {C->E, C->B, B->A, A->D}

B_Fx = {B} U {A, D}


_Equivalencia de conjuntos de Dependencias Funcionales_

F y G son equivalentes si F+ = G+

#### Cubrimiento minimal

- Todo implidacado (Id) de una df de F+ tiene un único atributo, es decir es _simple_
- Todo determinante (li) de un dg de F+ es _reducido_ si 
- ...

##### Algoritmo de cubrimiento minimal

Paso 1: (!!!)

Paso 2: (!!!)

Paso 3: Eliminar las df's redundantes

df que denotan el resultado de algún axioma


### Ejercicio - cubrir el conjunto minimal

R(A,B,C,D)

F: {CB->A, AD->CB, CD->AB, A->D}

AD -> C

AD -> B

CD -> A

CD -> B 

CB -> A

A -> D

_Seguir algoritmo_

minF = {BC->A, A->C, CD->B, A->D}

### Algoritmo de calculo de claves 1

_Paso 1_: Calcular el cubrimiento minimal de DF. 

Conjunto de atributos para el calculo = Ca = R

_Paso 2_: Detectar atributos independientes del calculo Ai (Aquellos que no están en ninguna Df), eliminar del conjunto.

Ca - Ai, y reservar para después.

_Paso 3_: Eliminar atributos equivalentes (dejar solo uno)
Ae= Atributos equivalentes

(ej. de equivalente: A->B, B->A)

Ca=Ca-Ae (Reservarlos para otro paso)

Se reemplazan en la Df por el/los atributos equivalentes que se conservan en CA

_Paso 4_: Se forma K con todos los elementos implicantes Ai, se calcula K+ si es solo R => K es clave. (solo lado izquierdo)

_Paso 5_: Si K no resulto clave, se (...) -> Ciclar

_Paso 6_: Agregar los elementos independientes (Ai)

_Paso 7_: Calculo el resto de claves con los equivalentes (Ae)


--- 
Ejercicio 

R(A,B,C,D,E,F,G,H)
Sm = {A->C, A->F, CF->A, CF->H, H->D, H->E, H->G, BCG->D, D->B}

Ai = {}

A -> CF por lo tanto CF = A
Ae = {CF}

Sm = {A->C, A->F, A->H, H->D, H->E, H->G, BCG->D, D->B}

K = {A, BCG}
Aid = {ABCDFGH} (todas menos E)

{A} -> {A, B, C, D, E, H, F, G}
{CF}

_Son claves_




