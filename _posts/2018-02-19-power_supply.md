---
layout: post
session: 9
title: Fuentes de Poder
date: 2018-02-19
---

# Objetivo
En esta práctica vamos a aprender sobre las fuentes de poder. Al final conocerás como implementar una para tus proyectos.

## Material
* 1 Regulador lineal 7805
* 1 Capacitor de 0.33 uF
* 1 Capacitor de 0.1 uF
* 1 Protoboard
* Cable

# Que es
Las fuentes de poder son circuitos eleécticos que nos proveen una fuente de voltaje y corriente para otros circuitos. Hay
muchas variaciones de fuentes, como AC-DC, DC-DC, lineales, conmutadas, y muchas más.

Un ejemplo sencillo de fuente de poder son las baterías, como las pilas externas para celulares o las pilas AA/AAA, que 
utilizamos para energizar nuestros celulares, controles remotos, juguetes, etcétera.

Para nuestro proyecto tenemos que hacer uso de una fuente de poder movil, por lo que requerimos de baterías. Necesitamos
energizar nuestro circuito de control y la etapa de potencia de los motores, por lo que una pila de alto voltaje y
corriente son ideales. Vamos a usar pilas de 9v. La ventaja es que podemos proveer a nuestros motores con un voltaje de
9v para que tengan mayor potencia, el problema es que nuestro circuito requiere 5v. Para solucionar esto implementaremos
un circuito regulador de voltaje.

# Reguladores
Estos circuitos integrados nos permiten mantener un nivel de voltaje definido y estable a partir de un voltaje mayor.

En nuestro caso vamos a usar el regulador 7805, el cual nos provee un voltaje regulado de 5v (como lo dicen sus números).

![Alt text]({{ site.url }}/images/7805.png)

Para reducir el ruido que se pudiera generar necesitamos agregar un par de capacitores en la entrada y salida del regulador.
El circuito se ve de la siguiente manera:

![Alt text]({{ site.url }}/images/circ-7805.png)

![Alt text]({{ site.url }}/images/circ-7805-2.png)

De esta manera nosotros podemos utilizar la misma fuente de poder (pila) para energizar nuestro circuito y darle poder a
nuestros motores.

En la siguiente práctica vamos a implementar un circuito junto con el que ya tenemos para controlar los motores.
