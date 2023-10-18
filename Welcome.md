

# Willkommen zum Hackathon 2023
Für den diesjährigen Hackathon stehen Mikrocontroller und Sensoren bereit. Dieses Repository soll dir den Einstieg in die Thematik erleichtern :)

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
Die Mikrocontroller sind dafür ausgelegt dezentral Daten zu erfassen - eben in der Stadt verteilt. Es gibt mehrere Wege, wie die Daten zu deiner Applikation gelangen können.

### WLAN
Die Mikrocontroller können sowohl eigene WLANs aufmachen, als sich auch mit bestehenden WLANs verbinden.
Nutze das Veranstalter-WLAN. Solltest du mobil unterwegs sein, mache ein Hotspot mit deinem SmartPhone auf.

### MQTT Broker
MQTT ist ein leichtgewichtiges Protokoll zum energiesparenden und einfachen versenden von Nachrichten.
Nutze einen Online-MQTT-Server ("Broker") um Daten an einen zentralen Ort zu versenden. Von dort kann ein MQTT-Client (deine Applikation) sie wieder abholen.

Beispiele sind:
- **HiveMQ Serverless** (https://www.hivemq.com/pricing/) in weniger als 5 Minuten erstellt, wenn du einen GitHub Account hast. In Verbindung mit ESP32 gibt es Tutorials im Netz.

- **AWS**: Pawel stellt euch einen AWS MQTT Broker bereit. Besonders interessant, wenn ihr einen Blick in Cloud-Technologien erhaschen wollt.

### HTTP
Mit **https://dweet.io/play/** gibt es eine Möglichkeit Nachrichten im HTTP-Format an dweet zu senden und wieder abzuholen.

### Eigene Lösung
Fällt dir eine Lösung ein, die für dich besser geeignet ist? Do it!

### Alternativen/Ausblick: 
Steht uns für diesen Hackathon leider nicht bereit, aber LoRaWan ist eine Technologie um möglichst energiesparsam Daten über große Distanzen zu verschicken. Quasi am Mobilfunknetz "vorbei" auf einer anderen Wellenlänge. Bist du am Aufbau einer größeren IoT / Smart City Lösung interessiert, lohnt sich der Einstieg auf alle Fälle!

# Stromversorgung

Die Stromversorgung des Mirkocontrollers und der Sensoren kann auf mehrere Arten geschehen.
Je nachdem, welchen Anwendungszweck du gerade brauchst, lässt sich die Stromversorgung umstellen.
Wir haben dazu mehrere "Ausbaustufen" für die Stromversorgung vorbereitet.


## Zur Beachtung
Nutzt du unsere Hardware, müssen wir dich auf folgende Regeln hinweisen, um Schäden an Hardware und Teilnehmer*Innen zu vermeiden:

- **Versorge einen Sensor und/oder Mikrocontroller niemals von zwei Stromquellen gleichzeitig!**
- **Bitte betreibe den Mikrocontroller nur über seinen Micro-USB Port mit Strom.** 
- **Das MB102 Netzteil kann nur einen Mikrocontroller zuverlässig mit Strom betreiben.** Hast du zwei Mikrocontroller, dann brauchst du zwei MB102 Netzteile.
- **Vergewissere dich stets, wie und womit du gerade deine Sensoren und Mikrocontroller mit Strom versorgst.**

## MB102 Netzteil
Das MB102 Netzteil kann einen Mikrocontroller und ein paar Sensoren mit Strom versorgen (ca. 300 bis 500mA Ausgabe). Das MB102-Netzteil wird auf das Breadboard gesteckt, sodass beide Schienen mit Strom versorgt werden.

Über Jumper-Stecker kann zwischen 0V, 3.3V und 5V je Stromschiene unterschieden werden. Bitte stecke die Jumper nur im ausgeschalteten Zustand um. Das MB102 Netzteil kann über den weißen Schalter neben der grünen LED ein-und ausgeschalten werden.

Um das MB102 Netzteil mit Strom zu versorgen, stehen Batterien und Netzteile für die Steckdose bereit. Suche dir die passende Lösung in den Nachfolgekapiteln aus.


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