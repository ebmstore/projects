---
title: Analisi dello sketch
---

Questo progetto punta ad introdurre le funzioni base per l'input/output
digitale su Arduino, ovvero la "scrittura" di un valore su un pin e la "lettura" dello stato di quest'ultimo.

### Per cosa sarà usato il pin?

Prima di poter iniziare ad usare un __pin__ bisogna comunicare al microcontrollore il tipo di operazioni che verranno
effettuate su di esso ovvero se sarà utilizzato per __input__  o __output__. Per fare ciò abbiamo a disposizione
la funzione `pinMode` utilizzata nelle prime righe di `setup()`.
Questa funzione riceve due parametr: il primo indica il pin su cui si vuole agire e il secondo indica la modalità
in cui verrà impostato.

Il __pin__ da utilizzare è generalmente un numero compreso tra 0 e 13, per maggiori informazioni fate riferimento al documento [La struttura di arduino](link).
Per la modalità invece abbiamo tre possibilità:

 * __OUTPUT__ indica che il pin sarà utilizzato come output, in questo caso per accendere e spegnere il led
 * __INPUT__ indica che il pin sarà utilizzato come input, in questo caso per leggere lo stato del bottone
 * __INPUT_PULLUP__ introdotta da Arduino 1.0.1 indica che il pin sarà utilizzato come input con le resistenze di pullup abilitate, che come dice la parola stessa portano a __HIGH__ (alto) il valore di default del pin.

### Che devo fare?

Per decidere se cambiare lo stato del led, bisognerà controllare lo stato del pushbutton, se è premuto allora
lo stato del led verrà cambiato (se acceso verrà spento e viceversa).

Per controllare lo stato del bottone, o più in generale di un pin configurato come output, si utilizza la funzione
`digitalRead` che riceve come parametro il pin digitale e ritorna il suo stato.
I possibili valori di ritorno sono:

 * __HIGH__ il valore del pin è alto (la tensione applicata al pin è 3V o superiore)
 * __LOW__ il valore del pin è basso (la tensione applicata al pin è 2V o inferiore)

### Controllare il led

Arrivati a questo punto bisogna accendere o spegnere il led, e quindi cambiare lo stato di un pin da alto a basso e viceversa.
Per poter controllare un pin configurato come __OUTPUT__ si utilizza la funzione `digitalWrite` che riceve due parametri: il numero del pin da controllare e lo stato che dovrà assumere.
I possibili valori in cui un pin può trovarsi sono ovviamente:

 * __HIGH__ che nel nostro caso accende il led
 * __LOW__ che invece lo spegne

### E poi? Aspetta!

Dopo la pressione del bottone, potete vedere una chiamata a `delay` la funzione di quest'ultima è quella di attendere ovvero di non far fare nulla al microcontrollore per un periodo di tempo definito.
In questo caso viene utilizzata per dare il tempo di staccare il dito dal bottone alla persona che ha l'arduo compito di controllare il led.
Questa funzione riceve come parametro un numero che indica in numero di _millisecondi_ da aspettare prima di riprendere le operazioni.