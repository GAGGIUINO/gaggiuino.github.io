# Archive

The files linked here should generally not be used for new systems. They are being saved in case an older install needs to be repaired. 

# Gen 3 - STM32 + ESP32

### Custom Wiring 

[3PLN Custom Wiring (May 2024 Version)](archive/3pln-custom-wiring-2024.md)

# Gen 2 - STM32 + Nextion

### User Manual 

* [User Manual - Gen 2](learning/user-manual-gen2.md)

### DC Schematics

<!-- tabs:start -->
<!-- tab:GCP -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1/v4 -->
  <img height="400" alt="image" src="schematics/stm32-lv/archive/2025-02/GCP_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/archive/2025-02/GCP_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tab:GC -->
  <!-- tabs:start -->
  <!-- tab:PCBv3.1/v4 -->
  <img height="400" alt="image" src="schematics/stm32-lv/archive/2025-02/GC_wiring_PCBv3_1_LV.png">
  <!-- tab:PCBv3 -->
  <img height="400" alt="image" src="schematics/stm32-lv/archive/2025-02/GC_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tabs:end -->

### Stock Wiring Integration Schematics
  **2025-01**
  <!-- tabs:start -->
  <!-- tab:Gaggia Classic Pro 120v -->
  ![GCP SI PCB](../schematics/install-stock-3pln/archive/2025-01/GCP_SI_wiring_PCBv3_1_120v.png ':size=80%')

  <!-- tab:Gaggia Classic 100-120v -->
  ![GC SI PCB](../schematics/install-stock-3pln/archive/2025-01/GC_SI_wiring_PCBv3_1_120v.png ':size=80%')

  <!-- tab:Gaggia Classic 220-240v -->
  ![GC SI PCB](../schematics/install-stock-3pln/archive/2025-01/GC_SI_wiring_PCBv3_1_220v.png ':size=80%')
  <!-- tabs:end -->

  **2023-05**
  <!-- tabs:start -->
  <!-- tab:Gaggia Classic -->
  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gc-hv-3pln.jpg">

  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gc-lv-3pln.jpg">
  <!-- tab:Gaggia Classic Pro -->

  **Gaggia Classic Pro**

  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gcp-hv-3pln.jpg">

  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gcp-lv-3pln.jpg">

  **Gaggia Classic Pro Eco**

  > [!Warning|style:callout]
  > [3PLN Plug-and-play/custom wiring](guides-stm32/3pln-custom-wiring.md) is recommended for machines with the eco board (automatic power-off).

  *Remember to do the [Power switch mod](https://www.youtube.com/embed/WNs3uSLA4Ts?start=99&end=151) to make it bistable.*  

  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gcp_eco-hv-3pln.jpg">

  <img height="300" alt="image" src="schematics/install-stock-3pln/archive/2023-05/gcp_eco-lv-3pln.jpg">
  <!-- tabs:end -->

### Basic HV Wiring diagrams

* [3PLN 120v, GC-specific](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)

### Build Upgrade Instructions

* [Lego Independent Relay and Dimmer](guides-upgrade/lego-independent-relay-dimmer.md)
* [Lego Nano to STM32 Upgrade](guides-upgrade/nano-to-stm32.md)

# Gen 1 - Arduino Nano + Nextion

### Installation Documents

* [Nano Install: Gaggia Classic](archive/guides-nano/gaggia-classic.md)
* [Nano Install: Gaggia Classic Pro](archive/guides-nano/gaggia-classic-pro-new-classic.md)

### Software 

* Arduino Nano [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)

|  MCU             |                               Code branch         
|------------------|------------------------------------------------------------------------------------
|  Arduino Nano    |[release-nano-final-v4](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final-v4)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

# PCBv2

* [PCBv2 Github](https://github.com/banoz/CoffeeHat/tree/main/Hardware/GaggiaBoard_V2)
* [Rigid Housing](https://www.printables.com/model/260901), [Easy Access Housing](https://www.printables.com/model/261267)

### PCB v2 Schematics
<!-- tabs:start -->
<!-- tab:Gaggia Classic 100-120v -->

*Remember to check and add [Grounding](guides/machine-specific-guide.md) if needed.*  

<img width="600" alt="GC 120v" src="schematics/custom-3pln/archive/2023-08/GC_wiring_PCBv2_120v.png">
<!-- tab:Gaggia Classic 220-240v -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/archive/2023-08/GC_wiring_PCBv2_220v.png">
<!-- tab:Gaggia Classic Pro 100-120v -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/archive/2023-08/GCP_wiring_PCBv2_120v.png">
<!-- tab:Gaggia Classic Pro 220-240v -->

*Remember to do the [Power switch mod](https://www.youtube.com/embed/WNs3uSLA4Ts?start=99&end=151) to make it bistable.*  

<img width="600" alt="GCP 220v" src="schematics/custom-3pln/archive/2023-08/GCP_wiring_PCBv2_220v.png">
<!-- tabs:end -->


# Accessories

### Hardware Scales 

* [LikeableBump HW Scales (500 g load cells)](archive/lb-scales.md)