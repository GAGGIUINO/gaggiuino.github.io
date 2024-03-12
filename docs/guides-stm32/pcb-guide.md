# Control A: PCB

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

>[!Note]
>BOM and 3D printed parts for PCBv3 have moved to the [Home page](README.md#bill-of-materials)

# Considerations
* PCBs are compatible with 3PLN stock wiring integration or custom wiring, though custom wiring is recommended for certain machines (see the [compatibility table](README.md#Compatibility))
* PCB v3 is suitable for most single-boiler espresso machines and is the focus of these instructions. PCB v2 supports more connection points for wiring and and/or multiple boiler control. 
* PCB v2 housing links *(Pick one)*
  * [Rigid Housing](https://www.printables.com/model/260901)
  * [Easy Access Housing](https://www.printables.com/model/261267)

>

# Pre-install test

See [MCU Flashing](guides-stm32/mcu-flashing.md) for instructions on flashing the Blackpill and display

<!-- tabs:start -->
<!-- tab:GC -->
<img height="400" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_LV.png">
<!-- tab:GCP -->
<img height="400" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_LV.png">
<!-- tabs:end -->

<img width="500" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/20517917-3c40-4902-8e60-052e627a0c35">

Connect the system components - Blackpill, thermocouple, pressure transducer, screen, SSR, ToFnLED (if defined) - to the PCB and power on the system through the USB-C port on the blackpill. If all is successful you should:
- see a build number during boot (good Blackpill-Nextion communication)
- see a "filling boiler" message a few seconds after boot
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target

>[!Tip]
>The system will not initialize if the ToFnLED board was enabled in the software but isn't plugged in

**Continue the install by referencing the 3PLN machine-specific schematics and/or install instructions that apply to your desired build path:**
* [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) page.
* [3PLN Custom Wiring](guides-stm32/3pln-custom-wiring.md) page.