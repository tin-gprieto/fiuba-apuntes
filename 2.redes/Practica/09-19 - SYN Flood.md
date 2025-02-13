---
~
---

## ! - Consultas

- 3 ACK repetidos como senal de caída
- Slow Start vs Congestion avoidance con timeout
- ...

## SYN Flood

(Diapositiva)

Tipo de DDOS (no distribuido)


## Ejercicio de Fragmentacion

Fragmentacion -> Capa de Red (IP)


Packet size: 1600B


_A_ -L1-> _R1_ -L2-> _R2_ -L3-> _R3_ -L4-> _B_

DF = 0
ID0 = 0xABCD

|        | L1   | L2   | L3  | L4   |
| ------ | ---- | ---- | --- | ---- |
| MTU(B) | 2000 | 1000 | 800 | 2000 |

Completar:

								DATAGRAM HEADER

| Name | Payload Size | IHL | Total Length | ID     | MF  | DF  | Fragment Offset |
| ---- | ------------ | --- | ------------ | ------ | --- | --- | --------------- |
| 0    | 1600         | 5   | 1620         | 0xABCD | 0   | 0   | 0               |
| 1    | 976          | 5   | 996          | 0xABCD | 1   | 0   | 0               |
| 2    | 624          | 5   | 644          | 0xABCD | 0   | 0   | 122             |
| 1.1  | 776          | 5   | 796          | 0xABCD | 1   | 0   | 0               |
| 1.2  | 200          | 5   | 220          | 0xABCD | 1   | 0   | 97              |

A _B_ llegan los paquetes: 2, 1.1, 1.2 -> SOLO EL HOST DE DESTINO RE-ENSAMBLA

- _Payload size_: ! Divisible por 8 para el total length

- _IHL_: Internet Header Length (3b)
Tamanio default (sin options): 20B -> value: 5

- _ID_:  Identifier (8B)

- _MF_: More fragments 
(0 - ultimo fragmento / 1 - hay mas fragmentos)

- _DF_: 
(0 - Se puede fragmentar / 1 - No se puede fragmentar)

- _Fragments Offsets_ (8B): Payload size anterior / 8


**Preguntas**:

- Que pasa si se pierde un fragmento?

Se pierde todo el paquete

- Que pasa si llegan desordenados ?

Nada, se guarda en un buffer y se re-ensambla cuando llega todo