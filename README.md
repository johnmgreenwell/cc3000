# Adafruit CC3000 Library

This is a library for the Adafruit CC3000 WiFi Breakouts etc

Designed specifically to work with the Adafruit CC3000 Breakout 
  ----> https://www.adafruit.com/products/1469

These modules use SPI to communicate, 6 pins are required to interface

Adafruit invests time and resources providing this open source code, 
please support Adafruit and open-source hardware by purchasing 
products from Adafruit!

Check out the links above for our tutorials and wiring diagrams 

Arduino library Written by Limor Fried & Kevin Townsend for Adafruit Industries.  
CC3000 host core written by TI

To download. click the DOWNLOADS button in the top right corner, rename the uncompressed folder Adafruit_CC3000 
Check that the Adafruit_CC3000 folder contains Adafruit_CC3000.cpp and Adafruit_CC3000.h

Place the Adafruit_CC3000 library folder your *arduinosketchfolder*/libraries/ folder. 
You may need to create the libraries subfolder if its your first library. Restart the IDE.

NOTE: the 'SendTweet' example currently DOES NOT WORK due to Twitter API changes. The code is being kept for posterity in case a workaround can be developed.

Modified by John Greenwell to adapt driver for custom HAL support, 2024.

## Usage

NOTE: Full driver modification is not complete at present state, though the source files have been moved into the PeripheralIO namespace for compatibility.

For this modified version, the following hardware abstraction layer (HAL) requirements must be satisfied:

* A header file `hal.h` providing access to HAL namespace classes and methods.
* A `GPIO` class within the `HAL` namespace with the following methods:
  - Set pin mode: `pinMode(uint8_t mode)`
  - Write logic level to pin: `digitalWrite(uint8_t val)`
* A `SPI` class within the `HAL` namespace with the following methods:
  - Perform SPI data transfer: `transfer(uint8_t data)`
* A millis() function in the HAL namespace that returns an accurate milliseconds counter to be used for timing.

Some further requirements may also be found. Typically, these will mirror the Arduino framework and should be added to `hal.h`.
* For example, this driver depends on the Arduino framework "Stream" class, and an equivalent will need to be provided, in the HAL or otherwise.

