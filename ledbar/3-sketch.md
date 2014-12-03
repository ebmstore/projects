---
title: Analisi dello sketch
---

In questo breve esempio vedremo come controllare una serie di pin digitali in sequenza configurati come __output__ per poter utilizzare la ledbar.

### Ripetere le cose

Prima di iniziare ad accendere e spegnere i led bisogna configurare i pin come output, il "problema" è che questa volta sono otto pin, e continuando come visto fino ad adesso dovreste scrivere otto righe solo per quest'operazione nonostante si tratti di richiamare sempre la stessa funzione con un diverso parametro.
Un modo abbastanza comodo per ripetere "una parte di codice" *n* volte è il costrutto __for__ ne vediamo di seguito la sintassi:

    for(int i = 0; i < 10; i++)
     {
        /* Blocco di codice da ripetere */
     }

Dove:

  * `int i = 0` è l'inizializzazione di una variabile contatore
  * ` i < 10` è una condizione di test che deve essere vera perchè il ciclo continui
  * `i++` è un'istruzione che viene eseguita al termine di ogni passo del ciclo
  * il blocco di codice tra le due parentesi graffe verrà eseguito ad ogni passo del ciclo

Nel nostro caso il ciclo verrà eseguito 8 volte e la variabile contatore pin assumerà tutti i valori da 2 a 9
nel blocco di codice la variabile verrà passata come parametro a `pinMode` e `digitalWrite`, di conseguenza ad
ogni passo il pin indicato dal contatore verrà configurato come __OUTPUT__ e settato a __LOW__

    for(int pin=2;pin<10;pin++)
    {
      pinMode(pin,OUTPUT);
      digitalWrite(pin,LOW);
    }