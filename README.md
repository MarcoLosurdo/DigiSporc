# DigiSporc

> The simple and economic parody of Digispark

![Il Purcello!!!](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/buta.png)

DigiSporc is a mini single-board microcontroller for ATtiny25/45/85 family that is **really easy to program and use** thanks to the application of a simple idea:

*its connector, plugged in the first female strip connector  of an Arduino Uno or Duemilanove (from the AREF to the digital port 8), has the pin already arranged in the right sequence to be able to be programmed with an Arduino in ISP mode.*

## 1.Intro
A few weeks ago, on Kickstarter, I saw a very interesting project called [Digispark](http://www.kickstarter.com/projects/digistump/digispark-the-tiny-arduino-enabled-usb-dev-board).

> Digispark - The micro-sized, Arduino enabled, usb development board

I'm not an electronic engineer, I just know a bit as the Arduino boards (and clones) works, so the first question I did was: «All the Arduino needs an FTDI chip; how is possible to program an ATtiny directly through a USB?».   
It seems that the "magic" happens thanks to a special bootloader and a data transmission technique called [bitbanging](http://en.wikipedia.org/wiki/Bit_banging). All this at the beginning it seemed very cool... but too unnecessarily complicated for someone like me who barely knows the difference between a LED and a capacitor.

Then, I remembered a [simple tutorial](http://hlt.media.mit.edu/?p=1695) published by the _MIT media lab_ about ATtiny programming using an Arduino. Giving it a further look I noticed that all pins required to program an ATtiny were on the strip connector Arduino that goes from AREF to digital 8, furthermore, the pins of a ATtiny are exactly eight as on that strip.  
So I came up with an idea: **why don't build an ATtiny45/85 board that can be plugged into an Arduino connector?**

Nothing could be easier! Et voilà:

![Proto boards](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/DigiSporc%20proto.jpeg)

That pic shows two prototypes (with and without the reset button). Into the repository you can find both named **DigiSporc** and **DigiSporc_Nano** (yes, I'm a sarcastic Apple fanboy).  
The prototype of DigiSporc in that pic, however, has no voltage regulator.

### 1.1.ATtiny and DigiSpork Pin-Outs
![ATtiny45-85pinout.png](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/ATtiny45-85pinout.png)
![DigiSporc_pinout.png](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/DigiSporc_pinout.png)

## 2.Getting Started
All you need to build your first DigiSporc (in DigiSporc_Nano configuration) is:

### 2.1.Hardware
* 1x 10K resistor (brown, black, orange, gold)
* 1x 1K resistor (brown, black, red, gold)
* 2x 0.1uF capacitors (but just one of them will be welded on the board, I promise!)
* 1x ATtiny85 (or 45)
* 1x 3mm LED
* 1x 1x8 pin headers (90° or straight)
* 1x 8x8 matrix board (but also an 8x6 is enough)

![Componenti](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/Lanciami_i_componenti.jpeg)

This tutorial was written by an Italian, so do not expect too many details (much less a perfect grammar). I'm not lazy, just don't wanna offend your intelligence.  
It is obvious that in order to complete the project you will need a **soldering iron**, some **tin wire**, an **Arduino** (Duemilanove or Uno) and an **USB cable** too.  
If you have no idea how to read a schematic or to make a circuit on a matrix board: search on Google.  
The internet is full of tinkering tutorials and I do not want to add another one.
 
...Ok, I'm lazy. Do your best, I trust you!

### 2.2.Software
* [Arduino IDE](http://arduino.cc/en/Main/Software).
* [ATtiny library](https://github.com/damellis/attiny/zipball/Arduino1)
* My version of [ArduinoISP](https://raw.github.com/MarcoLosurdo/DigiSporc/master/ArduinoISP_per_DigiSporc.ino)

#### 2.2.1.Installing ATtiny support in 37 easy steps:
1. Locate your Arduino sketchbook folder (start **Arduino IDE** and watch in the preferences);
1. if non exists, create a new sub-folder **hardware** in the sketchbook folder;
1. copy the attiny folder from inside the .zip to the **hardware** folder (you should obtain a structure like _Documents/Arduino/hardware/attiny_ that contains the file **boards.txt** and another folder called variants);
1. restart the Arduino IDE;
1. you should see ATtiny entries in the _Tools > Board_ menu;
1. the steps are just 5, not 37. I was joking. Move on.

## 3.ATtiny setup
1. Connect and select your Arduino from _Tools > Boards_ menu (e.g. **Arduino Uno**) and the right serial port (if you have a problem already at this step, please refer to the [official Arduino IDE guide](http://arduino.cc/en/Guide/HomePage));
1. connect and upload [ArduinoISP per DigiSporc](https://raw.github.com/MarcoLosurdo/DigiSporc/master/ArduinoISP_per_DigiSporc.ino) onto your Arduino board;
1. select your DigiSporc microcontroller from the _Tools > Boards_ menu (e.g. **ATtiny85 8 MHz**);
![Menu with ATtiny](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/ATtiny-Boards-Menu.png)
1. Select **Arduino as ISP** from the _Tools > Programmer_ menu;  
![ArduinoAsISP_menu.png](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/ArduinoAsISP_menu.png)
1. plug a 0.1uF capacitor between Arduino's RESET and GND (sometimes it is unnecessary, but it is always better to do);  
![DigiSporc_plugged.jpeg](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/capacitor_ResetGND.jpeg)
1. plug your DigiSporc into the AREF–DIGITAL8 slot;  
![DigiSporc_plugged.jpeg](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/DigiSporc_plugged.jpeg)
1. run the **Burn Bootloader** command from the Tools menu.  
![scrivi_bootloader_menu.png](https://raw.github.com/MarcoLosurdo/DigiSporc/master/pic/scrivi_bootloader_menu.png)

You need to do this **once** for every ATtiny.  
This doesn’t burn a bootloader onto the ATtiny, just configures the fuse bits of the microcontroller so it runs at 8 MHz.

## 4.Programming the DigiSporc for the first time
If you've restarted the Arduino IDE or changed something, repeat the steps from 1 to 6 as above for the ATtiny setup, then:

1. Open the **Blink** sketch from the _File > Examples > Basics_ menu;
1. edit the sketch and change the pin numbers from 13 to 0;  
`int led = 13;` → `int led = 0;`
1. upload the sketch and enjoy your blinking LED (if the LED don't blinks, something gone wrong).

## 6.Notes
* On the Arduino used as ISP programmer, still possible to run  the original version (supplied with the Arduino IDE) of **Arduino ISP**. But will be necessary to manually perform the connection between the 5V pin of Arduino and DigiSporc to provide the power supply;
* **sporc** it's the abbreviation of the italian word "sporco" (dirty).

## 7.Credits
- The project is based on the tutorial [Programming an ATtiny w/ Arduino 1.0.1](http://hlt.media.mit.edu/?p=1695) by MIT media lab.
- Many thanks to the people of [Tokyo Hackerspace](http://tokyohackerspace.org/) for any advices, but especially for the unexpected enthusiasm with which they welcomed the project.
- I’m sorry not to be able to thank guys DigiSpark, but at the time of publication of my project on Github, they had not yet published nothing of their "open hardware" board… probably, they were too busy to collect their quarter of a million dollars on KickStarter :D #LOL

## 8.Licence
DigiSporc (c) 2012, Marco Losurdo  
This project is realeased under the [CC-BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/us/) License.