---
title: Analisi dello sketch
---

In questo progetto vedremo le funzioni messe a disposizione da arduino per l'input/output analogico con lo scopo di controllare la luminosità di un led tramite un potenziometro.

### La lettura

Come già visto nel documento [Com'è fatto Arduino](link) sulla board abbiamo a disposizione una serie di pin predisposti alla lettura di valori analogici, questi pin sono numerati da 0 a 5 e identificati con la lettera A.
Per leggere il valore applicato ad uno di essi si usa la funzione `analogRead` passandogli come parametro il "numero" del pin preceduto dalla lettera A, nel nostro caso la chiamata sarà `analogRead(A0)` visto che vogliamo leggere dal pin analogico numero 0.
Il valore di ritorno di `analogRead` sarà un numero intero compreso tra 0 e 1023.

### La "scrittura"

Per controllare la luminosità del led si utilizza la funzione `analogWrite` passandogli come parameteri: il pin dal quale si desidera venga emesso
il segnale e un intero compreso tra 0 e 255.
A discapito di quanto possa suggerire il nome, questa funzione non permette di generare un vero e proprio segnale analogico ma un onda quadra costante con __duty cycle__ uguale al numero indicato nel secondo parametro della funzione, questa pratica prende il nome di [PWM](wikipedia).

Non tutti i pin possono generare un segnale PWM (e quindi essere usati in una chiamata `analogWrite`) su Arduino UNO questi pin sono  __3__, __5__, __6__, __9__, __10__, e __11__.

### Aggiustare i numeri

Come avrete potuto notare abbiamo a che fare con valori che si trovano in due intervalli differenti: il valore letto, tra **0** e **1023** e il valore da scrivere tra **0** e **255**, tutto ciò impedisce di utilizzare direttamente il valore letto dal potenziometro come parametro di luminosità del led.
Per ovviare a problemi di questo genere il core Arduino mette a disposizione una funzione chiamata `map` che permette di cambiare il range di un numero; la sintassi per richiamare funzione è la seguente: `map(valore, valoreMinimoIniziale, valoreMassimoIniziale, valoreMinimoFinale, valoreMassimoFinale)` e dati questi parametri ritornerà un un numero nel range desiderato.
Ad esempio, per trasformare il valore letto dal potenziometro in un valore usabile da `analogWrite` si farà in questo modo:
`int valoreFinale = map(valoreInizale, 0, 1023, 0, 255)`

Dove:
 * __valoreInizale__ è il valore letto
 * il primo __0__ è il valore minimo leggibile da un ingresso analogico
 * __1023__ è il valore massimo leggibile da un ingresso analogico
 * il secondo __0__ è il valore minimo accettato da `analogWrite`
 * __255__ è il valore massimo accettato da `analogWrite`
 * il valore contenuto in __valoreFinale__ dopo la chiamata sarà il numero nel nuovo range