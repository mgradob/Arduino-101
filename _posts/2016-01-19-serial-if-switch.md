---
layout: post
session: 3
title: Serial, If y Switch
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
Enviar datos es algo muy sencillo en Arduino. Por el contrario, recibir datos no lo es tanto. 
Aquí tenemos que tener un poco más de control sobre la comunicación.
Para lograr esto lo más lógico es primero revisar si hay algún dato disponible. Por ejemplo:

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

Primero revisemos que haya algún dato que leer. 
Si lo hay entonces leemos ese dato y lo guardamos en la variable _dato_. 
Una vez guardado, podemos hacer lo que sea con ese dato, por lo que decidimos enviarlo de vuelta. 
Esto es lo que conocemos como *Loopback*.

## Mejorando nuestro programa
El if nos da mucha flexibilidad, no solo podemos validar una expresión, podemos agregar diferentes expresiones e inclusive agregar una expresión común.

    void loop() {
        ...
        
        if(Serial.available() > 0) {
            char dato = Serial.read(); 
            Serial.print("Dato recibido: ");
            Serial.println(dato);
           
            if(dato == 'A') {           // Podemos anidar IF (IF dentro de IF)
                Serial.println(1);
            } else if(dato == 'B') {    // Podemos validar diferentes opciones
                Serial.println(2);
            } else {                    // Si no se cumple ninguna de las condiciones de arriba ejecutamos este código
                Serial.println(-1);
            }
        }
        
        ...
    }
    
## Mejorando todavía más
El if es una excelente herramiente ciertamente, pero tiene una gran desventaja, ¿que pasa cuando existen muchos casos?
C nos brinda de otra excelente herramienta, el [Switch](https://www.arduino.cc/en/Reference/SwitchCase).

    void loop() {
        ...
        
        if(Serial.available() > 0) {
            char dato = Serial.read(); 
            Serial.print("Dato recibido: ");
            Serial.println(dato);
           
            switch (dato) {
                case 'A':
                  Serial.println(1);
                  break;
                  
                case 'B':
                  Serial.println(2);
                  break;
                  
                default:
                  Serial.println(-1);
                  break;
            }
        }
        
        ...
    }

## Ejercicio
Haz un programa que reciba un dato de la computadora y dependiendo de su valor haga lo siguiente:
* Si recibe un 1 -> Imprima el resultado de 12 + 74
* Si recibe un 2 -> Imprima el resultado de 82 - 12
* Si recibe un 3, 4, 5 -> Imprima el resultado de 13 x 5
* Si recibe un 6, 7 -> Imprima el resultado de 36 / 7
* Si recibe un 8 en adelante -> Imprima "La operación no es válida"
