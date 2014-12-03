---
title: Analisi dello sketch
---

Il led __RGB__ è considerabile come la fusione di tre led (rosso verde e blu) in un uno solo, ad ognuno di questi colori
corrisponde uno dei quattro pin del led, quello rimanente è il catodo (o l'anodo, dipende dal led che avete) che è comune ai tre.
Combinando tra loro i tre colori emessi dal led e variandone la luminosità (come già visto in [Fade]()) è possibile riprodurre una buona parte dello spettro dei colori visibili, accendendoli alla massima luminosità tutti insieme invece si ottiene una luce bianca.

### Colori a caso

Lo scopo di questo progetto, oltre che capire il funzionamento del led RGB, è imparare a generare numeri (pseudo)casuali con le funzioni messe a disposizione dal core di Arduino, e quale modo migliore per unire le due cose se non far lampeggiare il led con colori casuali?
Prima di iniziare a generare questi numeri però, per non ottenerli non proprio casuali, è necessario inizializzare il generatore di numeri random con un valore scelto casualmente, per fare ciò si utilizza la funzione `randomSeed` passando come parametro un numero casuale come ad esempio il valore ritornato da una `analogRead` su un pin vuoto.

Dopo aver fatto ciò è possibile passare a generare i numeri, Arduino mette a disposizione due funzioni, entrambe chiamate `random` ma che ricevono
un numero di parametri differente.
La prima `random(max)`, che è quella che usiamo in questo sketch, riceve come parametro il numero massimo da generare e restituisce un numero compreso tra __max__ e __0__, la seconda `random(min,max)` invece riceve come parametri il numero minimo da generare e il massimo e ritorna un numero compreso tra questi due valori.