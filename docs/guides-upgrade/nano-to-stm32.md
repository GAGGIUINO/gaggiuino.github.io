# LEGO NANO TO STM32 UPGRADE GUIDE

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault! 

# Introduction
This guide will explain how to upgrade your nano build to use a STM32F4xxx (Blackpill). The upgrade is essentially a drop-in replacement for the nano maintaining a majority of the nano installation components. The major differences between nano and STM32 are mentioned below: 

**Upgrading from Nano Extended Functionality**
- STM32 Blackpill and ST-Link
- VSCode and PlatformIO instead of ArduinoIDE to upload to board.
- The wires from the external components to the nano expansion board must be switched around to different ports.
- Addition of snubber
- 5V relay for valve control (GC optocoupler removed)

**Upgrading from Nano Base Functionality also includes**
- ADS1115 board and pressure transducer for pressure sensing 
- Dimmer module for pump control

> [!Note]
> This will upgrade you to the STM32 independent relay and dimmer schematics. Depending on when you completed your nano install your exact setup may not be covered step-by-step. When in doubt trust the schematics. If you prefer, reverting to stock and doing a new install is an option.

# Bill Of Materials

### UPGRADING FROM EXTENDED FUNCTIONALITY
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://www.aliexpress.com/item/3256803997020234.html) 
* [Snubber](https://www.aliexpress.com/item/3256803573244277.html)

### UPGRADING FROM BASE FUNCTIONALITY ADD:
* [RobotDYN dimmer module - Dimmer 4A-400V](https://www.aliexpress.com/item/2251832615710334.html)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [O Ring - OD 11mm, 2.4 mm thick](https://www.aliexpress.com/item/1005003662931218.html)
* Wire _(see STM32 Blackpill tab if you don't already have wire from your initial build)_

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* [Saeco OEM high pressure braided hose](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) **HIGHLY RECOMMENDED ORIGINAL PART**
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high quality hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->

## Expansion Board Compatibility 

Ensure your expansion board circuitry looks like the bottom left (green) and not the bottom right (blue). The bottom right (blue) will not work correctly with the standard pindefs (the two circled pins in yellow are marked `GND` on the reverse and are both connected to the ground plane and each other), so it is advised for most people to purchase the board from the BOM that looks like the green expansion board. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/2452284/204672901-ac1a89d9-cbf2-4367-9196-e1a74fbce7dd.png">

If you receive an expansion board with this connection between two pins it will have the same problem as the blue board (two sets of pins are connected to each other). This can be fixed by cutting the trace. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/2452284/208331321-cef4d700-b961-4725-9cf1-f99202f1785a.jpg">

If you receive an expansion board with a linked ground plane then you'll need to cut the plane in two (likely on both sides of the board). It is recommended to not cut through the screw holes as that may allow a screw to reconnect the planes. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236353796-18f8c699-e251-4df1-bb13-56b204afd832.png">

## Important Considerations Before You Begin The Next Section
!> In most cases there will be high voltage components in the same enclosure as the nano. Something to consider before starting the stm32 upgrade: when removing the wires out of the expansion/breakout board and reinsert them into their new location you may have loose strands come off if you're not using ferrules. If those strands fall onto HV component traces they could cause significant issues. Please use caution and blow out or carefully clean the enclosure after wiring.  
See [Screw Terminals and Crimping](guides-stm32/lego-component-build-guide.md) for more details about making secure connections.

* Consider wrapping the dimmer with appropriate material before proceeding. 
* Using crimped ferrules for all main board connections or fully isolating the dimmer in some way to prevent the aforementioned issue from happening. 
* Take tape and go over the interior of your enclosures to pick up any loose strands from the installation.  

## Component Schematic

Refer to this schematic when completing the changes described below

<img width="500" alt="image" src="schematics/retrofit-indep-relay-dimmer/stm32-comp-build-ird.png">

## Low Voltage Wiring

### Pin changes from Nano to STM32 
The nano and blackpill/stm32 have different pin setups on their respective boards so the wires terminating on the nano expansion (which were defined in the nano instructions) will need to be moved to the newly defined pins (shown below) to work properly on stm32. You can use this table or follow the schematic above.

?>Initially make sure you blackpill is correctly positioned in the expansion board. This will allow you to then just focus on the labels written on nano expansion board.

| Wires     	    | nano EXP L         	| STM32 L              	    | STM32 R               | nano EXP R                | Wires                         |
| :---:       	    |    :----:          	|        :---:	            |   :---:               |      :---:                |       :---:                   |
|           	    |   D13             	|   PA9			            |   PB1                 |   D12                     |   HX711_sck_2                 |   
|           	    |   3V3               	|   PA10         		    |   PB0                 |   D11                     |   HX711_sck_1                 |
|   		        |   REF		            |   PA11  		            |   PA7                 |   D10                     |                               |
|                   |   A0                  |   PA12                    |   PA6                 |   D9                      |   thermoCS                    |
|   relayPin        |   A1                  |   PA15                    |   PA5                 |   D8                      |   thermoCLK                   |
|                   |   A2                  |   PB3                     |   PA4                 |   D7                      |                               |
|   thermoDO        |   A3                  |   PB4                     |   PA3                 |   D6                      |   TX                          |
|                   |   A4                  |   PB5                     |   PA2                 |   D5                      |   RX                          |
|   ADS1115_SCL     |   A5                  |   PB6                     |   PA1                 |   D4                      |   dimmerPin                   |
|   ADS1115_SDA     |   A6                  |   PB7                     |   PA0                 |   D3                      |   zcPin                       |
|   HX711_dout_1    |   A7                  |   PB8                     |   R                   |   D2                      |                               |
|   HX711_dout_2    |   5V                  |   PB9                     |   C15                 |   GND                     |   steamPin                    |
|   5V              |   RST                 |   5V                      |   C14                 |   RST                     |   brewPin                     |
|   GND             |   GND                 |   GND                     |   C13                 |   RXO                     |   valvePin                    |
|                   |   VIN                 |   3V3                     |   VB                  |   TXT                     |                               |

### ADS1115 and Pressure Transducer
The pressure transducer data line (if already installed) no longer directly connects to the expansion board. It will now connect to the A0 pin on the new ADS1115 board (shown as TS DATA). The ADS1115 SCA and SCL connections will go to the main board, and the rest should be self-explanatory per the [schematic](#component-schematic). G and ADDR are connected together to GND (such as to your stripboard or GND Wago). 

![ADS1115](https://user-images.githubusercontent.com/80347096/191159989-bdb2a54b-e610-41a7-9a17-5c668ef136de.png ':size=500')

> [!Note]
> If you haven't already installed the ADS board and pressure transducer then reference the installation instructions in the Component Build Guide's LV Wiring [ADS Board section](guides-stm32/lego-component-build-guide.md#ads-board) and the 3PLN Wiring Integration [Pressure Transducer section](guides-stm32/3pln-stock-wiring-integration.md#pressure-transducer).

### Dimmer Module

If the dimmer has not been installed, wire the low voltage DC connections per the [schematic](#component-schematic). 

If you already have the dimmer module installed then move zcPin (Z/C) to D3 and dimmerPin (PSM) to D4. In this case the high voltage AC wiring will also need to be changed - we'll take care of that after installing the 5V relay. 

### 5V RELAY INSTALLATION
Installing the relay allows the Gaggiuino to perform advanced functions (in conjunction with other necessary hardware): 

- Stop the pump during brew for stop-on-weight
- Pump assist during steaming to maintain extended steam pressure (requires pressure sensor) 
- Pump assist during descale program. 

For GC, remove the optocoupler and its splitters. See the [schematic](#component-schematic) for how the low voltage relay-in and power are connected. 

## High Voltage Wiring

The addition of the snubber and HV connections are where many installs diverge. If you're coming from a new-ish nano install you should be able to add the snubber per the [component schematic](#component-schematic) and follow the instructions on the [Lego Independent Relay and Dimmer page](guides-upgrade/lego-independent-relay-dimmer.md).

If your install wiring is not close to what you see on that page I would recommend wiring the HV near the components (Pump Out, L In, N In, 3WV Out, jumpers) as shown in the [component schematic](#component-schematic) and then checking connections vs the [machine-specific schematic](#machine-specific-schematics) that applies for you. If it's confusing you may even wish to go as far as returning your machine wiring harness to stock and starting fresh.

## Machine-Specific Schematics
?>Readers must be aware that you must study both HV and LV diagrams for your specific machine.

Save the images or right-click and open in a new tab to view at full resolution.

<details>
<summary><b>Gaggia Classic</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gc-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gc-lv-ird.jpg">
</details>

<details>
<summary><b>Gaggia Classic Pro</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp-lv-ird.jpg">
</details>

<details>
<summary><b>Gaggia Classic Pro Eco</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp_eco-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp_eco-lv-ird.jpg">
</details>

## Software Installation

!>ArduinoIDE will no longer work for building and uploading the software to the board as it was done for the nano. You will need to download the official STM32 drivers or the STM32 cube programmer and use VSCode and the PlatformIO extension to upload to the STM32.  
Please refer to [Prerequisites](/prereq/prerequisites.md) for installation and setup instructions.

Flash the Blackpill using the ST-Link (connect SWDIO, GND, SWCLK, and 3.3V*). To connect the ST-Link to the Blackpill (for flashing without opening the housing or machine) this is one of the few times in the project where DuPont connectors may be used. Another option is to solder the wires directly to the Blackpill. 

?> * If you wish to power the system through the 120 VAC PSU (powering on the espresso machine) to flash the Blackpill then do **not** connect 3.3V to the ST-Link unless you're sure you do not have a knock-off/clone ST-Link.

<details>
<summary>Setup project using PIO (Click to expand)</summary>

[Platform IO](https://user-images.githubusercontent.com/109426580/193900425-15c42d9c-adf4-4073-aa46-34874528bf43.mp4 ':include :type=video controls width=70%')

- Make sure you have git installed - https://www.git-scm.com/
- Make sure to update your version of python to the latest - https://www.python.org/downloads/ 
</details>

After pulling the project, build and then flash from tasks (shown in the figure below) based on your hardware and flashing configuration. An ST-Link is recommended for flashing. If you do not have an STLink, then choose the appropriate DFU task and enter DFU mode on the STM32 by plugging in the board, hold boot, and then press reset and let go of boot.

![Platformio Project Tasks](https://user-images.githubusercontent.com/53577819/220899280-554ef293-225d-4610-9c1b-81974cbec191.png ':size=500')
