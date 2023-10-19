

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

# Mikrocontroller
Stromaufnahme: bis zu 500mA, wobei WLAN am meisten Strom zieht
WLAN Code Snippet
Bluetooth musst du herausfinden :)

## Daten versenden
Die Mikrocontroller sind dafür ausgelegt dezentral Daten zu erfassen - eben in der Stadt verteilt. Es gibt mehrere Wege, wie die Daten zu deiner Applikation gelangen können.

### WLAN
Die Mikrocontroller können sowohl eigene WLANs aufmachen, als sich auch mit bestehenden WLANs verbinden.
Nutze das Veranstalter-WLAN. Solltest du mobil unterwegs sein, mache ein Hotspot mit deinem SmartPhone auf.

```cpp
#include <WiFi.h>

const char* ssid = "meinWLAN"; 
const char* password = "deinPasswort";

WiFi.mode(WIFI_STA);
WiFi.begin(ssid, password);
  
while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi..");
    Serial.println("Status:" + WiFi.status());
}
Serial.println("Connected to the WiFi network");
```

### MQTT Broker
MQTT ist ein leichtgewichtiges Protokoll zum energiesparenden und einfachen versenden von Nachrichten. Ursprünglich entwickelt für die Raumfahrt!


Nutze einen Online-MQTT-Server ("Broker") um Daten an einen zentralen Ort zu versenden. Von dort kann ein MQTT-Client (= deine Applikation) sie wieder abholen.

In Verbindung mit ESP32 gibt es Tutorials und Libraries im Netz. (Beispiel: https://github.com/knolleary/pubsubclient und https://www.survivingwithandroid.com/esp32-mqtt-client-publish-and-subscribe/)

Beispiele für MQTT Broker sind:
- **HiveMQ Serverless Free** (https://www.hivemq.com/pricing/) ist kostenlos und in weniger als 5 Minuten erstellt, wenn du einen GitHub Account hast.

- **AWS**: Pawel stellt euch einen AWS MQTT Broker bereit. Besonders interessant, wenn du einen Blick in Cloud-Technologien erhaschen willst.

### HTTP
Mit **https://dweet.io/play/** gibt es eine Möglichkeit Nachrichten im HTTP-Format an dweet zu senden und wieder abzuholen.

### Eigene Lösung
Fällt dir eine Lösung ein, die für dich besser geeignet ist? Do it!

### Ausblick: 
Steht uns für diesen Hackathon leider nicht bereit, aber LoRaWan ist eine Technologie um möglichst energiesparsam Daten über Kilometer zu verschicken. Quasi am Mobilfunknetz "vorbei" auf einer anderen Wellenlänge. Bist du am Aufbau einer umfangreichen IoT / Smart City Lösung interessiert, lohnt sich der Einsatz auf alle Fälle!


# Breadboard
Ein Breadboard (Steckplatine) hilft dir deine Technik zusammenzuhalten :)

Es bietet zwei stromführende Schienen an den Seiten. Von dort können deine Sensoren mit Strom versorgt werden. Der Strom kommt vom MB102-Netzteil. (Siehe dazu Datei [Stromversorgung.md](Stromversorgung.md))
  
Mittig liegen die Stecker, wo die Pins des Mikrocontrollers, Sensoren und Kabel eingesteckt werden können. Diese sind immer über 5 nebeneinanderliegenden Steckplätze verbunden.

![](img/Ein_Breadboard.jpg)

**Achtung: Die "blaue-rote-Plus-Minus Markierung" an den Stromschienen muss nicht zwangsläufig mit dem tatsächlichen Stromlauf zusammenhängen!** Das MB102-Netzteil gibt hier den Ton an! Achte auf die + und - Markierung vom MB102-Netzteil.


## Zwei Breadboards verbinden
Du kannst zwei Breadboards an den Seiten zusammenstecken. Am besten du entfernst eine der beiden zusammenliegenden Stromschienen, damit das MB102-Netzteil und der Mikrocontroller gut dazwischenpassen.

![](img/Zwei_Breadboards.jpg)

Auf diese Weise passen auch zwei Mikrocontroller und zwei MB102-Netzeil auf zwei Breadboards.

**Achtung: Setze den Jumper der MB102-Netzteile für die mittlere Stromschiene auf 0V.**

**Achtung: Du hast hier Hebelkräfte am Wirken. Sei vorsichtig, keine Pins des Mikrocontrollers zu verbiegen.**