---
layout: post
session: 7
title: Electrónica. Práctica 1.
date: 2018-01-31
---

# Objetivo
En esta práctica aprenderás sobre como hacer prototipos de circuitos elétricos. Al final sabrás como usar el protoboard 
y la fuente de poder.

## Material
* Protoboard.
* Fuente de poder (cables).
* 4 LEDs rojo.
* 2 Resistencias de 1k ohm.
* Cable.

## Parte 1 - Circuito en serie.
Arma un circuito en serie con los siguientes elementos: 

* 1 LED.
* 1 Resistencia de 1k ohm.
* Cable.

1. Configura la fuente de poder a 9v, no suministres energía todavía.
2. Conecta el cable positivo (rojo) a una de las lineas vertical del protoboard (rojo) y el cable negativo (negro) a la
otra linea vertical. **VERIFICA QUE NO SE JUNTEN LOS CABLES, EVITA UN CORTO.**
3. Conecta un pin de la resistencia a algún punto de la linea positiva.
4. Conecta el otro pin a una linea horizontal del protoboard.
5. Conecta el pin positivo del LED en la **misma** linea horizontal en la que está conectada la resistencia.
6. Conecta el pin negativo del LED en otra línea horizontal del protoboard.
7. Conecta un cable de la linea horizontal en donde está conectado el pin negativo del LED hacia la linea negativa.
8. Suministra energía de la fuente de poder.

En este punto el LED debe encender. La fuente debe marcar 9v y aproximadamente 7mA de corriente.

Al finalizar debes tener un circuito como el siguiente:
![Alt text]({{ site.url }}/images/elec-prac-1-1.png)

## Parte 2 - Circuito en paralelo.
Arma un circuito en paralelo con los siguientes elementos: 

* 4 LEDs.
* 2 Resistencias de 1k ohm.
* Cable.

1. Configura la fuente de poder a 9v, no suministres energía todavía.
2. Conecta el cable positivo (rojo) a una de las lineas vertical del protoboard (rojo) y el cable negativo (negro) a la
otra linea vertical. **VERIFICA QUE NO SE JUNTEN LOS CABLES, EVITA UN CORTO.**
3. Conecta un pin de la resistencia a algún punto de la linea positiva.
4. Conecta el otro pin a una linea horizontal del protoboard.
5. Conecta el pin positivo de un **primer** LED en la **misma** linea horizontal en la que está conectada la resistencia.
6. Conecta el pin negativo del **primer** LED en otra línea horizontal del protoboard.
7. Conecta el pin positivo de un **segundo** LED a otra línea horizontal del protoboard.
8. Conecta el pin negativo del **segundo** LED en otra línea horizontal del protoboard.
9. Conecta un cable entre el pin negativo del **primer** LED y el pin positivo del **segundo** LED.
10. Conecta un cable de la linea horizontal en donde está conectado el pin negativo del **segundo** LED hacia la linea negativa.
11. Repite los pasos 3 al 10 para los LEDs restantes.
8. Suministra energía de la fuente de poder.

En este punto los LEDs deben encender. La fuente debe marcar 9v y aproximadamente 10.8mA de corriente.

Al finalizar debes tener un circuito como el siguiente:
![Alt text]({{ site.url }}/images/elec-prac-1-2.png)
