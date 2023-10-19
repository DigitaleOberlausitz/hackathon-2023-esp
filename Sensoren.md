# Sensoren
Die Liste der bereitstehenden Sensoren:

| Messung von      | Bezeichnung                          |
|------------------|--------------------------------------|
| Abstand          | HC-SR04-P Ultraschall-Modul Entfernungsmesser |
| Bodenfeuchte     | AZDelivery Bodenfeuchte-Sensor Modul |
| Brennbare Gase   | MQ-2 Gas Sensor                      |
| Lichtstärke      | KY-018 Foto LDR Sensor               |
| Luftdruck        | WaveShare BME280 und Adafruit BME688 |
| Luftfeuchtigkeit | WaveShare BME280 und Adafruit BME688 |
| Luftqualität     | WaveShare BME280 und Adafruit BME688 |
| Regentropfen     | AZDelivery Regentropfen Sensor Modul |
| RGB-Farbspektrum | GY-TCS34725 RGB Color Sensor         |
| Schallpegel      | GY-MAX9814 Sound Sensor Module       |
| Temperatur       | WaveShare BME280 und Adafruit BME688 |


## Informationen und Codebeispiele
Hast du die Modellnamen, findest du _eigentlich_ genügend Infos im Internet.
Trotzdem sind uns ein paar Informationen und Code-Beispiele bekannt, die wir dir nicht vorenthalten möchten.
Codebeispiele sind für Arduino IDE geschrieben.

### WLAN

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

### Regentropfensensor
**Betriebsspannung**: 3.3V oder 5V

**Stromaufnahme**: 8mA

**Pinbelegung**: VCC = Versorgungsspannung = "Plus", GND = Erdung = "Minus", DO = Digital Output, AO = Analog Output

**Ausgangssignale**: Analog und Digital

Das analoge Signal ist dem digitalen vorzuziehen. Analog gibt eine kontinuierliche Zahl wieder, mit der sich die "Nässe" viel genauer bestimmen lässt. Der Wert liegt zwischen 0 (trocken) und 4095 (nass). Das digitale Signal sagt dir blos "hey ich bin genug nass".

Das kleine graue Kreuz ist ein Poti. Drehen im Uhrzeigersinn = erhöht Empfindlichkeit. Drehen gegen Uhrzeigersinn = verringert Empfindlichkeit.

```cpp
#define DIGITAL_PIN 25
#define ANALOG_PIN 35

uint16_t rainVal;
boolean isRaining = false;

void setup() {
  Serial.begin(9600);
  pinMode(DIGITAL_PIN, INPUT);
  pinMode(SENSOR_POWER, OUTPUT);
}
void loop() {
  delay(10);
  rainVal = analogRead(ANALOG_PIN);
  isRaining = digitalRead(DIGITAL_PIN);
  long moistureInPercent = map(rainVal, 0, 4095, 100, 0);
}
```

### Adafruit BME688 und Waveshare BME280
Diese Sensoren können direkt ausgelesen werden oder über die Bosch-Library BSEC2. Die BSEC2-Library is closed-sourced, aber bietet zusätzliche Funktionen. Zum Beispiel eine Integration mit BME AI-Studio Desktop (nur BME688).

Um die BSEC2 Library einzusetzen, folge diesem Tutorial auf GitHub:
https://github.com/BoschSensortec/Bosch-BSEC2-Library

Achtung: Der BME688 und BME280 brauchen ein paar Minuten um ihre Messungen zu präzisieren. Besonders beim Erstbetrieb können die Temperatur und Luftqualität-Werte um 20%(?) falsch liegen. Lasse die Sensoren ruhig 15+ Minuten durchgängig laufen, damit sich die Werte einpegeln.

Ein guter Codebeispiel gibt es hier:
https://github.com/boschsensortec/Bosch-BSEC2-Library/blob/master/examples/generic_examples/basic/basic.ino

Ergänze im obigen Beispiel eine fehlende Zeile und verbinde den Mikrokontroller mit dem BME688 über diese zwei Pins!
```cpp
[...]
/* Initialize the communication interfaces */
Serial.begin(115200);
Wire.setPins(21,22); //Diese Zeile fehlt in Basic.ino!!!
Wire.begin();
[...]
```

Mit dem BME688 und BME AI-Studio Desktop ist es möglich eine neuronales Netz zu trainieren:
https://www.bosch-sensortec.com/software-tools/software/bme688-software/
Wenn du einen guten Usecase hast, warum nicht?


### Hilfstool: I2CScanner
Der I2CScanner zeigt dir die I2C Adresse aller angeschlossenen Sensoren zurück. Damit findest du auch heraus, ob der Sensor richtig angeschlossen ist indem er dir eine Rückmeldung über I2C gibt.

```cpp
// --------------------------------------
// i2c_scanner
//
// Version 1
//    This program (or code that looks like it)
//    can be found in many places.
//    For example on the Arduino.cc forum.
//    The original author is not know.
// Version 2, Juni 2012, Using Arduino 1.0.1
//     Adapted to be as simple as possible by Arduino.cc user Krodal
// Version 3, Feb 26  2013
//    V3 by louarnold
// Version 4, March 3, 2013, Using Arduino 1.0.3
//    by Arduino.cc user Krodal.
//    Changes by louarnold removed.
//    Scanning addresses changed from 0...127 to 1...119,
//    according to the i2c scanner by Nick Gammon
//    https://www.gammon.com.au/forum/?id=10896
// Version 5, March 28, 2013
//    As version 4, but address scans now to 127.
//    A sensor seems to use address 120.
// Version 6, November 27, 2015.
//    Added waiting for the Leonardo serial communication.
//
//
// This sketch tests the standard 7-bit addresses
// Devices with higher bit address might not be seen properly.
//
 
#include <Wire.h>
 
 
void setup()
{
  Wire.begin();
 
  Serial.begin(9600);
  while (!Serial);             // Leonardo: wait for serial monitor
  Serial.println("\nI2C Scanner");
}
 
 
void loop()
{
  byte error, address;
  int nDevices;
 
  Serial.println("Scanning...");
 
  nDevices = 0;
  for(address = 1; address < 127; address++ )
  {
    // The i2c_scanner uses the return value of
    // the Write.endTransmisstion to see if
    // a device did acknowledge to the address.
    Wire.beginTransmission(address);
    error = Wire.endTransmission();
 
    if (error == 0)
    {
      Serial.print("I2C device found at address 0x");
      if (address<16)
        Serial.print("0");
      Serial.print(address,HEX);
      Serial.println("  !");
 
      nDevices++;
    }
    else if (error==4)
    {
      Serial.print("Unknown error at address 0x");
      if (address<16)
        Serial.print("0");
      Serial.println(address,HEX);
    }    
  }
  if (nDevices == 0)
    Serial.println("No I2C devices found\n");
  else
    Serial.println("done\n");
 
  delay(5000);           // wait 5 seconds for next scan
}
```
