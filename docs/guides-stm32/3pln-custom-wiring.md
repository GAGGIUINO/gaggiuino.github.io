> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!


# Considerations
* The [10 A Resettable Thermal Fuse 185 C](https://www.aliexpress.com/item/3256805232358051.html) or **Rancilio Silvia Boiler Thermostat 165º** (max steam temp of ~145) can be used for the thermal fuse. 
* Get covers for spades, possibly hard covers. Stock boiler terminal covers for round boiler terminal connectors (**160783-7 TE**) cannot be purchased, a printable option is linked on the [Home page](readme.md#3d-printed-parts).
* Consider buying a XH and PH JST kit to make up your own LV connectors instead of using pigtails.
* Know and study difference between HV and LV lines in the schematics.
* PCB v3 is designed to fit into the pump tower where the eco board would be on the 2019+ models (Gaggia Classic Pro, Eco, Evo).

>

!> As this wiring completely replaces the stock wiring harness it is expected that the reader can complete the wiring using only the schematics. Component builds can use the PCBv3 or HV Only schematics after completing the [Lego Component Build Guide](guides-stm32/lego-component-build-guide.md).

# Custom Wire Harness Schematics

**PCB v3** 
* [GC 120v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GC%20PCB%20v3%20120v/GC_wiring_PCBv3_120v.png?raw=true)
* [GC 240v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GC%20PCB%20v3%20220v/GC_wiring_PCBv3_220v.png?raw=true)
* [GCP 120v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GCP%20PCB%20v3%20120v/GCP_wiring_PCBv3_120v.png?raw=true)
* [GCP 240v](https://github.com/thejobbitt/gaggiuino-build/blob/main/wiring/GCP%20PCB%20v3%20220v/GCP_wiring_PCBv3_220v.png?raw=true)

**PCB v2** 
* [GC 110v](https://user-images.githubusercontent.com/53577819/220784209-062e3b3c-e8e7-4a49-b716-87f2ce0634c7.png)
* [GC 240v](https://user-images.githubusercontent.com/53577819/220784212-4b767c1b-8014-4902-81a5-95765ded1181.png)
* [GCP 110v](https://user-images.githubusercontent.com/53577819/220784207-f16a0571-b90c-42f7-89bc-c71b61c03278.png)
* [GCP 240v](https://user-images.githubusercontent.com/53577819/220784202-d218ff9d-0471-4209-afbd-ebc0a6fa8723.png)

**HV Only**
* [3PLN 120v, GC-specific](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)