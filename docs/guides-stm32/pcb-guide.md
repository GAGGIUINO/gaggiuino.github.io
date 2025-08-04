# Control A: PCB

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

<img height="300" alt="PCBv3.1 in case, connected" src="media/pcb_housing.png">

> 

# Pre-install test

## Schematics (DC)

<!-- tabs:start -->
<!-- tab:GCP -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1/v4 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tab:GC -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1/v4 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tabs:end -->

## Setup

<!-- tabs:start -->
<!-- tab:Gen 3 -->
> [!Warning|style:callout|label:Risk of Shorts]
> Make sure electronics are in their housings and/or secure on a non-conductive surface **before power is supplied**!

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
Connect the system components - thermocouple, pressure transducer, screen/headless, SSR, ToFnLED (if available) - to the PCB and power on the system through the USB-C port on the PCB.  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/5ea67541-0cf4-4064-9f87-19ad900bef8b">

<!-- tab:PCBv3 -->
Connect the system components - BlackPill, thermocouple, pressure transducer, screen/headless, SSR, ToFnLED (if available) - to the PCB and power on the system through the USB-C port on the BlackPill.  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/8f903e75-a563-4882-879c-9ef112254019">

<!-- tabs:end -->

> [!Note|style:callout|label:Setup Notes]
> * The headless module is connected to J1 in place of the screen. To see the test information you'll need to connect to the headless unit via Wi-Fi as described in the [User Manual](learning/user-manual-gen3.md).
> * Depending on revision, the Blue and Yellow screen wires may be reversed from the schematics. Do not disassemble pre-made cables! Verify connection points, not just color.
> * Bare Thermocouple wires should be folded over before being clamped in the connector; make sure insulation is not clamped
>   
>   <img width="300" alt="image" src="https://github.com/user-attachments/assets/3cac0e03-e850-4f7b-844e-4c19971a8382">

<!-- tab:Gen 2 -->
> [!Warning|style:callout|label:Risk of Shorts]
> The PCB and screen are shown out of their housings for clarity. Make sure electronics are in their housings and/or secure on a non-conductive surface **before power is supplied**!
<!-- tabs:start -->
<!-- tab:PCBv3.1 -->
Connect the system components - thermocouple, pressure transducer, screen, SSR, ToFnLED (if defined) - to the PCB and power on the system through the USB-C port on the PCB.  

<img width="500" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/836fe705-8835-40f8-af33-fc063a7d09b0">

<!-- tab:PCBv3 -->
Connect the system components - BlackPill, thermocouple, pressure transducer, screen, SSR, ToFnLED (if defined) - to the PCB and power on the system through the USB-C port on the BlackPill.  

<img width="500" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/20517917-3c40-4902-8e60-052e627a0c35">

<!-- tabs:end -->

> [!Note|style:callout|label:Notes]
> * See [MCU Flashing](guides-stm32/mcu-flashing.md) for instructions on flashing the STM32 / BlackPill and UI
> * The system will not initialize if the ToFnLED board was enabled in the software but isn't plugged in
> * If built, HW scales can be included in the bench test and even calibrated at this point

<!-- tabs:end -->

## Verification

<!-- tabs:start -->
<!-- tab:Gen 3 -->
Verify the following:
- the "Initialization in progress" message disappears after a few seconds
- a "Filling boiler" message is shown a few seconds after boot (and a red LED on the underside of PCBv3.1/v4 lights up at the same time)
- temperature is displayed and changes when heat is applied to the thermocouple
- the SSR light turns on if the temperature is below the setpoint (or flashes if temp is close to setpoint)
- the pressure value is 0.0 bar with no deviation
- brew temperature is the target (not steam temperature)
- Build numbers in Settings (About page on screen) match each other and the [latest release](https://github.com/Zer0-bit/gaggiuino/releases/latest)

> [!Note|style:callout|label:Notes]
> * If the build numbers don't match then see [MCU Flashing](guides-stm32/mcu-flashing.md) for instructions on flashing the STM32 / BlackPill and UI
> * If built, HW scales can be included in the bench test and even calibrated at this point

<!-- tab:Gen 2 -->
Verify the following:
- screen shows a build number during boot (good BlackPill-Nextion communication)
- a "filling boiler" message is shown a few seconds after boot
- Temperature is displayed and changes when heat is applied to the thermocouple
- the SSR light turns on if the temperature is below the setpoint (or flashes if temp is close to setpoint)
- the pressure value is 0.0 bar with no deviation
- brew temperature is the target (not steam temperature)
<!-- tabs:end -->

**Continue the installation by referencing the 3PLN machine-specific schematics and/or instructions that apply to your desired build path.**  
Custom wiring is recommended for certain machines (see the [compatibility table](README.md#Compatibility))

* [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) page.
* [3PLN Custom Wiring](guides-stm32/3pln-custom-wiring.md) page.