# HM-ES-PMSw1-Pl_GosundSP1     [![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)     [![GitHub issues](https://img.shields.io/github/issues/stan23/HM-ES-PMSw1-Pl_GosundSP1.svg)](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/issues)

Umbau [Gosund SP1 bzw. BliTZWOLF SHP2](https://www.blitzwolf.com/Wifi-Smart-Socket-EU-p-244.html) zu HM-ES-PMSw1-Pl_SP1

Dies basiert auf der hervorragenden Arbeit von [pa-pa](https://github.com/pa-pa/AskSinPP) und [Jérôme](https://github.com/jp112sdl/Beispiel_AskSinPP).


*Achtung*: es kann verschiedene Versionen der Gosund/Blitzwolf-Stecker geben. Diese Platine passt bei folgender Version:

![Blitzwolf SHP2](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Blitzwolf_SHP2.jpg)


# Hardware

### Bauteile

#### Reichelt

[Bestellliste](https://www.reichelt.de/my/1519439)

Bauteil                  | Bestellnummer   | Anzahl | Kommentar
------------------------ | --------------- | ------ | ---------
C1                       | X5R-G0603 10/6  |   1    | -
C2 .. C6                 | X7R-G0603 100N  |   5    | -
R1                       | RND 0603 1 10K  |   1    | -
R2                       | RND 0603 1 1,0M |   1    | -
U1                       | ATMEGA 644PA-AU |   1    | -
Y1                       | CSTCE 8,00      |   1    | -
Verbinder zu U2          | MPE 156-1-032   |   1    | muss per Hand umgebogen werden
Verbinder zu U2          | SL 1X20G 2,00   |   1    | optional, hilfreich zum Anschließen des ISP


#### Sonstiges

Bauteil | Bestellnummer            | Anzahl | Kommentar
------- | ------------------------ | ------ | ---------
U2      | CC1101 Funkmodul 868 MHz |   1    | z.B. [eBay](https://www.ebay.de/itm/272455136087)

~8,3 cm Draht als Antenne


### Programmieradapter
- 1x ISP (z.B. [diesen hier](https://www.diamex.de/dxshop/USB-ISP-Programmer-fuer-Atmel-AVR-Rev2))


# Software

### Fuses
Ext:  0xFF
High: 0xD2
Low:  0xFF (für den internen Takt: 0xE2)

`C:\Program Files (x86)\Arduino\hardware\tools\avr\bin> .\avrdude -C ..\etc\avrdude.conf -p m644p -P com7 -c stk500 -U lfuse:w:0xFF:m -U hfuse:w:0xD2:m -U efuse:w:0xFF:m`


### Firmware

Projektverzeichnis: [HM-ES-PMSw1-Pl_GosundSP1](https://github.com/jp112sdl/Beispiel_AskSinPP/tree/master/examples/HM-ES-PMSw1-Pl_GosundSP1)

Benötigt werden die Bibliotheken [AskSinPP](https://github.com/pa-pa/AskSinPP) aus dem master-Branch, sowie die [HLW8012](https://github.com/xoseperez/hlw8012), die [MightyCore](https://github.com/MCUdude/MightyCore), die [EnableInterrupt](https://github.com/GreyGnome/EnableInterrupt) und [Low-Power](https://github.com/rocketscream/Low-Power).

![Einstellungen IDE](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/ArduinoIDE_Auswahl_Controller.png)



# Bauanleitung

Zuerst den ATmega auflöten, die Markierung (kleiner Punkt) muss zur Beschriftung U1 zeigen.
Danach die Kondensatoren und den Widerstand auflöten.

Mit einem Multimeter messen ob kein Kurzschluss zwischen VCC und GND besteht (mehrere 10 K Widerstand sind okay).

Den ISP Programmieradapter an die Lötaugen des CC1101 anschließen. Ein Adapterkabel vom 6-poligen ISP-Adapter auf eine 2 mm-Stiftleiste wird empfohlen :)

![ISP Anschluss](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Platine_ISP_Beschriftung.jpg)

Pin am ISP-Kabel | Bedeutung
---------------- | ----------
1                | MISO
2                | VCC
3                | SCK
4                | MOSI
5                | Reset
6                | GND



Anschließend kann das Funkmodul auf der Rückseite aufgelötet werden. Dabei gibt es verschiedene Möglichkeiten:
- mit Stift- und Buchsenleiste (abnehmbar)
- mit Stiftleiste

An den Antennenanschluss muss noch das 8,3 cm Drahtstück angelötet werden.

Mit einem FTDI USB-seriell-Adapter an den Lötpunkten RX, TX, 3.3 V und GND und mit einem Terminalprogramm kann man die Ausgabe beobachten. Es sollten schon *Ignore...*-Meldungen empfangen und angezeigt werden.

Als nächstes muss das überflüssige WLAN-Modul aus dem Gosund/Blitzwolf-Stecker ausgelötet und die neue Platine eingelötet werden. Der Antennendraht muss mit Heißkleber im Gehäuse befestigt werden, so dass er möglichst weit von 230 V entfernt ist!

Nach dem Zusammenbau kann der Anlernvorgang durch langes Drücken der einzigen Taste gestartet werden. Die Anlernprozedur wird durch langsames Blinken der blauen WLAN-LED angezeigt, der Erfolg durch schnelles Blinken.


# Kalibrierung

TBD


# Bilder

![ATmega](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Platine_Vorderseite_bestückt.jpg)
![eingelötet](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Platine_Rückseite_bestückt_1.jpg)
![eingelötet](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Platine_Rückseite_bestückt_2.jpg)
![eingelötet](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Platine_V2_bestückt.jpg)

![Einbau](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Einbau1.jpg)
![Einbau](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Einbau2.jpg)
![Einbau](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Einbau3.jpg)
![Einbau](https://github.com/stan23/HM-ES-PMSw1-Pl_GosundSP1/blob/master/Bilder/Einbau4.jpg)


[![Creative Commons Lizenzvertrag](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

Dieses Werk ist lizenziert unter einer [Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz](http://creativecommons.org/licenses/by-nc-sa/4.0/).
