---
layout: post
title: 3 - Loopback y LEDs
date: 2016-01-19
---

## Objetivo
En esta práctica vamos a aprender como comunicar nuestro Arduino con la PC. De esta forma podremos enviar información 
que nos puede ayudar a debuggear un programa, realizar ciertas acciones u obtener información del Arduino. Al final de 
la práctica conoceremos:

* Estructuras de control básicas (IF, ELSE, SWITCH).
* Enviar un String (texto) del Arduino a la PC.
* Enviar Caracteres de la PC al Arduino.

y llegaremos a esto:
<iframe frameborder='0' height='448' marginheight='0' marginwidth='0' scrolling='no' src='https://123d.circuits.io/circuits/1463292-loopback-and-leds/embed#breadboard' width='650'></iframe>

## Materiales
* 1 Arduino UNO R3
* 1 Cable USB A - USB B (Impresora)
* 1 Protoboard
* 3 Resistencias de 150 ohms.
* 1 LED RGB.
* Cable

## Enviar datos del Arduino a PC
Abre un nuevo proyecto de Arduino (menú Archivo/Nuevo). Lo primero que tenemos que hacer es configurar el módulo de 
comunicación del Arduino. Para hacerlo usaremos las instrucciones [Serial](https://www.arduino.cc/en/Reference/Serial):

    void setup() {
        // put your setup code here, to run once:
        ...
    
        Serial.begin(9600);
    }

[Serial.begin(9600)](https://www.arduino.cc/en/Serial/Begin) es una instrucción que configura el módulo Serial (comunicación) del Arduino para poder platicar con la PC. Esta instrucción **siempre** debe de ir en la función *setup()* y **siempre** debe ser la primera instrucción de *Serial* en utilizarse.
El número *9600* significa la velocidad a la cual se va a transmitir los datos. En este caso se van a transmitir *9600* bits por segundo (Baud Rate). Este número **no** es elegido al azar, es una de las velocidades más utilizadas comercialmente, aunque existen otras velocidades como 115,200 (máx velocidad del Arduino). Es **muy importante** saber la velocidad a la que se están comunicando los dispositivos puesto que si tienen configuradas velocidades diferentes los datos enviados pueden ser corrompidos o perdidos.

Para enviar texto a la computadora tenemos las siguientes instrucciones:

* [Serial.print()](https://www.arduino.cc/en/Serial/Print):
Esta instrucción manda el texto que pongamos entre los paréntesis sin hacer un salto de línea, por ejemplo:

        void loop() {
            Serial.print("Kiubo compa");
            Serial.print(", no lo haga compa");
        }
	
en la computadora veríamos: 

	Kiubo compa, no lo haga compa

* [Serial.println()](https://www.arduino.cc/en/Serial/Println):
Esta instrucción manda el texto que pongamos entre los paréntesis haciendo un salto de línea, por ejemplo:

        void loop() {
             Serial.println("Kiubo compa");
             Serial.println(", no lo haga compa");
         }
	
en la computadora veríamos: 

	Kiubo compa
	, no lo haga compa

Podemos hacer combinaciones entre estos dos comandos, por ejemplo:

    void loop() {
        Serial.print("Kiubo compa");
        Serial.println(", no lo haga compa");
        Serial.print("no soy 100tifico, ");
        Serial.print("tampoco 1000itar.");
        Serial.print(" Pero soy 3,1416loto xD");
    }

y en la computadora veríamos:

    Kiubo compa, no lo haga compa
    no soy 100tifico, tampoco 1000itar. Pero soy 3,1416loto xD

O podemos enviar datos:

    void loop() {
        Serial.print("Cien: ");
        Serial.println(100);
        Serial.print("HIGH: ");
        Serial.println(HIGH);
    }
	
y en la computadora veríamos:

    Cien: 100
    HIGH: 1

Por último tenemos que abrir *Serial Monitor* del menú *Tools* y verificar que la **velocidad configurada es la misma que la que configuramos en el Arduino (ej: 9600).**

De esta manera nosotros podemos ver lo que está haciendo el Arduino, en que parte del código va, que por lo contrario sería algo muy complicado de hacer.

> **Precaución:** Una vez que se configure el módulo Serial los pines 0 y 1 del Arduino no podrán ser utilizados para otra cosa. No hay que conectar nada aquí o se va a descomponer la comunicación.

## Enviar datos de la PC al Arduino
Enviar datos es algo muy sencillo en Arduino. Por el contrario, recibir datos no lo es tanto. Aquí tenemos que tener un poco más de control sobre la comunicación. A simple vista, tenemos que:

1. Revisar si hay algun dato disponible.
2. Leer el dato.

Para lograr esto, lo más lógico es primero revisar si hay algún dato disponible, antes de hacer nada. Por ejemplo:

    void loop() {
        ...
    
        if(Serial.available() > 0) {
            Serial.println("Dato recibido");
        }
    
        ...
    }

Aquí haremos uso, por primera vez, de las estructuras de control, en este caso el [**if**](https://www.arduino.cc/en/Reference/If). Básicamente, el **if** evalua una condición y si esta es verdadera entonces ejecuta el código que se encuentra dentro de los corchetes que le siguen, si no entonces se saltea esa parte. En este caso, **si** nuestro módulo Serial nos dice que tiene  más de 0 datos para leer disponibles entonces le mandamos a la computadora el texto "Dato recibido", **si no** recibimos ningún dato entonces no enviamos nada.

> Más sobre [Serial.available()](https://www.arduino.cc/en/Serial/Available).

> Más sobre [*if*](https://www.arduino.cc/en/Reference/If).

Ahora, es útil saber que hemos recibido un dato, pero es más útil saber *que* dato recibimos. Para esto haremos lo siguiente:

    void loop() {
        ...
    
        if(Serial.available() > 0) {
            char dato = Serial.read();
            Serial.print("Dato recibido: ");
            Serial.println(dato);
        }
    
        ...
    }

Primero revisemos que haya algún dato que leer. Si lo hay entonces leemos ese dato y lo guardamos en la variable _dato_. Una vez guardado, podemos hacer lo que sea con ese dato, por lo que decidimos enviarlo de vuelta. Esto es lo que conocemos como *Loopback*.

Ya que sabemos como recibir datos de una PC en el Arduino podemos hacer cosas mucho más complejas, como encender un LED dependiendo del dato recibido. Para hacerlo más interesante utilizaremos LEDs RGB (Red-Green-Blue), que son capaces de encender en cualquier color del espectro visible. Para esto hay que conectar el circuito como sigue:

<iframe frameborder='0' height='448' marginheight='0' marginwidth='0' scrolling='no' src='https://123d.circuits.io/circuits/1463292-loopback-and-leds/embed#breadboard' width='650'></iframe>

Para probar el circuito probemos el siguiente programa:

    // pin references:
    int rojo = 11;
    int azul = 10;
    int verde = 9;
    
    void setup() {
        // put your setup code here, to run once:
        pinMode(rojo, OUTPUT);
        pinMode(azul, OUTPUT);
        pinMode(verde, OUTPUT);
    }
    
    void loop() {
        // put your main code here, to run repeatedly:
        digitalWrite(rojo, HIGH);
        delay(500);
        digitalWrite(rojo, LOW);
        delay(500);
        digitalWrite(azul, HIGH);
        delay(500);
        digitalWrite(azul, LOW);
        delay(500);
        digitalWrite(verde, HIGH);
        delay(500);
        digitalWrite(verde, LOW);
        delay(500);
    }

Para continuar, nuestro programa debe hacer lo siguiente:

1. Si la PC envía la letra 'R' el LED rojo debe encenderse.
2. Si la PC envía la letra 'r' el LED rojo debe apagarse.
2. Si la PC envía cualquier otra letra el LED no debe cambiar su estado.

Una forma que podemos utilizar para esto es revisar que dato fué el que recibimos y *si* recibimos la letra *'R'* entonces procedemos a encender el LED, *si* recibimos la letra *'r'* apaguemos el LED, y si es cualquier otra no hagamos nada. Por ejemplo:

    void loop() {
        ...
    
        if(Serial.available() > 0) {
            // Guardamos el dato recibido...
            char dato = Serial.read();
            Serial.print("Dato recibido: ");
            Serial.println(dato);
    
            // Verificamos el dato guardado...
            if(dato == 'R') {						// si el dato es 'R'...
                digitalWrite(rojo, HIGH);
            } else if(dato == 'r') {				// si el dato no es 'R' pero si es 'r'...
                digitalWrite(rojo, LOW);
            } else {								// Si no fue ninguno de los dos...
                Serial.println("Dato incorrecto");
            }
        }
    
        ...
    }

Ahora tenemos un programa mucho más funcional, interesante y complejo! Podemos ver que las condiciones (IF's) nos proveen de mucha más flexibilidad y poder para controlar nuestro Arduino. Aunque el **if** no es la unica estructura que existe, te presento el [Switch](https://www.arduino.cc/en/Reference/SwitchCase).

## Ejercicio
Ahora que sabes como controlar los colores del LED desde un Arduino el siguiente paso es:

1. Controlar los colores verde y azul con las letras 'G' y 'B', respectivamente, de la misma manera que se controla el color rojo.
2. Crea una sequencia de colores, donde el color cambie cada 1 segundo, con solo enviarle **una** instrucción desde la computadora.

> Tip: utiliza el [Switch](https://www.arduino.cc/en/Reference/SwitchCase) para mayor facilidad.
