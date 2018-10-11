# HM-ES-PMSw1-Pl_GosundSP1     [![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

Umbau [Gosund SP1 bzw. BliTZWOLF SHP2](https://www.blitzwolf.com/Wifi-Smart-Socket-EU-p-244.html) zu HM-ES-PMSw1-Pl_SP1

Dies basiert auf der hervorragenden Arbeit von [pa-pa](https://github.com/pa-pa/AskSinPP) und [Jérôme](https://github.com/jp112sdl/Beispiel_AskSinPP).


# Hardware

### Bauteile

#### Reichelt

[Bestellliste](https://www.reichelt.de/my/)

Bauteil                  | Bestellnummer   | Anzahl | Kommentar
------------------------ | --------------- | ------ | ---------
C6                       | X5R-G0603 10/6  |   1    | -
C1, C2, C3, C8           | X7R-G0603 100N  |   4    | -
R1                       | RND 0603 1 10K  |   1    | -
...                      | ...             |   1    | -


#### Sonstiges

Bauteil | Bestellnummer            | Anzahl | Kommentar
------- | ------------------------ | ------ | ---------
U2      | CC1101 Funkmodul 868 MHz |   1    | z.B. [eBay](https://www.ebay.de/itm/272455136087)

~8,3 cm Draht als Antenne


### Programmieradapter
- 1x ISP (um den Bootloader zu brennen, z.B. [diesen hier](https://www.diamex.de/dxshop/USB-ISP-Programmer-fuer-Atmel-AVR-Rev2))


# Software

### Fuses


### Firmware

https://github.com/jp112sdl/Beispiel_AskSinPP/blob/master/examples/HM-ES-PMSw1-Pl/HM-ES-PMSw1-Pl.ino

Benötigt wird die AskSinPP aus dem master-Branch, der V3-Branch ist zu alt.


# Bauanleitung

Zuerst den ATmega auflöten, die Markierung (kleiner Punkt) muss zur Beschriftung U1 zeigen.
Danach die Kondensatoren und den Widerstand auflöten.

Mit einem Multimeter messen ob kein Kurzschluss zwischen VCC und GND besteht (mehrere 10 K Widerstand sind okay).

Den ISP Programmieradapter an die Lötaugen des CC1101 anschließen. Ein Adapterkabel vom 6-poligen ISP-Adapter auf eine 2 mm-Stiftleiste wird empfohlen :)


Pin am ISP-Kabel | Bedeutung
---------------- | ----------
1                | MISO
2                | VCC
3                | SCK
4                | MOSI
5                | Reset
6                | GND

# Bilder


[![Creative Commons Lizenzvertrag](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

Dieses Werk ist lizenziert unter einer [Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz](http://creativecommons.org/licenses/by-nc-sa/4.0/).
