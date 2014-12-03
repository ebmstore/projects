---
title: Analisi dello sketch
---

### Gestire il servomotore

Per utilizzare i servomotori abbiamo a disposizione la libreria Servo, già inclusa nel core Arduino.

#### Inizializzazione

Innanzitutto bisogna includere la libreria, con il solito:

    #include <Servo.h>

Dichiarare un'oggetto di tipo Servo:

    Servo myServo;

Inizializzare l'oggetto utilizzando il metodo `attach` che riceve come
parametro il pin a cui è collegato il servo.

#### Farlo muovere

Per far muovere il servo e quindi posizionarlo in un dato angolo si utilizza il metodo `write` che per il nostro servo riceve come parametro un numero compreso tra 0 e 179 che è appunto l'angolo.

    myServo.write(120);