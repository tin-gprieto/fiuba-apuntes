

## ¿Qué es la arquitectura de software?


 ### Martin Fowler 

1. La descompiscioón de más alto nivel de un sistema en sus partes fundamentales
2. Conjunto de decisiones de diseño que son dificiles de cambiar

### ISO-IEC-IEEE 42010

"Conceptos o propiedades fundamentales de un sistema en su entorno, comprendido por sus elementos, relaciones y principios de su diseño y evolución"

### Roy Fielding -> web

"Abstracción de los elementos de tiempo de ejecución (__Run-time elements__ ) de un sistema de software durante alguna fase de operación"

"Un sistema puede tener muchos _niveles de abstracción_ y muchas fases de operación"

### Robert Martin -> "Clean Architecture", 2017

"Es la forma dada al sistema por quienes lo construyen"

Esa forma está determinada por la división en componentes y las maneras en que pueden comunicarse entre ellos.

El propósito de esa forma es facilitar el desarrollo, despliegue, operación y mantenimiento del sistema.

La estrategia es dejar tantas opciones abiertas como sea posible, por el máximo tiempo posible.

### (!) Software Engineering Institute (SEI)

"Conjunto de _estructuras_ necesarias para razonar sobre el sistema que constan de _elementos_ de software, _relaciones_ entre ellos y _propiedades_"

_Estructura_ : Conjuntos de elementos unidos por una relación

_Elementos_ : Módulos (estáticos) y componentes (dinánimos)

## Tipos de estructuras:

Representación de __procesos (componentes)__ vs representación de __módulos__ -> Estructura 

### Módulos
__Estaticas__ (Unidades de implementación)
- Descomposición
- Clases 
- Uses

### Componentes - Conectores (C&C) 
__Dinámicas__ (Elementos de run-time)
- Procesos
- Client-Server
- Concurrencia

### Asignación (Allocation)

- Despliegue
- Implementación
- Desarrollo

## Vistas de la arquitectura

"Diseñamos estructuras y documentamos _vistas_ de estas estructuras" -> Método de ___representación___

La arquitectura es una abstracción


## Arquitectura y Negocio 

- Objetivos a cumplir por el negocio con el software
- Requerimientos del sistema

¿Cómo se vinculan estos elementos con la arquitectura?

(Próxima clase) Elementos que ayuden a unir ambos mundos

## Atributos de Calidad y Tácticas






























































































