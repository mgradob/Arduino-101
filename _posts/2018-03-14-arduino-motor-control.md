---
layout: post
session: 10
title: Arduino + Motores + Etapa de Potencia
date: 2018-03-14
---

# Objetivo
Controlar la dirección de un motor eléctrico, aplicando lo aprendido en las prácticas anteriores.

# Instrucciones
Programar el arduino para que reciba un dato desde la computadora (1 caracter) y ejecute lo siguiente:
1. Si el dato es 'i', girar el motor en un sentido.
2. Si el dato es 'd', girar el motor en el otro sentido.
3. Si el dato es 's' el motor debe detenerse.

Para cualquier otro caso no se debe realizar ninguna accion.

# Código
El código es muy sencillo, porque podemos tomar la práctica de comunicacion serial (esta es nuestra base). La diferencia
estaa en la accion a ejecutar en cada caso.

Primero que nada configuramos los pines de salida:

    void setup()
    {
      Serial.begin(9600);
      
      pinMode(6, OUTPUT);
      pinMode(7, OUTPUT);
    }
    
Vamos a usar los pines 6 y 7 del Arduino como salidas, por eso las configuramos como OUTPUT.

Luego, en nuestro loop vamos a agregar las instrucciones digitalWrite(). Esta instrucción nos permite encender (5v) o 
apagar (0v). 

Como vimos en la práctica del L293, cuando combinamos las señales que reciben los pines de INPUT del L293 es cuando 
controlamos la direccioón del motor, por eso solo basta con jugar con los valores de HIGH o LOW en los pines para generar
estas señales, por ejemplo:

    if(dato == 'i') {
      Serial.println("Izquierda");
      digitalWrite(6, LOW);
      digitalWrite(7, HIGH);
    }
    
El código anterior haría que nuestro motor gire en un sentido.

El código terminado luce de la siguiente manera:
    
    void setup()
    {
      Serial.begin(9600);
      
      pinMode(6, OUTPUT);
      pinMode(7, OUTPUT);
    }
    
    void loop()
    {
      if(Serial.available() > 0) {
        char dato = Serial.read(); 
        Serial.print("Dato recibido: ");
        Serial.println(dato);
           
        if(dato == 'i') {
          Serial.println("Izquierda");
          digitalWrite(6, LOW);
          digitalWrite(7, HIGH);
        } else if(dato == 'd') {
          Serial.println("Derecha");
          digitalWrite(6, HIGH);
          digitalWrite(7, LOW);
        } else if(dato == 's'){             
          Serial.println("Alto");
          digitalWrite(6, LOW);
          digitalWrite(7, LOW);
        }
      }
    }

# Conexiones
![Alt text]({{ site.url }}/images/session-10-1.png)

_Recuerda poner mucha atención al conectar los cables, asegurate que sean las entradas correctas!_
