# GAGGIUINO STM32 UPGRADE GUIDE

## SAFETY DISCLAIMER
Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. **Always work with the Gaggia unplugged.** You are performing this project under your own risk and the author of this guide and anyone associated with this project are NOT liable for your actions. 

## INTRODUCTION

This guide will explain how to upgrade or start the project with an STM32F4xxx (Blackpill) board. The upgrade is essentially a drop-in replacement for the nano maintaining a majority of the nano installation components. The major differences between nano and STM32 are mentioned below: 

- The wires from the external components to the nano expansion board must be switched around to different ports.

- The ADS1115 board installed between the expansion board and the pressure sensor. 
    
- New 5V relay in place of Optocoupler sensor (for GC) or goes between direct connection from MCU and brew button (for GCP). 

- VSCode and PlatformIO instead of ArduinoIDE to upload to board.

### Components 
Always refer to the official Gaggiuino BOM on the Github project page for the most current materials and links: https://gaggiuino.github.io/#/?id=bill-of-materials

- [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html ) **MAKE SURE THE PROPER BOARD IS SELECTED**

- [ADS1115](https://www.aliexpress.com/item/32869421559.html) 

- [5V RELAY](https://a.aliexpress.com/_vpUdrT) **Supersedes the 1-bit opto**

### Expansion Board Compatibility 
 
Ensure your expansion board circuitry looks like the bottom left (green) and not the bottom right (blue). The bottom right (blue) will not work correctly with the standard pindefs (it will not trigger the relay to heat up the boiler), so it is advised for most people to purchase the board from the BOM that looks like the green expansion board. 
![Expansion Boards](https://user-images.githubusercontent.com/80347096/191157625-4ef4f8d1-0811-4800-b28f-b26ab0f22a12.png)

### Important Considerations Before You Begin The Next Section

![Warning](https://user-images.githubusercontent.com/80347096/191159408-7902397d-a255-4dbb-889c-581c6492b357.png)

 Many that have performed the original nano installation have the dimmer in the same enclosure as the nano. Something to consider before starting the stm32 upgrade: when removing the wires out of the expansion/breakout board and re-twisting them to insert them into their new location, you are likely to have loose strands come off. If your dimmer is not wrapped in something (large heat shrink, silicone self-fuse electrical tape, 3d print) or isolated from other components, then one or a few of more strands may fall onto the dimmer at some point and ignite when brew is activated. 

- Consider wrapping the dimmer with appropriate material before proceeding. 

- Consider using crimped ferrules for all mainboard connections or fully isolating the dimmer in some way to prevent the aforementioned issue from happening. 

- Take tape and go over the interior of your enclosuresto pick up any loose strands from the installation.  

## THE UPGRADE

The major upgrade procedure involved with this process is changing the wires from the nano pin definitions to the STM32 and installing the ADS1115 board. 

### Pin changes from Nano to STM32 

The nano and blackpill/stm32 have different pin setups on their respective boards so the wires terminating on the nano expansion (which were defined in the nano instructions) will need to be moved to the newly defined pins (shown below) to work properly on stm32. 


  
### Install the ADS1115 

With the STM32 upgrade, the pressure transducer data line no longer directly connects to the expansion board. It will now connect to the A0 pin on the new ads1115 board (shown as TS DATA). The ads1115 SCA and SCL connections will go to the main board, and the rest should be self-explanatory per the diagram below. G and ADDR are connected together to GND (such as to your GND Wago). 

![ADS1115](https://user-images.githubusercontent.com/80347096/191159989-bdb2a54b-e610-41a7-9a17-5c668ef136de.png)

### Begin Switching the Wires 
The nano expansion board you already have mirrors the nano pin locations but not the STM32, so we created a chart to demonstrate where the wires go based on the screened pins on both the Blackpill and nano expansion board.  

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

## SOFTWARE INSTALLATION

ArduinoIDE will no longer work for building and uploading the software to the board as it was done for the nano. You will need to download the official STM32 drivers or the STM32 cube programmer and use VSCode and the PlatformIO extension to upload to the STM32.

- Setup VSCode with platformio as shown in the video linked below.  
[VSCode and platformio setup](https://discord.com/channels/890339612441063494/922092497847582721/997109453994328075)

- After pulling the project, build and then flash from tasks (shown in the figure below) based on your hardware and flashing configuration. If you do not have an STLink, then choose the appropriate DFU task and enter DFU mode on the STM32 by plugging in the board, hold boot, and then press reset and let go of boot.

- The folders starting with "scales" should only be flashed for scale calibration. For bench testing and normal machine operation select the folder that matches the rest of your hardware setup.

![Platformio Project Tasks](https://user-images.githubusercontent.com/80347096/191400246-b9dd4b1e-4c5f-4e42-a48a-41a0145d0a8e.png)

Consider buying an ST-Link v2 to more easily upgrade the firmware onto the Blackpill. They can be found on eBay, Amazon and Ali. You will need to solder the 4 angled pins to the board and connect the correct corresponding pins to the stm32 when updating with this tool.

![ST-Link](https://user-images.githubusercontent.com/80347096/191400915-6ed2a991-5f0c-4d2a-b52d-aad29978c0d1.jpg)

## RELAY INSTALLATION

Installing the relay allows the Gaggiuino to perform advanced functions (in conjunction with other necessary hardware): 

- Stop the pump during brew for stop-on-weight (currently requires scales) 

- Pump assist during steaming to maintain extended steam pressure (requires pressure sensor) 

- Pump assist during descale program. 

Installing the relay is relatively simple as it is essentially a drop-in replacement for the Optocoupler. The below diagram demonstrates the install with the GC switch panel, relay and related pins.   

![Figure 6 - Relay diagram for the GCP](https://user-images.githubusercontent.com/80347096/191401329-cdcc0a6a-b414-4c01-bbc8-07d16a5a4282.png)

For the GCP, the LV connection side to the relay and switch are the same as the diagram above. The HV wires on the brew switch connect to the COM and NO HV connectors on the relay.
