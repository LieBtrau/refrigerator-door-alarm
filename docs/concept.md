# Detection of open/closed door
Using normally closed reed-relay.  As long as the door is closed, the magnet will be in proximity with the relay and the contact will be open.
This contact will conduct the current that powers on the device.  When the door is closed, no current will be drawn.  This satisfies low power use.

# Audible alert
## Buzzer component
### Standard SMD buzzer
* Electro-mechanical : 8x8mm

### Buzzer with feedback
* might be louder, but harder to construct

# Visual notification
* dual color LED : RED for LOBATT, GREEN to signal that the device is still operational

# MCU

ATtiny204 : 
* 8 pins should be enough
* low power
* low cost
* good software support
* good documentation
* works from 1.8V to 5.5V
* programming with UPDI (single pin)

## Reset connection
[AN2519 AVR® Microcontroller Hardware Design Considerations](https://ww1.microchip.com/downloads/en/Appnotes/AN2519-AVR-Microcontroller-Hardware-Design-Considerations-00002519B.pdf)
* Add 10k pull up on reset, but don't add a pull down capacitor because it would thwart UPDI programming.

## Supervisory circuit
* internal BOD removes the need for a voltage supervisor.

## Programming connector
SKEDD

## Programmer
[DIY UPDI USB programmer which can be made with cheap hardware](https://daumemo.com/diy-updi-usb-programmer-which-can-be-made-with-cheap-hardware/)

# Power 
## Battery
### Li-Ion : 
* no LDO required for the ATtiny204
* cheap
* small
* can deliver large current

### ~~CR2032~~
* current delivery for the buzzer will be problematic.  The output voltage will likely drop significantly.

# Battery protection
UVLO, short-circuit

# Connectors
* JST-PH for battery

# Switches
## Slide switch
* C&K PCM12SMTR

## Reed switch

# LED
* Reverse mount bicolor R&G LED
* Wuerth 156125RV73000 / Lite-On LTST-C235KGKRKT / Dialight 5977703607F

# Housing
* to be developed in Fusion360.
* It should be possible to remove the electronics from the housing without having the remove the housing from its point of installation.
* Concept:
  * Open box stuck against the refrigerator
  * The PCB is the lid of the box.  All electronics mounted on the back side of the PCB.
  * The PCB fits on the housing (small rim around the PCB for easy alignment.)

# Firmware
* [AN2447 Measure VCC/Battery Voltage Without Using I/O Pin on tinyAVR and megaAVR](https://ww1.microchip.com/downloads/en/Appnotes/00002447A.pdf)
* [PlatformIO setup for programming](https://github.com/LieBtrau/urban-edc-flashlight/tree/main/firmware/urban-edc-flashlight)