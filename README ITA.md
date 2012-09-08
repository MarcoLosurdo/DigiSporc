# DigiSporc

> La parodia semplice ed economica della Digispark

DigiSporc è un mini microcontroller su singola scheda basato sulla famiglia ATtiny25/45/85 – realmente facile da usare e programmare – grazie alla applicazione di una semplice idea:

**il suo connettore, inserito nel primo* connettore strip femmina di una scheda Arduino Uno o Duemilanove, ha i pin disposti già nella sequenza necessaria per poterne effettuare la programmazione tramite una Arduino in modalità ISP.**

*quello da AREF alla porta digitale n.8 per intenderci.

### ATtiny25/45/85 Microcontroller Pin-Outs
![ATtiny85 pinouts](http://hlt.media.mit.edu/wp-content/uploads/2011/10/ATtiny45-85.png)

### DigiSporc Pin-Outs
![DigiSporc pinouts](https://raw.github.com/MarcoLosurdo/DigiSporc/master/DigiSporc_pinout.png)

## Note
* Sulla Arduino dovrà girare la variante dello sketch [ArduinoISP modificata per la scheda DigiSporc](https://raw.github.com/MarcoLosurdo/DigiSporc/master/ArduinoISP_per_DigiSporc.ino), oppure, la versione originale fornita con la IDE. Ma in quest'ultimo caso si renderà necessario effettuare manualmente il collegamento fra il pin 5V della scheda Arduino e quello della DigiSporc per fornire l'alimentazione necessaria.

* Per programmare i microcontrollori della famiglia ATtiny25/45/85 occorre inserire nella cartella hardware la apposita libreria [ATtiny](https://github.com/damellis/attiny)) 

## Credits
* Il progetto è basato sul tutorial [Programming an ATtiny w/ Arduino 1.0.1](http://hlt.media.mit.edu/?p=1695) del MIT media lab.

* Infiniti ringraziamenti ai ragazzi del [Tokyo Hackerspace](http://tokyohackerspace.org/) per i vari consigli, ma soprattutto per l'inaspettato entusiasmo con cui hanno accolto il progetto.

## Licence
DigiSporc (c) 2012, Marco Losurdo  
This work is realeased under the [CC-BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/us/
) License.


