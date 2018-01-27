---
layout: post
session: 6
title: Intro a Electrónica
date: 2018-01-29
---

# Objetivo
En esta práctica vamos a aprender de manera básica sobre circuitos eléctricos y electrónica. Al final conocerás sobre los
distintos tipos de circuitos y componentes que existen, así como implementarlos.

# Electricidad
La electricidad simplemente se refiere al flujo de electrones. Hay dos tipos:

* Alterna
* Directa

## Alterna
En este tipo la dirección hacia donde fluyen los electrones siempre se está intercalando, o alternando. Este cambio se 
mide en hertz, que es el número de cambios que hay en 1 segundo (60 Hz = 120 cambios, 2 por ciclo).  

## Directa
En este tipo la dirección no cambia, siempre se mantiene fija en sentido de positivo (+) a negativo (-), o tierra como 
se le conoce también.

Usualmente usamos las medidas de volts (V) y amperes (A). Los amperes son la cantidad de electrones que estan fluyendo, 
mientras que el voltaje es la fuerza que se requiere para poder moverlos de un punto a otro. También se utilizan los 
watts (W) que nos dice el trabajo que se realiza cuando fluye la electricidad (P = V * I).

## Circuito abierto y cerrado
Un circuito cerrado es cualquier camino cerrado y completo por donde pueda fluir la electricidad. Por el contrario, un 
circuito abierto es un camino incompleto, que no permite el flujo de electrones.

## Resistencia
Lo más importante de un circuito es que su electricidad siempre debe ser usada. En otras palabras, debe haber algo entre
la fuente de poder (fuente de voltaje y corriente) que agregue resistencia al circuito (motor, cable, componente). Cuando
no hay resistencia en un circuito cerrado se le conoce como corto. Es muy importante que no haya cortos en nuestros 
circuitos, porque la electricidad es floja, y prefiere tomar el camino que menos resistencia tenga, pudiendo llegar a 
dañar el equipo y componentes que utilicemos.

## Serie y paralelo
Hay dos formas de conectar circuitos eléctricos:

* Serie
* Paralelo

### Serie
En un circuito en serie los componentes están conectados uno tras del otro, creando
una cadena. De esta manera la corriente fluye por el primer componente, luego el que le sigue y así sucesivamente. Hay 
que tomar en cuenta que la corriente que fluye en este circuito es siempre igual, pero el voltaje se divide entre los 
componentes.

### Paralelo
En un circuito en paralelo los componentes están conectados lado a lado, compartiendo dos puntos en común. Esto hace que
el voltaje que reciban sea el mismo para todos, pero la corriente se va a dividir entre los componentes.

#Componentes
Hay muchísimos componentes electrónicos, aquí veremos solo los más básicos. 

## Resistencias
Como su nombre implica, este componente agrega resistencia a nuestro circuito. Se miden en ohms y tienen diferentes marcas
que nos indican su valor, en un código de colores.

## Capacitores
Este componente es como una pequeña pila, almacena electricidad y luego la descarga cuando el circuito sufre una pérdida 
de voltaje. Se miden en faradios (F) con valores normalmente entre picofaradios (pF), nanofaradios (nF) y microfaradios (uF).
Los dos timpos más comunes son los capacitores cerámicos (que parecen lentejas) y los electrolíticos (tubos). Los cerámicos
no son polarizados, mientras que los electrolíticos si lo son, lo que requiere que los conectemos correctamente o pueden
llegar a fallar (incluso a explotar).

## Diodos
Son componentes polarizados, por lo que permiten el flujo de corriente solo hacia una dirección, y nos permiten evitar 
que haya flujo en el sentido incorrecto. Estos componentes tienen un consumo de generalmente 0.7v, lo que hay que tener 
en consideración al momento de diseñar nuestro circuito.

## Transistores
Los transistores son otro componente que nos permiten controlar corriente. En este caso, reciben una pequeña corriente en
el pin de Base y la amplifican de tal manera que una corriente mas grande fluya entre el Colector y el Emisor. Existen
básicamente dos tipos: NPN y PNP. En los NPN la corriente fluye del Colector al Emisor. En los PNP fluye del Emisor al
Colector.

## Circuitos Integrados
Son componentes que, como su nombre lo dice, contienen ya un circuito que realiza alguna función en específico, en un
empaque pequeño, y emplean otros componentes. Tienen su número de parte impreso y tambien tienen una pequeña marca que 
nos indica en donde empieza el conteo de pines.

## Potenciómetros
Son resistencias variables, tienen una perilla para ajustar el valor de la resistencia deseada. Su valor, a diferencia de
las resistencias, viene impreso en número, y pueden incrementar de manera lineal o logarítmica. Tienen 3 pines, de tal
manera que actuan como un **divisor de voltaje**.

## LED
Los LEDs son diodos que emiten luz (Light Emitting Diode), y como todos los diodos, solo permiten el flujo de corriente 
en una sola dirección y requieren de un voltaje para funcionar. Por lo general no añaden mucha resistencia, por lo que
es muy recomendable agregar una resistencia en serie para evitar un corto.

## Switch
Son instrumentos mecánicos que permiten abrir o cerrar un circuito. Los switches no generan resistencia alguna, por lo que
un circuito con un solo switch se puede considerar un corto, mientras este cerrado.

## Protoboard (Breadboard)
Son unas placas con agujeros que nos permiten hacer prototipos de circuitos.

Al centro estan divididos en dos secciones, con filas hacia los lados, marcadas con letras. Esto permite insertar circuitos
integrados en el centro.

A los lados hay columnas continuas, las cuales se usan generalmente para voltaje y tierra respectivamente. 
 