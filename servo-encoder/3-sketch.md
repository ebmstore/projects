---
title: Analisi dello sketch

---

### Reimparare a gestire l'encoder

Visto che Timer1 e Servo utilizzano lo stesso timer e quindi vanno in conflitto, in questo sketch utilizzeremo una nuova libreria per gestire l'encoder.
Scaricabile da qui, Encoder può gestire un encoder collegato ai pin di interrupt di arduino.