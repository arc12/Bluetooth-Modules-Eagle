# Bluetooth Modules Eagle CAD Files
"Breakout" boards designed for HM10 and HM11 Bluetooth (BT) modules and pin-equivalent clones (etc) based on TI CC2540/2541 SoC.

These are intended to be usable for both breadboard prototyping and as modules for "finished" items (although admittedly in a DIY concept). Unlike breakouts on the open market, it is strictly a 3.3V approach. Both modules have a 5-pin header exposing the "debug" interface pins of the CC254x which can be used for loading new firmware (see notes below) and probably for actual debugging operations with a suitable IDE. The 5-pin header is semi-detached from the rest of the board due to a milled slot so that it can be cut off if not required (but pay attention to making sure the cut copper tracks don't have short-cuts.

As a "finished" item, the concept for the two boards differs:
- For the HM11 based board, the main header is arranged such that the central 6 pins match the pinout of popular USB-Serial boards based on CH340. The intention is that the BT board is plugged into the same header as is used for loading the firmware and is used to provide wireless serial output from a separate MCU and its associated sensors, or to provide serial input for control etc. Notice that there is a cuttable (and re-solderable) link adjacent to the header pins where the CH340 has DTR and RTS/CTS pins. Cut these if these are being used for bootloader control.
- For the HM10 based board, the scenario in mind is that the CC254x is used without a controlling MCU, with its I/O pins being used for various sensors or output connected to the main header.

Each board has one resistor and one capacitor as 1206 size SMD pads. These are optional; the capacitor is good practice for power supply and the resistor is intended for the "finished" scenarios.

## Changing Firmware
This is relevant to "clone" modules, although it may not work on all clones (definitely not if the CC254x is not genuine).

There are two fairly easy approaches:
- Using an ESP8266. See: https://github.com/Jason2866/CCLoader
- Using a Raspberry Pi. See: https://github.com/exotulip/CC2541-programmer

There are a lot of people who have essentially re-hashed the ESP8266 instructions and published online and the arduino forum is full of various accounts of success or failure. Using the boards presented here, with 3.3V native devices such as the RPi and ESP8266 should make life easier.