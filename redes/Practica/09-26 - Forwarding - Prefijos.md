
## Forwarding

### Tipos de forwarding


## Mascara de red



### Forwarding table 


### LPM

_Longest Prefix Match_

Resuelve el problema cuando hay una superposición en la forwarding table.


## Agregación de Prefijos 

Objetivo: Reducir la cantidad de entradas en la tabla de routeo

Dos redes _continuas_:
- Prefijos de igual longitud 
- Difieren solo en el ultimo bit


## Arquitectura de clases en IP

- CLASE A
- CLASE B
- CLASE C

## Sub-nets

Subdivision lógica de una red

Permiten agrupar una cantidad de direcciones 


Dirección de la red 195.42.40.0/22 -> Hosts: 10 bits 

195.42.40.0/n -> n = 32 - bits para los hosts

Direcciones = # hosts + broadcast + multicast +

| subnet | hosts | routers | addrs | block_size | bits de host | Prefijo subred   | Últimos bits                        |
| ------ | ----- | ------- | ----- | ---------- | ------------ | ---------------- | ----------------------------------- |
| C      | 500   | 1       | 503   | 512        | 9 b          | 195.42.40.0/23   | 00.00000000                         |
| A      | 126   | 1       | 129   | 156        | 8 b          | 195.42.42.0/24   | 01.11111111 + 1 : 00101010.00000000 |
| B      | 61    | 1       | 64    | 64         | 6 b          | 195.42.43.0/26   | 00101011.00000000                   |
| D      | 50    | 1       | 53    | 64         | 6 b          | 195.42.43.64/26  | 00101011.01000000                   |
| E      | 30    | 1       | 33    | 64         | 6 b          | 195.42.43.128/26 | 00101011.10000000                   |
| F      | 2     | 1       | 5     | 8          | 3 b          | 195.42.43.192/29 | 00101011.11000000                   |
| p      | 0     | 3       | 5     | 8          | 3 b          | 195.42.43.200/29 | 00101011.11001000                   |
| r34    | 0     | 2       | 4     | 4          | 2 b          | 195.42.43.208/30 | 00101011.11010000                   |

