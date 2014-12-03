---
title: Analisi dello sketch
---

In questo esempio vedremo come svolgere delle operazioni di base sul con il display per poter stampare un piccolo testo.
Per gestire il display bisognerà includere la libreria `LiquidCrystal.h`, già disponibile nell'IDE Arduino.

### Inizializzazione del display

Per iniziare il display bisognerà chiamare il costruttore all'inizio dello sketch con la chiamata: `LiquidCrystal lcd(12, 11, 5, 4, 3, 2);`
Dove i parametri sono:

   * Pin __RS__
   * Pin __ENABLE__
   * Pin dati

Successivamente, in `setup()` bisognerà richiamare la funzione `begin` nel seguente modo: `lcd.begin(16,2)`
I parametri sono:

   * Colonne (16)
   * Righe  (2)

### Scrivere sul display

Per scrivere un messaggio sul display abbiamo a disposizione la funzione `print`, che prende come parametro il messaggio da stampare.
Esempio: `lcd.print("Messaggio")`

### Spostare il cursore

Per spostare il cursore si usa il metodo `setCursor` che riceve come parametri la colonna e la riga in cui posizionare il cursore.
__Righe e colonne si contano a parire da zero__