---
title: Analisi dello sketch
---

### Utilizzare il sensore DS18B20

#### Librerie

Per utilizzare il __DS18B20__ abbiamo bisogno di installare due librerie:

   * OneWire, che implementa il protocollo usato dal sensore
   * DallasTemperature, per utilizzare il sensore

#### Inizializzazione

Dopo aver installato le librerie bisogna innanzitutto includerle, questo viene fatto nelle prime due righe:

      #include <OneWire.h>
      #include <DallasTemperature.h>

Definiamo il pin a cui sarà collegato il sensore con `#define ONE_WIRE_BUS 8`

Successivamente inizializziamo l'oggetto OneWire passandogli come parametro il pin a cui abbiamo collegato il sensore:

     OneWrite oneWire(ONE_WIRE_BUS)

Procediamo quindi ad inizializzare l'ogetto DallasTemperature con il quale ci interfacceremo con il sensore:

     DallasTemperature sensor(&oneWire)

Come parametro riceve il riferimento a __oneWire__ (che si indica con la &)

#### Leggere la temperatura

Per leggere la temperatura dal sensore utilizzeremo prima il metodo `requestTemperatures()`
Poi uno dei due metodi:

  * getTempCByIndex(index) restituisce la temperatura in Celsius (index nel nostro caso è 0)
  * getTempFByIndex(index) restituisce la temperatura in Farenight (index nel nostro caso è 0)