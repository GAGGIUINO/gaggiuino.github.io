# Control A: PCB

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

# Pre-install test

See [MCU Flashing](guides-stm32/mcu-flashing.md) for instructions on flashing the Blackpill and display

<!-- tabs:start -->
<!-- tab:GC -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tab:GCP -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tabs:end -->

> [!Warning|style:callout|label:Risk of Shorts]
> The PCB is shown out of its case for clarity. Make sure all cases are installed and components are on a non-conductive surface **before power is supplied**!

<!-- tabs:start -->
<!-- tab:PCBv3.1 -->
Connect the system components - thermocouple, pressure transducer, screen, SSR, ToFnLED (if defined) - to the PCB and power on the system through the USB-C port on the PCB.  

<img width="500" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/836fe705-8835-40f8-af33-fc063a7d09b0">

If all is successful you should:
- see a build number during boot (good PCB-Nextion communication)
- see a "filling boiler" message a few seconds after boot and a red LED on the underside of the board lighting up at the same time
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target

<!-- tab:PCBv3 -->
Connect the system components - Blackpill, thermocouple, pressure transducer, screen, SSR, ToFnLED (if defined) - to the PCB and power on the system through the USB-C port on the blackpill.  

<img width="500" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/20517917-3c40-4902-8e60-052e627a0c35">

If all is successful you should:
- see a build number during boot (good Blackpill-Nextion communication)
- see a "filling boiler" message a few seconds after boot
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target

<!-- tabs:end -->

> [!Note|style:callout|label:Notes]
> * The system will not initialize if the ToFnLED board was enabled in the software but isn't plugged in
> * If built, HW scales can be included in the bench test and even calibrated at this point

**Continue the installation by referencing the 3PLN machine-specific schematics and/or instructions that apply to your desired build path.**  
Custom wiring is recommended for certain machines (see the [compatibility table](README.md#Compatibility))

* [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) page.
* [3PLN Custom Wiring](guides-stm32/3pln-custom-wiring.md) page.