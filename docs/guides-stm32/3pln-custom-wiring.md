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

### PCB v3
> #### Gaggia Classic
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GC PCBv3 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_120v.png"> | <img height="300" alt="GC PCBv3 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_220v.png"> |
>
> #### Gaggia Classic Pro
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GCP PCBv3 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_120v.png"> | <img height="300" alt="GCP PCBv3 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_220v.png"> |
### PCB v2
> #### Gaggia Classic
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GC PCBv2 120v" src="schematics/custom-3pln/GC_wiring_PCBv2_120v.png"> | <img height="300" alt="GC PCBv2 220v" src="schematics/custom-3pln/GC_wiring_PCBv2_220v.png"> |
>
> #### Gaggia Classic Pro
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> |<img height="300" alt="GCP PCBv2 120v" src="schematics/custom-3pln/GCP_wiring_PCBv2_120v.png"> | <img height="300" alt="GCP PCBv2 220v" src="schematics/custom-3pln/GCP_wiring_PCBv2_220v.png"> |

### HV Only
* [3PLN 120v, GC-specific](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)