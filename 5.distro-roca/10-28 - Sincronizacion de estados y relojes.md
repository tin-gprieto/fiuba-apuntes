# Estados globales
## Algoritmo de Chandy-Lamport

tiempo lógico vs tiempo físico 
# Sistema de tiempo real 

Real-Time (RT)

El sistema evoluciona en función de requerimientos temporales requeridos por el entorno.

Depende de que se entregue una respuesta CORRECTA en un tiempo CORRECTO 

- __Hard RT__: 
	- Marcapasos -> no se admiten respuestas fueras de termino (_deadline_)
- __Soft RT__:
	- Los fallos de delivery pueden ser admitidos ocasionalmente


Previsibilidad != Performace

No es una respuesta rápida, sino una respuesta en un intervalo indicado 

Tiempo característico de un fenómeno físico 

__Frecuencia de nyquist__

Comunicación fiable y sincrónica

TCP NO ES PARA RT -> Garantiza fiabilidad pero no garantiza delivery on time 

Utilizar la comunicación de la capa _FISICA_
Protocolo RS32 ?

__Profi bus__
__Profi net__: Protocolo certificado para un cable ethernet

__PLC__ - Hardware especifico para Sistemas RT (empresas como ABB, Siemens, etc)

Microprocesador - Computadora domestica - multiprosito
Microcontrolador - Propósito especifico - Código grabado dentro del procesador que se repite una y otra vez sin posibilidad de que se modifique - Lenguaje C/ Assembly - Frecuencia lenta pero confiable


# Sistemas de control

Control vs Proceso 

Variable controlada  vs variable manipulada 

Actuador

Sistema de controla abierto 

![[Drawing 2025-10-28 21.35.36.excalidraw]]


Control a lazo cerrado 

![[Drawing 2025-10-28 21.38.20.excalidraw]]