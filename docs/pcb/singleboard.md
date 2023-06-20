> [!Warning]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project.

>[!Note]
>BOM and 3D printed parts for PCBv3 have moved to the [Home page](README.md#bill-of-materials)

# Considerations
!> It is expected that when going through PCB install you will follow the [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) guide or figure out the custom wiring by yourself. Please note, these are only suggestions/food for thought/rough guidance. 

* If you want to do a custom harness:
  * The [10 A Resettable Thermal Fuse 185 C](https://www.aliexpress.com/item/3256805232358051.html) or **Rancilio Silvia Boiler Thermostat 165º** (max steam temp of ~145) can be used for the thermal fuse. 
  * Get covers for spades, possibly hard covers. Stock boiler terminal covers for round boiler terminal connectors (**160783-7 TE**) cannot be purchased, a printable option is linked on the [Home page](readme.md#3d-printed-parts).
* Consider buying a XH and PH JST kit to make up your own.
* Know and study difference between HV and LV lines.
* Gaggia Classic New 2018/19 - ECO board must be bypassed or custom wiring used. PCB v3 can slot it into the pump tower where the eco board would be.
* PCB v3 is suitable for most single-boiler espresso machines. PCB v2 supports more connection points for wiring and and/or multiple boiler control. 
* PCB v2 housing links *(Pick one)*
  * [Rigid Housing](https://www.printables.com/model/260901)
  * [Easy Access Housing)](https://www.printables.com/model/261267)

>

# Custom Wire Harness Schematics

>[!Note]
>For stock harness integration follow the [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) guide.

**PCB v3** 
* [GC 120v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GC%20PCB%20v3%20120v/GC_wiring_PCBv3_120v.png?raw=true)
* [GC 240v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GC%20PCB%20v3%20220v/GC_wiring_PCBv3_220v.png?raw=true)
* [GCP 120v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GCP%20PCB%20v3%20120v/GCP_wiring_PCBv3_120v.png?raw=true)
* [GCP 240v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GCP%20PCB%20v3%20220v/GCP_wiring_PCBv3_220v.png?raw=true)
* [*GC Standard (revised)*](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [*3PLN 240v*](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)
* [*3PLN 120v*](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)

**PCB v2** 
* [GC 110v](https://user-images.githubusercontent.com/53577819/220784209-062e3b3c-e8e7-4a49-b716-87f2ce0634c7.png)
* [GC 240v](https://user-images.githubusercontent.com/53577819/220784212-4b767c1b-8014-4902-81a5-95765ded1181.png)
* [GCP 110v](https://user-images.githubusercontent.com/53577819/220784207-f16a0571-b90c-42f7-89bc-c71b61c03278.png)
* [GCP 240v](https://user-images.githubusercontent.com/53577819/220784202-d218ff9d-0471-4209-afbd-ebc0a6fa8723.png)