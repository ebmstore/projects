---
title: Analisi dello sketch
---

### Qualcosa di più complesso

In questo esempio vedremo come controllare la ledbar con l'encoder, l'effetto sarà visivamente simile a [Ledbar potenziometro](/projects/ledbar-potentiometer)
ma quello che imparerete sarà significativamente maggiore. Questo infatti è il primo esempio più complesso dello starter kit.

### Gestire l'encoder

Per gestire l'encoder senza dannarsi è preferibile utilizzare una libreria, in questo caso la scelta è ricaduta su ClickEncoder, libreria scritta da __0xPIT__ e disponibile su [qui](https://github.com/0xPIT/encoder/tree/arduino).
ClickEncoder è stata scritta per gestire encoder rotativi con bottone, come quello incluso nel kit, la gestione del bottone però non sarà argomento di questo esempio ma verrà trattata in [Lampada Multicolore](/projects/rgb-encoder).

Per poter utilizzare ClickEncoder è prima necessario includerla all'inizio dello sketch, insieme alla libreria TimerOne (già vista in [Come installare una libreria](/instlib)), questo viene fatto con le direttive:

    #include <ClickEncoder.h>
    #include <TimerOne.h>

Successivamente bisognerà dichiarare le variabili utilizzate per gestire l'encoder:
 
 * `ClickEncoder *encoder` istanzierà un puntatore ad un oggetto di tipo ClickEncoder
 * `int16_t last` verrà utilizzata per conservare l'ultimo valore letto
 * `int16_t value` verrà utilizzata per conservare il valore appena letto

Dopo le variabili bisognerà dichiarare la funzione da far richiamare al Timer1, che semplicemente richiamerà `encoder->service()`

In `setup()` oltre alla configurazione dei pin come output (già affrontata precedentemente) compiremo le seguenti azioni:

#### Inizializzazione dell'oggetto ClickEncoder

Nella riga quì seguente verrà istanziato un oggetto di tipo ClickEncoder tramite la chiamata al costruttore ClickEncoder:

      encoder = new ClickEncoder(A1, A0, A2);

I parametri da passare al costruttore sono i seguenti: i primi due sono i due pin di impulsi dell'encoder e il terzo è il pin del bottone.

#### Inizializzazione del Timer1 e attacco della funzione

Con la chiamata a `Timer1.initialize(1000)` il timer 1 sarà configurato per richiamare la funzione ogni 1000 millisecondi.
La funzione da richiamare verrà attaccata con `Timer1.attachInterrupt(nomeFunzione)` che in questo caso sarà `Timer1.attachInterrupt(timerIsr)`

#### Recuperare i dati dall'encoder

Nella funzione `loop()` avremo bisogno di leggere i il valore dall'encoder, per fare ciò basterà sommare a value il valore ritornato da `encoder->getValue()`, successivamente bisognerà controllare se il valore è maggiore di 11 e nel caso riportarlo a 0.
Dopo aver controllaro che il valore sia in range bisognerà controllare che sia diverso dall'ultimo valore letto (per verificare che l'encoder sia stato girato), in caso affermativo all'ultimo valore letto (`last`) viene assegnato il valore appena letto, cioè `value`.
