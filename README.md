/* The MIT License (MIT)

Copyright (c) 2018 David Payne

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/

# Printer Monitor (OctoPrint 3D Printer Monitor)

## Features:
* Displays the print status from OctoPrint Server
* Estimated time remaining
* Time Printing
* Percentage complete
* Progress bar
* Screen turns off when printer is turned off or disconnected
* Screen turns on when printer is Operational or connected
* Option to display a clock screen instead of sleep mode
* Sample rate is every 60 seconds when not printing
* Sample rate is every 10 seconds when printing
* Fully configurable from the web interface (not required to update Settings.h)
* Supports OTA (loading firmware over WiFi connection on same LAN)
* Basic Athentication to protect your settings
* Video: https://youtu.be/niRv9SCgAPk

## Required Parts:
* Wemos D1 Mini: https://amzn.to/2qLyKJd
* 0.96" OLED I2C 128x64 Display (12864) SSD1306:  https://amzn.to/2JDEAUF

## Wiring for the Wemos D1 Mini to the I2C SSD1306 OLED
SDA -> D2  
SCL -> D5  
VCC -> 5V+  
GND -> GND-  

## 3D Printed Case by Qrome:  
https://www.thingiverse.com/thing:2884823

## Compiling and Loading to Wemos D1 Mini
It is recommended to use Arduino IDE.  You will need to configure Arduino IDE to work with the Wemos board and USB port and installed the required USB drivers etc.  
* USB CH340G drivers:  https://wiki.wemos.cc/downloads
* Enter http://arduino.esp8266.com/stable/package_esp8266com_index.json into Additional Board Manager URLs field. You can add multiple URLs, separating them with commas.  This will add support for the Wemos D1 Mini to Arduino IDE.
* Open Boards Manager from Tools > Board menu and install esp8266 platform (and don't forget to select your ESP8266 board from Tools > Board menu after installation).
* Select Board:  "WeMos D1 R2 & mini"

**Packages** -- the following packages and libraries are used (download and install):  
ESP8266WiFi.h  
ESP8266WebServer.h  
ArduinoJson.h  --> https://github.com/bblanchon/ArduinoJson  
WiFiManager.h --> https://github.com/tzapu/WiFiManager  
ESP8266mDNS.h  
ArduinoOTA.h  --> Arduino OTA Library  
"SSD1306Wire.h" --> https://github.com/ThingPulse/esp8266-oled-ssd1306  
"OLEDDisplayUi.h"  

## Initial Configuration
You will can update the **Settings.h** file with your OctoPrint API Key or do it from the web interface.  
* Your OctoPrint API Key from your OctoPrint -> User Settings -> Current API Key  

NOTE: The settings in the Settings.h are the default settings for the first loading. After loading you will manage changes to the settings via the Web Interface. If you want to change settings again in the settings.h, you will need to erase the file system on the Wemos or use the “Reset Settings” option in the Web Interface.  

## Web Interface
The Printer Monitor uses the **WiFiManager** so when it can't find the last network it was connected to 
it will become a **AP Hotspot** -- connect to it with your phone and you can then enter your WiFi connection information.

After connected to your WiFi network it will display the IP addressed assigned to it and that can be 
used to open a browser to the Web Interface.  Everything can be configured there.

<p align="center">
  <img src="/images/shot_01.png" width="200"/>
  <img src="/images/shot_02.png" width="200"/>
  <img src="/images/shot_03.png" width="200"/>
  <img src="/images/shot_04.png" width="200"/>
</p>

## Contributors
David Payne  
Daniel Eichhorn -- Author of the TimeClient class and OLEDDisplayUi

[![Watch the video](/images/video_print_monitor.png)](https://youtu.be/niRv9SCgAPk)
![Printer Monitor Temps](/images/temperatures.jpg)  
![Printer Monitor Time Remaining](/images/time_remaining.jpg)  
![Printer Monitor Printing Time](/images/printing_time.jpg)
