---
layout: post
id: 2
title: Hola Mundo
date: 2016-01-11
---

## Objetivo
En esta práctica vamos a ver por primera vez como se utiliza el Arduino. Vamos a crear un programa muy simple que hará 
parpadear un LED en la tablilla de color amarillo (ámbar) cada segundo. Al final de la práctica conoceremos:

* Como utilizar el IDE de Arduino.
* La estructura básica de un programa de Arduino.
* Como conectar el IDE a nuestro Arduino.
* Como cargar un programa de nuestra computadora al Arduino.

Y llegaremos a esto:
<iframe frameborder='0' height='448' marginheight='0' marginwidth='0' scrolling='no' src='https://123d.circuits.io/circuits/1411515-hello-world/embed#breadboard' width='650'></iframe>

## Materiales
* 1 Arduino UNO R3
* 1 Cable USB A - USB B (Impresora)
 
## Instrucciones
Primero que nada, abre un nuevo proyecto de Arduino haciendo click en el botón “Nuevo” (New) o en el menú Archivo/Nuevo 
(File/New). Nos debe de aparecer una nueva ventana como se muestra en la imagen. Ésta es la ventana de nuestro código. 
Aquí estaremos escribiendo todas las instrucciones que queramos que realice nuestro Arduino. 

Podemos observar que de entrada el archivo sketch_<fecha> contiene unas lineas de código ya escritas. No entraremos 
tanto en detalle por ahora.

Ahora hay que escribir el siguiente código:

    void setup() {
      // put your setup code here, to run once:
      pinMode(13, OUTPUT);
    }
    
    void loop() {
      // put your main code here, to run repeatedly:
      digitalWrite(13, HIGH);
      delay(500);
      digitalWrite(13, LOW);
      delay(500);
    }

A continuación debemos de cargar el código siguiendo los siguientes pasos:

1. Conecta el Arduino a tu PC si no lo has hecho todavía.
2. Del menu "Tools", en la opción "Board:" revisar que este seleccionado "Arduino/Genuino Uno".
![Alt text]({{ site.url }}/images/select_board.png)
3. Del menu "Tools" revisar que la opción "COM##" **para Windows** (ej. COM3) o "/dev/tty.usbmodem" **para Mac**.
![Alt text]({{ site.url }}/images/select_port.png)
4. Dar click en el botón "Upload" y esperar.
![Alt text]({{ site.url }}/images/upload.png)

En el Arduino deben de ver dos LEDs prendíendose y apagándose (Tx, Rx). Cuando la descarga del programa finalice 
aparecerá un mensaje diciendo "Done Uploading". Unos segundos después el LED (L) empezará a parpadear como en la imágen.