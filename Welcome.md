

# Willkommen zum Hackathon 2023
Für den diesjährigen Hackathon stehen Mikrocontroller und Sensoren bereit.
Dieses Repository soll dir den Einstieg in die Thematik erleichtern :)

Ansprechpartner: Marco und Pawel


# Motivation
Auf Daten folgen Taten...

Im Herzen einer Smart City befinden sich Sensoren und Mikrocontroller, die ihre Umwelt aufnehmen und daraus Daten generieren. Diese Daten fließen in Echtzeit in die Rathäuser, zu den Bürgern oder zur städtischen Infrastruktur. Sie sind die Grundlage für neue Anwendungen, die das Leben der Stadtbewohner ganz konkret verbessern sollen.

Wir vom Verein Digitale Oberlausitz e.V. glauben, es gibt in den Städten eine ganze Menge Möglichkeiten, wo mehr Daten mehr helfen könnten. Doch was sind das für Möglichkeiten? Wo liegen die Datenschätze, die gehoben werden möchten?

Das ist unsere diesjährige Challenge! Welche Daten könnten Rathäusern helfen, ihre Stadt zu gestalten? Von welchen Daten würden die Bewohner profitieren? Welche Prozesse könnten damit angestoßen werden?



# Übersicht
Wir bieten folgende Sensoren an:

- Abstand
- Bodenfeuchte
- Brennbare Gase
- Lichtstärke
- Luftdruck
- Luftfeuchtigkeit
- Luftqualität
- Regentropfen
- RGB-Farbspektrum
- Schallpegel
- Temperatur

Dazu bieten wir folgenden Mikrocontroller an:
- "ESP32-S DevKit C V2" mit "ESP32 WROOM-32" Chipsatz
- mit WLAN 802.11 b/g/n 2.4Ghz
- mit Bluetooth Classic & Low Energy (BLE)
- I2C, SPI, UART, GPIO, ...
- verarbeitet analoge und digitale Sensorsignale
- 3.3V und 5V Versorungs-und Betriebsspannung
- Programmierbar über Micro-USB per Arduino und C

# Installation

## Arduino Studio

## Breadboard beschalten

## Zwei Mikrocontroller betreiben
Breadboard zusammenstecken


# Mikrocontroller
Stromaufnahme: bis zu 500mA, wobei WLAN am meisten Strom zieht
WLAN Code Snippet
Bluetooth musst du herausfinden :)

## Daten versenden
WLAN
HiveMQ
Azure: nein
AWS: Pawel stellt euch das bereit
Eigene Lösung: gern!


# Stromversorgung

Die Stromversorgung des Mirkocontrollers und der Sensoren kann auf mehrere Arten geschehen.
Je nachdem, welchen Anwendungszweck du gerade brauchst, lässt sich die Stromversorgung umstellen.


## Zur Beachtung
- Niemals einen Sensor/Mikrocontroller von zwei Stromquellen gleichzeitig zu versorgen!
- Das MB102 Netzteil kann nur einen Mikrocontroller zuverlässig mit Strom versorgen. Hast du zwei Mikrocontroller, dann brauchst du zwei MB102 Netzteile.
- Der USB-Ausgang des MB102 kann den Mikrocontroller mit Strom versorgen.
- Bitte versorge den Mikrocontroller nur über seinen Micro-USB Port mit Strom. 
- Vergewissere dich stets, wie und womit du gerade deine Sensoren und Mikrocontroller mit Strom versorgst.

## MB102 Netzteil
+ - Verwechselung auf dem MB102
Jumper auf dem MB102
6,5V bis 12V Eingangsspannung
ca. 300 Milliampere
reicht für einen Mikrocontroller und paar Sensoren


## Stationär: Laptop-USB für Mikrocontroller und Sensoren
Situation:
- Mikrocontroller versorgt die Sensoren mit Strom
- Du willst den Mikrocontroller programmieren

Du brauchst:
- Micro-USB-Kabel

ToDo:
- Verbinde mit dem USB-Kabel Mikrocontroller und Laptop

![](img/Strom_via_Laptop.jpg)

## Stationär: Netzteil MB102 für Sensoren, Laptop-USB für Mikrocontroller
Situation:
- Mikrocontroller kann nicht alle Sensoren mit Strom versorgen
- Du willst den Mikrocontroller programmieren

Du brauchst:
- MB102 Netzteil
- Netzteil für die Steckdose
- USB-Kabel

ToDo:
- Verbinde mit dem USB-Kabel Mikrocontroller und Laptop
- Verbinde die Sensoren Stromversorgung mit der Breadboard-Schiene
- Verbinde das Netzteil für die Steckdose mit dem MB102 Netzteil

Achtung: Vergewissere dich stets, wie und womit du gerade deine Sensoren und Mikrocontroller mit Strom versorgst.

![](img/Strom_via_Netzteil_und_Laptop.jpg)


## Stationär: Netzteil MB102 für Mikrocontroller und Sensoren
Situation:
- Mikrocontroller kann nicht alle Sensoren mit Strom versorgen
- Der Mikrocontroller ist programmiert

Du brauchst:
- MB102 Netzteil
- Strom-Netzteil
- UBS-Kabel

ToDo:
- Verbinde mit dem USB-Kabel das MB102 Netzteil mit dem Mikrocontroller

![](img/Strom_via_Netzteil.jpg)


## Mobil: Powerbank-USB für Mikrocontroller und Sensoren
Situation:
- Der Mikrocontroller ist programmiert
- Mikrocontroller versorgt die Sensoren mit Strom
- Du willst mobil Daten sammeln

Du brauchst:
- Deine 5V Powerbank, mit der du auch dein SmartPhone lädst
- USB-Kabel

ToDo:
- Verbinde mit dem USB-Kabel deine Powerbank mit dem Mikrocontroller
- Achtung: Manche Powerbanks können sich wegen der geringen Stromaufnahme des Mikrocontrollers von selbst abschalten.
- Achtung: Powerbanks nicht für den Dauerbetrieb ausgelgegt. Alternativ nutze Batterien.

![](img/Strom_via_Powerbank.jpg)


## Mobil: Batterie für Mikrocontroller und Sensoren
Situation:
- Der Mikrocontroller ist programmiert
- Mikrocontroller und/oder das MB102-Netzteil versorgt die Sensoren mit Strom
- Du willst mobil Daten sammeln

Du brauchst:
- MB102-Netzteil
- USB-Kabel
- 9V-Batterie
- Batterie-Clip

ToDo:
- Verbinde mit dem USB-Kabel das MB102 Netzteil mit dem Mikrocontroller
- Vergewissere dich, dass dein MB102 Netzteil ausgeschalten ist (grüne LED ist AUS)
- Verbinde den Batterieclip mit der Batterie
- Verbinde den Batterieclip mit dem MB102

![](img/Strom_via_Batterie.jpg)