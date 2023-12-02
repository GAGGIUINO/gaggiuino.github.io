> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

>[!Note]
>BOM and 3D printed parts for PCBv3 have moved to the [Home page](README.md#bill-of-materials)

# Considerations
* PCBs are compatible with 3PLN stock wiring integration or custom wiring, though custom wiring is recommended for certain machines (see the [compatibility table](README.md#Compatibility))
* PCB v3 is suitable for most single-boiler espresso machines. PCB v2 supports more connection points for wiring and and/or multiple boiler control. 
* PCB v2 housing links *(Pick one)*
  * [Rigid Housing](https://www.printables.com/model/260901)
  * [Easy Access Housing)](https://www.printables.com/model/261267)

>

# Programming/Flashing

## Blackpill
  
Make sure you have the software prerequisites. See [Prerequisites](prereq/prerequisites.md)

Flashing instructions:
1. Connect the Blackpill to the ST-Link (connect SWDIO, GND, SWCLK, and 3.3V**\***)
2. Connect ST-Link to the computer
3. Click the Upload task in VS Code
4. Wait until you see green/success logs

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/262874364-c44f2eea-6a64-4731-adb8-a0c1a16089d6.png">

!> Do not flash the Blackpill with the ST-Link while the Blackpill is powered through USB-C. The ST-Link should be the only one providing power to the Blackpill*

?> **\*** If you wish to power the system through the 120/220 VAC PSU to flash the Blackpill then do **not** connect 3.3V to the ST-Link unless you're sure you do not have a knock-off/clone ST-Link.

## Nextion display

Flashing instructions:
1. On an otherwise-empty ≤32 GB FAT32 microSD card, copy the applicable nextion-*-lcd.tft
2. Put the microSD card in the powered **off** Nextion display
3. Power on the display. Power for flashing the Nextion may be provided through the USB-C port on the Blackpill so long as you are using a USB power adapter that will supply 4.6-5.2 VDC (don't use a battery bank or PC USB 2.0 ports for power).  
4. Wait for the Nextion to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.


# Pre-install test

>[!Tip]
>The system will not initialize if the ToFnLED board was enabled in the software but isn't plugged in

Connect the system components (Blackpill, thermocouple, pressure transducer, screen, SSR, switch wires, ToFnLED if defined) to the PCB and power on the system through the USB-C port on the blackpill. If all is successful you should:
- see a build number during boot (good Blackpill-Nextion communication)
- see a "filling boiler" message a few seconds after boot
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target

**Continue the install by referencing the 3PLN machine-specific schematics and/or install instructions that apply to your desired build path:**
* [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) page.
* [3PLN Custom Wiring](guides-stm32/3pln-custom-wiring.md) page.