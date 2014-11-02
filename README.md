# Cozir CO2 Sensor Arduino Library

This library was originally authored by [DirtGambit](http://forum.arduino.cc/index.php?action=profile;u=47469).

The version of this library was found in an Arduino forum post:  http://forum.arduino.cc/index.php?topic=91467.msg1793827#msg1793827

The datasheet for the Cozir sensors is available on:

* [CO2Meters.com](http://www.co2meters.com/Documentation/AppNotes/AN128-%20Cozir_Arduino.pdf)
* [Scribd](https://www.scribd.com/doc/245203963/AN128-Cozir-Arduino)

## Example Sketch

```cpp
#include <SoftwareSerial.h>
#include "cozir.h"

SoftwareSerial nss(2,3);
COZIR czr(nss);

void setup()
{
 Serial.begin(9600);
 delay(5000);
 //czr.SetOperatingMode(CZR_POLLING);
 //czr.SetOperatingMode(CZR_STREAMING);
 //czr.CalibrateFreshAir();
// czr.SetDigiFilter(64);
}

void loop()
{
 delay(4000);
 float t = czr.Celsius();
 float f = czr.Fahrenheit();
 float h = czr.Humidity();
 int c = czr.CO2();
 int digi = czr.GetDigiFilter();

 Serial.print("Celcius : ");Serial.println(t);
 Serial.print("Fahrenheit : ");Serial.println(f);
 Serial.print("Humidity : ");Serial.println(h);
 Serial.print("CO2 : ");Serial.println(c);
 Serial.print("Digital Filter : ");Serial.println(digi);
 Serial.println("");
}
```
