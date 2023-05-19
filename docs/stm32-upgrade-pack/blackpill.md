# NANO TO STM32 UPGRADE GUIDE

> [!Warning]
> Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. **Always work with the Gaggia unplugged.** You are performing this project under your own risk and the author of this guide and anyone associated with this project are NOT liable for your actions. 

## Introduction
This guide will explain how to upgrade or start the project with an STM32F4xxx (Blackpill) board. The upgrade is essentially a drop-in replacement for the nano maintaining a majority of the nano installation components. The major differences between nano and STM32 are mentioned below: 

- The wires from the external components to the nano expansion board must be switched around to different ports.
- The ADS1115 board installed between the expansion board and the pressure sensor. 
- New 5V relay in place of Optocoupler sensor (for GC) or goes between direct connection from MCU and brew button (for GCP). 
- VSCode and PlatformIO instead of ArduinoIDE to upload to board.

### Components 
Always refer to the official [Gaggiuino BOM](/?id=bill-of-materials) for the latest hardware:

- **STM32F411CEU6**
- **ADS1115**
- **5v RELAY**

### Expansion Board Compatibility 
Ensure your expansion board circuitry looks like the bottom left (green) and not the bottom right (blue). The bottom right (blue) will not work correctly with the standard pindefs (it will not trigger the relay to heat up the boiler - the two circled pins in yellow are marked `GND` on the reverse and are both connected to the ground plane and each other), so it is advised for most people to purchase the board from the BOM that looks like the green expansion board.  

![Expansion Boards](https://user-images.githubusercontent.com/2452284/204672901-ac1a89d9-cbf2-4367-9196-e1a74fbce7dd.png ':size=500')

If you do purchase a green expansion board but see on the reverse side this connection between two pins - it will have the same problem as the blue board (two sets of pins are connected to each other) this can be fixed by cutting this trace.

![Connected trace](https://user-images.githubusercontent.com/2452284/208331321-cef4d700-b961-4725-9cf1-f99202f1785a.jpg ':size=500')

### Important Considerations Before You Begin The Next Section
!> Many that have performed the original nano installation have the dimmer in the same enclosure as the nano. Something to consider before starting the stm32 upgrade: when removing the wires out of the expansion/breakout board and re-twisting them to insert them into their new location, you are likely to have loose strands come off. If your dimmer is not wrapped in something (large heat shrink, silicone self-fuse electrical tape, 3d print) or isolated from other components, then one or a few of more strands may fall onto the dimmer at some point and ignite when brew is activated. 

* Consider wrapping the dimmer with appropriate material before proceeding. 
* Using crimped ferrules for all main board connections or fully isolating the dimmer in some way to prevent the aforementioned issue from happening. 
* Take tape and go over the interior of your enclosures to pick up any loose strands from the installation.  

## Software Installation
?>Please refer to [Prerequisites](/prereq/prerequisites.md).

!>ArduinoIDE will no longer work for building and uploading the software to the board as it was done for the nano. You will need to download the official STM32 drivers or the STM32 cube programmer and use VSCode and the PlatformIO extension to upload to the STM32.

<details>
<summary>Setup project using PIO (Click to expand)</summary>

[Platform IO](https://user-images.githubusercontent.com/109426580/193900425-15c42d9c-adf4-4073-aa46-34874528bf43.mp4 ':include :type=video controls width=70%')

- Make sure you have git installed - https://www.git-scm.com/
- Make sure to update your version of python to the latest - https://www.python.org/downloads/ 
</details>

After pulling the project, build and then flash from tasks (shown in the figure below) based on your hardware and flashing configuration. If you do not have an STLink, then choose the appropriate DFU task and enter DFU mode on the STM32 by plugging in the board, hold boot, and then press reset and let go of boot.

![Platformio Project Tasks](https://user-images.githubusercontent.com/53577819/220899280-554ef293-225d-4610-9c1b-81974cbec191.png ':size=500')

Consider buying an ST-Link v2 to more easily upgrade the firmware onto the Blackpill. They can be found on eBay, Amazon and Ali. You will need to solder the 4 angled pins to the board and connect the correct corresponding pins to the stm32 when updating with this tool.

## Install the ADS1115 
With the STM32 upgrade, the pressure transducer data line no longer directly connects to the expansion board. It will now connect to the A0 pin on the new ads1115 board (shown as TS DATA). The ads1115 SCA and SCL connections will go to the main board, and the rest should be self-explanatory per the diagram below. G and ADDR are connected together to GND (such as to your GND Wago). 

![ADS1115](https://user-images.githubusercontent.com/80347096/191159989-bdb2a54b-e610-41a7-9a17-5c668ef136de.png ':size=500')

## 5v RELAY INSTALLATION
Installing the relay allows the Gaggiuino to perform advanced functions (in conjunction with other necessary hardware): 

- Stop the pump during brew for stop-on-weight (currently requires scales) 
- Pump assist during steaming to maintain extended steam pressure (requires pressure sensor) 
- Pump assist during descale program. 

Installing the relay is relatively simple as it is essentially a drop-in replacement for the optocoupler on GC and just an additional component for GCP. The below diagram demonstrates the install with the GC switch panel, relay and related pins, the installation is very similar for both GC and GCP, the goal is to move all brew switch HV wires to the relay HV ports, then on the GC/GCP brew switch only LV wires should be connected when the relay is fully wired.

![Figure 6 - Relay diagram for the GC](https://user-images.githubusercontent.com/80347096/191401329-cdcc0a6a-b414-4c01-bbc8-07d16a5a4282.png ':size=500')

For the GCP, the LV connection side to the relay and switch are the same as the diagram above. The HV wires on the brew switch are removed and connected to the COM and NO HV connectors on the relay - thus leaving no connections on the right side of the brew switch, plugged into it. See [Schematics](#schematics-and-diagrams).

* BREW MIDDLE HV - Disconnect the middle HV cable from brew switch common pole 5, connect to relay COM.
* BREW TOP HV - Disconnect the top HV cable from brew switch pole 4, connect to relay NO.  

## Pin changes from Nano to STM32 
The nano and blackpill/stm32 have different pin setups on their respective boards so the wires terminating on the nano expansion (which were defined in the nano instructions) will need to be moved to the newly defined pins (shown below) to work properly on stm32.

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

## Schematics and Diagrams
?>Readers must be aware that you must study both HV and LV diagrams for your specific machine.

!>Updated with new independent relay and dimmer wiring

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

<details>
<summary><b>STM32 Component Build</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/stm32-comp-build-ird.png">

</details>