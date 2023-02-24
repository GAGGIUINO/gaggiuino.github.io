> [!Warning]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project.

> [!Note] 
> The PCB can only be ordered through discord where the ordering process can be monitored and any possible frauds averted. Install resources are also on discord at this point in time while a more tailored process is being formulated.
>
> **Make sure to read the info in the *#pcb-interest-registration* discord channel as well for more info on the ordering process as well as searching discord for any PCB related questions as many have been answered multiple times already.**

# Bill of Materials

* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link V2](https://www.aliexpress.com/item/32860702733.html)
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj)
* [C-M4 ungrounded screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant silicone wires](https://bit.ly/3tjSQbI)
  * **18AWG - 1m:** Black, Red, Brown, White, Green, Blue & Yellow
  * **26AWG - 5m:** Black, Red, White, Orange & Yellow
* [JST XH 4P](https://www.aliexpress.us/item/2251832768103991.html)
* [JST PH 2P, 3P, 4P and 5P](https://www.aliexpress.com/item/4000091077742.html)
* [Spade connectors M/F 6.3mm](https://bit.ly/2Sjrkhu)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
  * [O Ring - OD 11mm](https://www.aliexpress.com/item/1005003662931218.html) 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* Saeco - [Option 1](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) | [Option 2](https://www.ebay.co.uk/itm/114865529829)  **HIGHLY RECOMMENDED ORIGINAL PART - AVAILABLE LOCALLY**
* **THIS ALTERNATE HOSE OPTION IS A LAST RESORT - READ BELOW WARNING** [ID4mm x OD9mm](https://www.aliexpress.com/item/1005001729453617.html)
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

!> The Aliexpress hose IS NOT rated as high as the original SAECO hose, please use common sense when operating the machine if you can't buy the recommended original SAECO hose use the exact size recommended here as pressure resistance is determined by the hose diameter as well.
<!-- tabs:end -->

# Considerations
!> It is expected that when going through PCB install you are able to figure out most things by yourself. Please note, these are only suggestions/food for thought/rough guidance. 

* Get rid of old harness and replace with homemade one. 
* Try to maintain the wiring for the thermal fuse and boiler terminals. If not get a resettable thermostat - **Rancilio Silvia Boiler Thermostat 165º** and boiler terminals are **160783-7 TE**.
* Get covers for spades, possibly hard covers. [Printable boiler terminal covers.](https://www.printables.com/model/380256-gaggia-boiler-terminal-shroud)
* Consider buying a XH and PH JST kit to make up your own.
* Know and study difference between HV and LV lines.
* Gaggia Classic New 2018/19 - ECO board must be bypassed. Highly recommend getting PCB v3 as you can slot it into the pump tower where the eco board would be.

# Schematics
## PCB v2
* [GCP 110v](https://user-images.githubusercontent.com/53577819/220784207-f16a0571-b90c-42f7-89bc-c71b61c03278.png)
* [GCP 240v](https://user-images.githubusercontent.com/53577819/220784202-d218ff9d-0471-4209-afbd-ebc0a6fa8723.png)
* [GC 110v](https://user-images.githubusercontent.com/53577819/220784209-062e3b3c-e8e7-4a49-b716-87f2ce0634c7.png)
* [GC 240v](https://user-images.githubusercontent.com/53577819/220784212-4b767c1b-8014-4902-81a5-95765ded1181.png)

## PCB v3
* [GC Standard (revised)](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)


