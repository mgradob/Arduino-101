---
layout: post
session: 8
title: Electrónica. Práctica 2.
date: 2018-02-09
---

# Objetivo
En esta práctica aprenderás como controlar motores eléctricos por medio de señales eléctricas.

## Material
* Protoboard.
* Fuente de poder (cables).
* 1 Motor 5v.
* 1 Circuito Integrado L293.
* Cable.

## Circuitos Integrados
Estos componentes electrónicos contienen muchos más componentes en su interior. En nuestro caso el L293 contiene toda la
electrónica necesaria para controlar motores de corriente directa.

Los circuitos integrados se ven de la siguiente manera:
![Alt text]({{ site.url }}/images/elec-prac-2-1.png)

Todos los pines (patitas) estan enumerados, y para conocer cual es el primero debemos buscar la marca en un extremo 
(una media luna). Una vez que identifiquemos la marca los pines se empiezan a enumerar empezando del lado izquierdo hacia
abajo y luego al lado derecho empezando por abajo.

Cada pin del circuito integrado tiene una función y en el caso del L293 éstas son las funciones que tienen:
 ![Alt text]({{ site.url }}/images/elec-prac-2-2.png)

## Parte 1 - Circuito en serie.
Para el circuito los pasos son un poco diferentes a los de la práctica anterior: 

1. Conecta el pin Vcc 1 (#16) a 5v. Este pin energiza todo nuestro circuito integrado.
2. Conecta el pin Vcc 2 (#8) a 5v. Este pin provee la energia a los motores, si quisieramos que giraran más rápido 
podríamos aplicar mayor voltaje.
3. Conecta los pines de GND (#12 y #13) a tierra.
4. Conecta el pin Input 4 (#15) a 5v.
5. Conecta el pin Input 3 (#10) a 5v.
6. Conecta un pin del motor al pin Output 4 (#14).
7. Conecta el otro pin del motor al pin Output 3 (#11).
8. Enciende la fuente de poder.

Al finalizar debes tener un circuito como el siguiente:
![Alt text]({{ site.url }}/images/elec-prac-2-3.png)

En este punto nuestro circuito está energizado, brindando de electricidad a nuestro motor, pero... no se mueve, ¿Por qué?

- Desconecta el cable del pin Input 4 (#15) y conectalo a GND.

Ahora nuestro motor gira en un sentido.

- Vuelve a conectar el cable del pin Input 4 (#15) a 5v.
- Desconecta el cable del pin Input 3 (#10) y conectalo a GND.

Ahora el motor gira en el sentido opuesto.

La explicación es simple:

Para que nuestro motor gire debe existir una diferencia de voltaje, cuando tenemos conectados los pines Input 3 e Input 4
a 5v el L293 está suministrando 5v en los pines de Output 3 y 4, respectivamente. 

Cuando tenemos conectados los pines de Input 3 e Input 4 a GND el L293 está suministrando 50v en los pines de Output 3 y
4, respectivamente.

Para que giren los pines de Input deben estar conectados diferentes, uno a 5v y otro a GND.

Ahora, solo hemos usado la mitad del circuito integrado, pero el L293 puede controlar otro motor del otro lado (pines #1
a #7).

¿Qué combinaciones se te ocurren? ¿Cuantos motores podríamos controlar con 1 solo L293?
