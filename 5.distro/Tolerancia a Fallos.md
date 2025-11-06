---
~
---

Estudia las necesidades de sistemas _confiables_

Garantizar que se ejecuyten y comporten de acuerdo a lo esperado por el usuario en distintas condiciones 

Prevenir la aparición de gallas o averías de cara al usuario, tanto normales como excepcionales 

Alternativas para prevenir como tolerar cada situación

_Herramientas_: replicación,votación y recuperación

# Fallos

__Fallo (fault)__ -> __Error__ (en el estado del sistema) -> __Falla/avería (failure)__ (comportamiento incorrecto)

Fallo parcial:
- Un componente incurre en error
- Característica distintiva de los sistemas distribuidos

## Categorización

- __Transientes__: Ocurren una vez y luego desaparecen
- __Intermitenste__: Dificiles de diagnosticar ya que ocurren de forma intermitente
- __Permanente__: Existen hasta el componente defectuoso los reemplaza 

Fallos _improbables != imposibles_

- Improbable: que una moneda caiga de canto
- Imposible: que una moneda se suspenda en el aire


- __Crash__: El servicio se detiene 
- __Timing__: Respuesta fuera de tiempos aceptables 
- __Omisión__: El servicio falla al responder solicitudes entrantes 
- __Respuesta__: La respuesta es incorrecta 
- __Arbitraria o Bizantina__: Diferente información para diferentes consumidores

## Condiciones 

- De entorno:
	- Físicas del hardware (temperatura, ubicación, impedimentos)
	- Interferencia y ruido 
	- Clock drift
- Operacionales:
	- Especificaciones, valores límites y tiempos de respuesta
	- Networking (ancho de banda / latencia)
	- Protocolos soportados

## Detección de errores

Estrategias

__Fault Removal__:
Remover errores antes de que estos sucedan. Detección de errores 

__Fault forecasting__
Determinar la probabilidad de que un componente puede llegar a fallar

__Fault prevenction/Avoidance__
Evitar las condiciones que llevan a la generación de errores (ej. prevención de race condition)

__Fault tolerance__(IMPORTANTE)
Procesar errores en el sistema y tratar los mismos en vez de evitar que sucedan

## Resiliencia 

Mantener cierto nivel aceptable de servicio en presencia de _fallos_ y _desafíos_ ar la operación normal 
- Errores de configuración u operacionales 
- Desastres naturales
- Factores políticos, económicos, sociales o de negocio
- Ataque maliciosos 

__Graceful degradation__ (degradación suave): el comportamiento difiere del comportamiento sin fallos pero continua siendo aceptable

# Confiabilidad 

# Coordinación y Acuerdo 

# Exclusión mutua distribuida