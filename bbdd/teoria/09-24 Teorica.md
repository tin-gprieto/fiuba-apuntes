# Diseño relacional


### Criterios de buen diseno relacional
- Perservacion de la información
	- No se pierde información, si en una relación contiene la clave de algunas de las entidades de la misma (repasar)
- Redundancia minima
	- No repetir información que pueda generar problemas de agregación o eliminación -> abstraer en una nueva entidad

### Dependencias funcionales

_Dependencia funcional_:

_Dependencia trivial o no trivial_:
### Formas normales - Tipos de redundancias
#### 1FN

Condición: Los atributos solo permiten valores atómicos (indivisibles) y mono-valuados

#### 2FN

_Atributo primo_: Es parte de alguna clave candidata de la relación

Condición: Cuando todos los atributos no primos tienen dependencia _funcional completa_ de las claves candidatas

(!= dependencia funcional parcial: { A B D } -> C, se puede determinar C con AB, AD, BD, por ejemplo)

_Descomposición_:

_Relación universal_: R(A1,..., An) 

#### 3FN

_Dependencia transitiva_: 

Condición: No hay dependencias transitivas

#### FNBC

Se puede perder dependencias funcionales al arreglarlo

#### 4FN - 5FN

No se evaluan - AFUERA