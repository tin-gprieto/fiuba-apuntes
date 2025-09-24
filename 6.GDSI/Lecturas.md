
# User Story Mapping

# Estimaciones e indicadores

## Video de la cátedra 

Para administrar el alcance, tiempo y costos necesitamos:
- Estimaciones previas _para planificar_
- Indicadores que nos permitan hacer _seguimiento y control_

### Estimación 

"predicción acerca de la duración o costo de una actividad"

__Objetivo__ -> Enunciación de un logro deseable para el negocio -> No siempre se puede cumplir

__Compromiso__ -> Promesa de entregar una funcionalidad definida con una calidad determinada en una fecha dada

__Información previa__ ! -> Requerimientos funcionales, exigencias en tiempos de entrega 

Manejar las __expectativas__ del cliente -> Acuerdo de ambas partes -> Entre tiempo y alcance

Naturaleza __probabilistica__ de las estimaciones -> __NO ES EXACTA__ -> Rangos

![[Pasted image 20250924114342.png]]

Ejemplo: 
- entre 8 a 16 semanas ocupa el mayor volumen de la distribución _normal_
- el valor medio, es decir 12 semanas, tiene un 50% de probabilidad -> Asumir riesgos 

Otras distribuciones __más realistas__

![[Pasted image 20250924114814.png]]

Todo proyecto implica __INCERTIDUMBRE__ debido a riesgos, desconocimientos o deslizamiento del alcance -> COMUNICAR LA INCERTIDUMBRE AL CLIENTE (ej: Expresar el rango o probabilidades)

A medida que avanza el proyecto, se puede ir __midiendo__ (indicadores), se conoce mejor el __alcance__ real por parte del cliente o se materializan (o no) los __riesgos__ -> Afinando la estimación realizada (_más precisa_)

![[Pasted image 20250924120040.png]]

## NoEstimates - Allen Holub

Nunca vas a saber el costo de algo que nunca implementaste 

Dificultad de expresar probabilidades -> La gente no lo entiende realmente

__Disfuncionalidades__ dentro del negocio:
- Mal asignación de recursos -> Gastar tiempo en cosas no importantes
- Sobreexplotación de los developers
- Toma de decisiones sobre información inexacta


__Chaos report__ -> 80% de los proyectos se demoran o fracasan 

No se sabe estimar

Se implementan cosas inútiles para llegar con los tiempos estimados

__Story points__ -> Manera de estimar -> Poner un puntaje de dificultad sobre las US => Disfuncional -> Se vuelve a hablar de tiempo y por ende es una estimación


__Velocidad__ -> Tiempo idear / tiempo actual 


__Backlog__ -> 10% de US correctas - 30% van a cambiar de acuerdo a los que se aprenda en el proyecto - 60% son fantasía

Por esto, estimar en base a las US del Backlog es inútiles

### Lean manufacturing

Sistema de producción toyotista -> Empoderamiento del trabajador para estimar su propio tiempo -> DEJAN de estimar (la estimación es una obligación de los jefes)

=> Developers control time -> Nadie te obliga a seguir tiempos o mantener cierta planificación => Los managers dejan de tener utilidad -> Horizontalidad de la organización

![[Pasted image 20250924132153.png]]
Los managers empiezan a tener otro rol -> Quitar todos los obstaculos para trabajar -> Ayudar a los developers (support)


Objetivo de Lean -> Eliminar desperdicio -> Si no aporta valor al consumidor, es un desperdicio => __LA ESTIMACIÓN ES DESPERDICIO __

### Accurate proyections

Decisiones 
-> Se debe matar el proyecto?
-> Se debe sumar más gente?


NoEstimates -  Vasco Duarte  

Proyecciones en base al _conteo de US_ -> __ES SUFICIENTE__

![[Pasted image 20250924133134.png]]


### Priorizar

Mejor forma de planificar -> __User Story Map__

Permite 2 dimensiones de tiempo y prioridad

Permite definir un MVP y diferentes releases 

No es un documento estático


# # An Introduction to Planning Poker By Bob Hartman


Consensuar el peso de las user stories con el PO (Product Owner) y el equipo de desarrollo.

1. Cada participante tiene cartas en una secuencia de números. Potencia de dos (0, 0.5, 1, 2, 4, 8, 16,...) o fibonacci (1,2,3,5,13,21,...).
2. El moderador presenta una US
3. El PO responde preguntas al respecto de la US
4. Cada participante selecciona una carta que represente el peso (complejidad, riesgo, tamano, u otros factores) 
5. Todos muestran su carta a la vez
6. Si hay consenso se avanza, sino el de menor y mayor peso explican sus argumentos
7. Se vuelve a tirar las cartas como en el paso 4 y 5 hasta llegar al consenso (max 3 vueltas)
8. Se llega al consenso del peso de la carta (o se elige el mayor peso si se lega a las 3 vueltas)
9. Se repite para todas el resto de US


Beneficios:
- Colabora todo el equipo
- Se genera en base al consenso y no al criterio de una única persona 
- Se exponen problemas prematuramente en el debate

Supuestos:
- Solo votan los que van a participar del proyecto
- Los managers no votan -> Tienden a pensar que las cosas toman menos tiempo. Pueden tener veto en caso de que consideren que deba aumentarse el peso 
- Si no hay consenso entre dos pesos, se elige el más pesado 
- Parar las discusiones sobre implementación si se vuelven muy largas o profundas. Discusiones de no más de un minuto 
- Limitar la duración de la reunión para determinar los pesos. Hacer recreos en el medio 


# _Software Estimation: Demystifying the Black Art_ – Steve McConnell

### Resumen general

El libro aborda la problemática de la estimación en proyectos de software, una actividad muchas veces mal entendida o confundida con compromisos y metas. McConnell explica que una buena estimación no es una predicción exacta, sino una herramienta para tomar decisiones informadas, gestionar riesgos y alinear expectativas. Presenta técnicas, buenas prácticas y principios para mejorar la precisión y utilidad de las estimaciones. Concluye que el verdadero valor de la estimación es ayudar a controlar proyectos, no a prometer milagros.

### Conclusiones principales

- Una **estimación** no es lo mismo que un **compromiso** ni que un **objetivo de negocio**.
    
- Las estimaciones siempre llevan asociada una **incertidumbre y probabilidad**.
    
- La clave no es la precisión absoluta, sino su **utilidad para la gestión del proyecto**.
    
- Se debe basar en datos históricos, descomposición de tareas y métodos estructurados.
    
- Las organizaciones maduras logran altos niveles de cumplimiento gracias a estimaciones realistas más control de proyectos.
    

### Contenido por capítulos (breve)

- **Cap. 1: ¿Qué es una estimación?**  
    Explica la diferencia entre estimación, compromiso y meta. Introduce la noción de estimaciones como declaraciones de probabilidad y no de certeza.
    
- **Cap. 2–4: Errores comunes y la “Cono de Incertidumbre”**  
    Muestra las fuentes típicas de error (optimismo injustificado, requisitos inestables, políticas internas). Introduce el _Cone of Uncertainty_ para mostrar cómo la precisión mejora a medida que avanza el proyecto.
    
- **Cap. 5–10: Influencias y factores en la estimación**  
    Factores de productividad, tamaño del software, complejidad, experiencia del equipo y lenguaje de programación.
    
- **Cap. 11–16: Técnicas de estimación**  
    Métodos como descomposición (_work breakdown structure_), analogía con proyectos anteriores, juicio experto, Wideband Delphi, puntos de función, líneas de código, y técnicas proxy como _story points_ o _t-shirt sizing_.
    
- **Cap. 17–20: Uso combinado de métodos y herramientas**  
    Recomienda usar múltiples enfoques en paralelo, calibrar con datos históricos y apoyarse en herramientas automatizadas (COCOMO, Construx Estimate, etc.).
    
- **Cap. 21–24: Reestimación, negociación y comunicación**  
    La estimación debe revisarse durante todo el ciclo. Se enfatiza la importancia de comunicar claramente supuestos, rangos y probabilidades, además de separar estimaciones de compromisos.
    
- **Cap. 25: Rol real de la estimación**  
    Concluye que el objetivo principal es decidir si las metas del negocio son realistas y, si no lo son, renegociar alcance, costos o tiempos. Una buena estimación es la que permite tomar decisiones correctas de gestión.
    

---

# _Stop Promising Miracles_ – Karl Wiegers

### Resumen general

El artículo de Wiegers critica la tendencia de las organizaciones a hacer estimaciones poco realistas y “prometer milagros” en plazos y costos. Presenta el método **Wideband Delphi** como una técnica estructurada y colaborativa para mejorar la exactitud, reducir sesgos y aumentar el compromiso del equipo. Concluye que, aunque no existe un método perfecto, Wideband Delphi ofrece un enfoque práctico y confiable que refleja la incertidumbre inherente a la estimación.

### Conclusiones principales

- La mayoría de los profesionales de software no reciben entrenamiento en estimación.
    
- Se subestiman tareas, no se incluyen buffers y se olvida trabajo esencial.
    
- Wideband Delphi mejora resultados al combinar múltiples perspectivas, iterar, y reflejar la variabilidad con rangos en lugar de un único número.
    
- El resultado no debe ser una “respuesta mágica” sino un **rango probabilístico** que apoye decisiones realistas.
    

### Estructura del artículo (secciones principales)

- **Problema de las estimaciones tradicionales**  
    Falta de entrenamiento, exceso de optimismo, omisión de tareas y riesgos.
    
- **Método Delphi y evolución a Wideband Delphi**  
    Origen en RAND, adaptación por Boehm, y perfeccionamiento posterior.
    
- **Proceso de Wideband Delphi**  
    Incluye planificación, reunión de arranque, preparación individual, reunión de estimación en rondas, consolidación de resultados y revisión final.
    
- **Ventajas**  
    Más tareas identificadas, menos sesgo, anonimato que evita presiones políticas, mayor compromiso del equipo.
    
- **Evaluación final**  
    Wideband Delphi no es infalible, pero ayuda a reemplazar promesas imposibles por estimaciones útiles y consensuadas.

### Pasos de **Wideband Delphi**

1. **Planificación**
    
    - Se define el problema a estimar, se eligen participantes y se preparan materiales.
        
2. **Kickoff meeting (reunión inicial)**
    
    - Se explica el método, se entrega la especificación del problema y se acuerdan unidades de estimación.
        
3. **Preparación individual**
    
    - Cada estimador arma su lista de tareas y sus estimaciones de manera independiente y anónima.
        
4. **Reunión de estimación**
    
    - Se comparten listas y supuestos.
        
    - Se combinan en una lista común.
        
    - Se realizan rondas de estimación ajustando valores tras discutir diferencias.
        
5. **Consolidación**
    
    - El moderador o PM unifica tareas y estimaciones en un listado maestro con rangos.
        
6. **Reunión de revisión final**
    
    - El equipo valida la lista final, supuestos y rangos de estimación.
        
    - Se alcanza consenso y se documenta el resultado.
# Conceptos Claves de Estimación de Software

### 1. **Estimación**

Proceso de predecir el esfuerzo, costo, tamaño o duración de un proyecto de software, expresado normalmente como un rango probabilístico y no como un único número fijo.

### 2. **Meta (Target)**

Objetivo de negocio deseado, como una fecha límite o presupuesto, que puede no coincidir con la estimación realista del proyecto.

### 3. **Compromiso (Commitment)**

Promesa de entregar cierta funcionalidad en un plazo y con una calidad específica. Puede ser igual, más agresivo o más conservador que la estimación.

### 4. **Planificación vs. Estimación**

- **Estimación**: análisis imparcial para aproximar costos/tiempos.
    
- **Planificación**: proceso sesgado hacia cumplir un objetivo (se ajusta el alcance, recursos o prioridades).
    

### 5. **Cono de Incertidumbre (Cone of Uncertainty)**

Modelo que muestra cómo la precisión de las estimaciones mejora progresivamente a medida que el proyecto avanza y se reducen las incógnitas.

### 6. **Estimación de un solo punto**

Un único valor (ej. “14 semanas”), que suele ser engañoso porque no refleja la probabilidad ni el rango de incertidumbre.

### 7. **Estimación por rango**

Expresada como intervalo (ej. “18 a 24 semanas”), comunica la variabilidad esperada y ofrece información más realista.

### 8. **Juicio experto**

Método basado en la experiencia personal de profesionales para estimar, aunque sujeto a sesgos y optimismo excesivo.

### 9. **Delphi / Wideband Delphi**

Técnica colaborativa de estimación en la que varios expertos producen estimaciones de manera anónima y, tras rondas iterativas de discusión y ajuste, convergen hacia un rango de valores más realista.

### 10. **Descomposición (Work Breakdown Structure, WBS)**

División del proyecto en tareas más pequeñas y manejables para facilitar la estimación bottom-up.

### 11. **Puntos de función (Function Points)**

Medida de tamaño funcional del software basada en entradas, salidas, consultas, archivos y otros componentes, independiente del lenguaje de programación.

### 12. **Story Points / T-shirt sizing**

Técnicas ágiles de estimación por analogía que asignan un tamaño relativo a las funcionalidades, evitando medir directamente en tiempo o esfuerzo.

### 13. **Buffers de contingencia**

Margen adicional de tiempo o esfuerzo agregado a la estimación para cubrir riesgos, imprevistos o re-trabajos inevitables.

### 14. **Probabilidad en estimación**

Toda estimación tiene asociada una probabilidad de ocurrencia. Una “buena” estimación expresa explícitamente esa probabilidad (ej. “90% de confianza en 24 semanas”).

### 15. **Reestimación**

Proceso de revisar y actualizar las estimaciones durante el ciclo de vida del proyecto conforme cambian requisitos, supuestos y condiciones.

### 16. **Optimismo injustificado**

Tendencia a subestimar tiempos y costos, olvidando sobrecargas, tareas omitidas y errores recurrentes, lo que conduce a prometer “milagros”.

### 17. **Negociación de estimaciones**

Discusión entre responsables técnicos y de negocio para alinear las estimaciones con objetivos realistas, evitando confundirlas con compromisos inamovibles.