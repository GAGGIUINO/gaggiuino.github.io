# Archive

The files linked here should generally not be used for new systems. They are being saved in case an older install needs to be repaired. 

# Gen 2 - STM32 + Nextion

* [User Manual - Gen 2](learning/user-manual-gen2.md)

# Gen 1 - Arduino Nano + Nextion

* [Nano Install: Gaggia Classic](archive/guides-nano/gaggia-classic.md)
* [Nano Install: Gaggia Classic Pro](archive/guides-nano/gaggia-classic-pro-new-classic.md)
* Arduino Nano [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)


  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final-v4](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final-v4)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

# PCBv2

* [PCBv2 Github](https://github.com/banoz/CoffeeHat/tree/main/Hardware/GaggiaBoard_V2)
* [Rigid Housing](https://www.printables.com/model/260901), [Easy Access Housing](https://www.printables.com/model/261267)

## PCB v2 Schematics
<!-- tabs:start -->
<!-- tab:Gaggia Classic 100-120v -->

*Remember to check and add [Grounding](guides/machine-specific-guide.md) if needed.*  

<img width="600" alt="GC 120v" src="schematics/custom-3pln/GC_wiring_PCBv2_120v.png">
<!-- tab:Gaggia Classic 220-240v -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/GC_wiring_PCBv2_220v.png">
<!-- tab:Gaggia Classic Pro 100-120v -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/GCP_wiring_PCBv2_120v.png">
<!-- tab:Gaggia Classic Pro 220-240v -->

*Remember to do the [Power switch mod](https://www.youtube.com/embed/WNs3uSLA4Ts?start=99&end=151) to make it bistable.*  

<img width="600" alt="GCP 220v" src="schematics/custom-3pln/GCP_wiring_PCBv2_220v.png">
<!-- tabs:end -->

# Basic HV Wiring diagrams
* [3PLN 120v, GC-specific](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)

# Hardware Scales (500 g load cells)

* [LikeableBump HW Scales](archive/scales.md)