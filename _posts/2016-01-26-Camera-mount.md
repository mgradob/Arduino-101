---
layout: post
title: Montaje de la Cámara
date: 2016-02-02
---

## Objetivo
La sesión pasada terminamos de desarrollar el código para controlar los dos servomotores y los LEDs. En esta práctica vamos a integrar el código con el circuito necesario.

## Materiales
* 1 Arduino UNO R3
* 1 Cable USB A - USB B (Impresora)
* 2 Servomotor
* 4 LEDS
* 5 Resistencias 1k
* 1 Transistor
* 1 Bateria 11.1v
* 1 Protoboard
* Cable

## Código final
El código que desarrollamos es el siguiente:
    
    #include<Servo.h>
    
    Servo horizontal;
    Servo vertical;
    
    int gradh = 90;
    int gradv = 90;
    
    int leds = 13;
    
    void setup() {
        Serial.begin(9600);
        
        horizontal.attach(12);
        vertical.attach(11);
        
        pinMode(leds, OUTPUT);
    }
    
    void loop() {
        if(Serial.available() > 0){
            char dato = Serial.read();
            Serial.print("Dato: ");
            Serial.println(dato);
            
            if(dato == 'w'){
                if(gradv < 180){
                    gradv = gradv + 10;
                }
            }
            else if(dato == 's'){
                if(gradv > 0){
                    gradv = gradv - 10;
                }
            }
            else if(dato == 'a'){
                if(gradh > 0){
    	            gradh = gradh - 10;
                }
            }
            else if(dato == 'd'){
                if(gradh < 180){
                	gradh = gradh + 10;
                }
            }
            else if(dato == 'l'){
                digitalWrite(leds, HIGH);
            }
            else if(dato == 'o'){
                digitalWrite(leds, LOW);
            }
            
            vertical.write(gradv);
            delay(15);
            horizontal.write(gradh);
            delay(15);
        }
    }
    

## Circuito
Nuestro circuito debe verse como el siguiente:

<iframe frameborder='0' height='448' marginheight='0' marginwidth='0' scrolling='no' src='https://123d.circuits.io/circuits/1534702-camera-mount/embed#breadboard' width='650'></iframe>

### Transistor
Vamos a utilizar 4 LEDs para la lámpara, y esto significa que va a haber mucho consumo de energía. El primer problema que nos enfrentamos es el mismo Arduino. Este es capaz de suministrar muy poca energía para prender todos los LEDs y los servomotores al mismo tiempo. Así que tenemos que apoyarnos de la electrónica.

El **transistor** es un componente electronico que nos permite tener un **switch** que se activa o desactiva con electricidad, en lugar de un botón físico.

El transistor tiene 3 patitas: Colector, Base y Emisor.

#### Colector
En esta patita es por donde entra toda la energía que van a utilizar nuestro transistor, así que aquí se van a conectar todos los LEDs que queramos prender. **Hay que tener en cuenta que cada LED debe tener una resistencia en serie!**

#### Base
Esta patita es la que activa o desactiva el transistor, como el botón de un switch físico. Aquí vamos a conectar el pin del Arduino que va a controlar el encendido y apagado de los LEDs.

#### Emisor
Por esta patita va a salir la energía que utilizó el transistor, así que esta patita debe conectarse a GND.

### Pila Externa de 11.1v
Como nuestro Arduino no va a ser capaz de entregar toda la energía que requiere nuestro circuito necesitamos usar una pila externa. Esta pila tiene 2 cables, rojo = voltaje, negro = GND.

>**Es MUY importante que todas las GND estén conectadas entre sí!!**