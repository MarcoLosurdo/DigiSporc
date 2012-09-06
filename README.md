# DigiSporc
> The simple and economic parody of Digispark

DigiSporc is a mini single-board microcontroller for ATtiny25/45/85 family that is ***really easy to program and use*** thanks to the application of a simple idea:

*its connector, plugged in the first female strip connector  of an Arduino Uno or Duemilanove (from the AREF to the digital port 8), has the pin already arranged in the right sequence to be able to be programmed with an Arduino in ISP mode.*


### ATtiny25/45/85 Microcontroller Pin-Outs
![ATtiny85 pinouts](http://hlt.media.mit.edu/wp-content/uploads/2011/10/ATtiny45-85.png)

### DigiSporc Pin-Outs
![DigiSporc pinouts](https://raw.github.com/MarcoLosurdo/DigiSporc/master/DigiSporc_pinout.png)

## Notes
* On the Arduino will run a variation of the sketch "ArduinoISP" customized for the DigiSporc, or the original version supplied with the Arduino IDE. But in the latter case it will be necessary to perform manually the connection between the 5V pin of Arduino and DigiSporc to provide the power supply.

* To program the microcontrollers ATtiny25/45/85, the [ATtiny](https://github.com/damellis/attiny) library should be inserted in the appropriate "hardware" folder on the Arduino IDE working dir.

## Credits
* The project is based on the tutorial [Programming an ATtiny w/ Arduino 1.0.1](http://hlt.media.mit.edu/?p=1695) by MIT media lab.

* Many thanks to the guys of [Tokyo Hackerspace](http://tokyohackerspace.org/) for any advices, but especially for the unexpected enthusiasm with which they welcomed the project.

## Licence
(c) 2012, Marco Losurdo  
This project is realeased under the [CC-BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/us/) License.