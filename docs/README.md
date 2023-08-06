> [!WARNING|style:flat|label:Impact of purchasing from unofficial sources|iconVisibility:visible]
>
> We want to bring your attention to an important issue that affects the sustainability of the project. We've noticed that some bad actors are taking advantage of our hard work and dedication for their own financial benefit. Buying PCBs, kits, or 3D prints from unauthorized sources directly supports these profit-driven individuals, undermining the very core ideas and values that our mod stands for.
>
> We are committed to sticking to our principles and keeping the community strong. We have consciously chosen not to commercialize the project, allowing it to remain open and accessible to all. Therefore, we urge you to pause and think twice before making any purchases from websites that are not officially approved and listed on the left side menu.
>
> Instead, we encourage you to support our officially approved suppliers who are dedicated to upholding our mod's principles and ensuring top-notch quality. By doing so, you not only help us maintain the integrity of the project but also show your support for the countless hours of work invested by our team and contributors.
>
>Thank you for being a part of the GAGGIUINO community and for your understanding in this matter.
>
>Sincerely,
>
>The GAGGIUINO Team

**Contribute to better docs written by a professional technical writer.**
<!-- ko-fi :id=zer0bit :color=<color> -->
    Support better docs
<!-- ko-fi -->
>
# Features

  Feature                |  Arduino Nano    |  STM32 Blackpill
-----------------------  |------------------|-----------------
  Neat integration       |:heavy_check_mark:|:heavy_check_mark:       
  Embedded UI            |:heavy_check_mark:|:heavy_check_mark:       
  Full temp control      |:heavy_check_mark:|:heavy_check_mark:       
  Auto Shot Timer        |:heavy_check_mark:|:heavy_check_mark:       
  Graphing               |:heavy_check_mark:|:heavy_check_mark:                
  Pressure profiling     |:heavy_check_mark:|:heavy_check_mark:   
  Manual flow control    |:heavy_check_mark:|:heavy_check_mark:       
  Settings persistence   |:heavy_check_mark:|:heavy_check_mark: 
  Descale program        |:heavy_check_mark:|:heavy_check_mark:       
  Integrated scales      |:heavy_check_mark:|:heavy_check_mark:      
  Flow profiling         |       :x:        |:heavy_check_mark:  
  Advanced profiling     |       :x:        |:heavy_check_mark:      
  __Stop on Weight/Dose__*|      :x:        |:heavy_check_mark:       
  __DreamSteam__*        |       :x:        |:heavy_check_mark:  
  __Predictive scales__* |       :x:        |:heavy_check_mark:  
  Profiles Management    |       :x:        |:heavy_check_mark: 
  Web interface          |       :x:        |:heavy_plus_sign: 
  OTA updates            |       :x:        |:heavy_plus_sign: 
  OTA updates            |       :x:        |:heavy_plus_sign: 

<!-- panels:start -->
<!-- div:left-panel -->
__Explanation__  
:heavy_check_mark:  Available      
:x:  Not available       
:heavy_plus_sign: Planned   
>
_*1_ __Stop on Weight/Dose__ - stops at a desired yield.  
_*2_ __DreamSteam__ - software driven steam boosting.  
_*3_ __Predictive scales__ - software driven predicted weight output.
<!-- panels:end -->

# Releases

  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

# Timeline

<details>
<summary><b>Initial checks</b> <i>(Click to expand)</i></summary>


1. Purchase the parts listed from Ali and expect a wait of ~1 month.

   Any parts purchased anywhere else are done so at your own risk (they've not been tested).

2. Connect test components described in the doc to Arduino.

   Using the expansion board, twist the ends of cables and connect to the screw terminals. At this point using DuPont connections is fine but please note later we will solder to the boards or pins.

3. Flash Arduino and LCD with code.

4. Plug in and test.

   Check for a temp reading. It will contain the default offset of 7 degrees which means the initial temp will be room temp -7.
</details>

<details>
<summary><b>Base Install</b> <i>(Click to expand)</i></summary>

1. Plan out where the components will sit inside the machine to determine cable length
2. Create piggyback cables. Determine what switch points to piggyback from.
3. Wire in power delivery method - isolate the board using an enclosure or tape it up after wiring.
4. If you have the eco timer, disable it.
5. Swap out thermocouple - ease out the boiler (don't fully remove it) in order to gain more access.
6. Install the max temp board - isolate the board using an enclosure or tape it up after wiring.
7. Place and wire relay - attach the brew thermostat wires to the SSR relay and sit/attach the back plate or relay on the body of the machine, add some thermal paste
8. Re-Wire the steam switch for steam handling - you need to swap the brew thermostat wires (above step) for the steam thermostat wires and bridge the brew thermostat wires together then take some wires from the steam switch to the Arduino.
9. Wire brew switch for continuity
10. Test.
</details>

<details>
<summary><b>Extended Install</b> <i>(Click to expand)</i></summary>

1. Install the pressure sensor. Ensure it does not leak under pressure.
2. Install dimmer - isolate the board using an enclosure or tape it up after wiring.
3. Install the load cells.
</details>

<details>
<summary><b>Final checks</b> <i>(Click to expand)</i></summary>

1. Make sure all connections are proper i.e., no metal is exposed and well isolated, all soldering is perfect and wrapped in heat-shrink.
2. Flash the Arduino and LCD with the latest version from GitHub (there could have been changes since).
3. Record your first start. Post this to [#first-start](https://discord.com/channels/890339612441063494/919183771079692328) on Discord.
4. Find out your regional settings and set them in the settings of the Arduino.
5. Check all other settings save correctly.
6. Record your first shot. Post this to [#first-shot](https://discord.com/channels/890339612441063494/910972035205857320) on Discord.
</details>

>
?> **_Total estimated install time will be based on understanding and experience._** 
> 
<!-- panels:start -->
<!-- div:title-panel -->
# Bill of Materials

<!-- tabs:start -->
<!-- tab:STM32 LEGO -->
### BASE FUNCTIONALITY
_Will enable brew and steam temperature control as well as pump control based on active pressure feedback (this enables pressure and flow profiling as well as other functionality)._
>
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html) **GET THE GREEN ONE**
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://a.aliexpress.com/_vpUdrT) 
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj) **+ MicroSD card (Class 10 HC 8GB to 32GB)**
* [MAX6675 thermocouple](https://bit.ly/3ejTUIj) 
* [C-M4 screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant Silicone Wire](https://bit.ly/3tjSQbI)
  * **18AWG - 1m:** Black, Red, White
  * **22AWG - 5m:** Black, Red, Blue, Yellow, White
  * **26AWG - 5m:** Black, Red, Blue, Yellow
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [Piggy Back spades](https://www.aliexpress.com/item/32800326782.html)
* [12v/1A Power Supply](https://www.aliexpress.com/item/33012749903.html)
* [12v to 5v stepdown](https://a.aliexpress.com/_uAvaIl)
* [Snubber](https://www.aliexpress.com/item/3256803573244277.html)
* [RobotDYN dimmer module - Dimmer 4A-400V](https://bit.ly/3xhTwQy)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [O Ring - OD 11mm, 2.4 mm thick](https://www.aliexpress.com/item/1005003662931218.html)

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* [Saeco OEM high pressure braided hose](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) **HIGHLY RECOMMENDED ORIGINAL PART**
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high qulity hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->
<!-- tab:STM32 PCB -->
### BASE FUNCTIONALITY
_Will enable brew and steam temperature control as well as pump control based on active pressure feedback (this enables pressure and flow profiling as well as other functionality)._
>

> [!Note] 
> If you're not exerienced with ordering PCBs it can be group ordered through Discord where the ordering process can be monitored and possible frauds averted.
>
> **Make sure to read the info in the *#pcb-interest-registration* discord channel as well for more info on the ordering process as well as searching discord for any PCB related questions as many have been answered multiple times already.**

* [PCBv3 *(Group buy or custom order)*](https://github.com/banoz/CoffeeHat/tree/main/Hardware/GaggiaBoard_V3)
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj)
* [C-M4 ungrounded screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant silicone wires](https://bit.ly/3tjSQbI)
  * **18AWG - 1m:** Black, Red, Brown, White, Green, Blue & Yellow
  * **22AWG - 5m:** Black, Red, White, Orange & Yellow
* [JST XH 4P](https://www.aliexpress.com/item/2251832768103991.html)
* [JST PH 3P, 4P & 5P](https://www.aliexpress.com/item/4000091077742.html)
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [O Ring - OD 11mm, 2.4 mm thick](https://www.aliexpress.com/item/1005003662931218.html) 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* [Saeco OEM high pressure braided hose](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) **HIGHLY RECOMMENDED ORIGINAL PART**
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high qulity hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->

<!-- tab:Nano to STM32 Upgrade -->
### UPGRADING FROM EXTENDED FUNCTIONALITY
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://a.aliexpress.com/_vpUdrT) 
* [Snubber](https://www.aliexpress.com/item/3256803573244277.html)

### UPGRADING FROM BASE FUNCTIONALITY ADD:
* [RobotDYN dimmer module - Dimmer 4A-400V](https://bit.ly/3xhTwQy)
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
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high qulity hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->
<!-- tab:Arduino Nano -->
### BASE FUNCTIONALITY
_Will enable only brew and steam temperature control_
>
* [Arduino Nano AT328](https://bit.ly/3eXSfXZ) 
* [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html) **GET GREEN - BLUE IS NOT COMPATIBLE FOR STM32 - SEE STM GUIDE FOR MORE INFO**
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj) **+ MicroSD card(Class 10 HC 8GB to 32GB)**
* [MAX6675 thermocouple](https://bit.ly/3ejTUIj) 
* [C-M4 screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant Silicone Wire](https://bit.ly/3tjSQbI)
  * **18AWG - 1m:** Black, Red, White
  * **22AWG - 5m:** Black, Red, Blue, Yellow, White
  * **26AWG - 5m:** Black, Red, Blue, Yellow
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [Piggy Back spades](https://www.aliexpress.com/item/32800326782.html)
* [12v/1A Power Supply](https://www.aliexpress.com/item/33012749903.html)
* [12v to 5v stepdown](https://a.aliexpress.com/_uAvaIl)

**Gaggia Classic Specific**
* [1-Bit AC 220V Optocoupler](https://www.aliexpress.com/item/1005003228104606.html)  

### EXTENDED FUNCTIONALITY
_Will enable pump control based on active pressure feedback, this enables pressure and flow profiling as well as other functionality._
* [RobotDYN dimmer module - Dimmer 4A-400V](https://bit.ly/3xhTwQy)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [O Ring - OD 11mm, 2.4 mm thick](https://www.aliexpress.com/item/1005003662931218.html) 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* [Saeco OEM high pressure braided hose](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) **HIGHLY RECOMMENDED ORIGINAL PART**
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high qulity hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->
<!-- tabs:end -->
<!-- div:panel-end -->
> 


# Accessories

Accessories can be added to the base Gaggiuino build for additional features. BOM and instructions are linked below. 

* [Hardware Scales](accessories/hw-scales.md) sit below the drip tray and measure weight during shots. They're most useful for those who like to experiment with beans, grind, and profiles where predictive scales may have a difficult time
* [ToFnLED](accessories/tofnled.md) provides an RGB LED and sensor for measuring water tank level


# 3D Printed Parts
> [!Tip]
> If you prefer to purchase printed parts the oficially approved providers in the __Approved Official Suppliers__ sidebar section use recommended materials and print settings.

_BOM and assembly instructions for the 3D printed parts are linked here._  
If you'd like to print yourself, order from CraftCloud, or use a local print shop please carefully review the recommended print parameters on the design pages. 

### Base Functionality
_Parts used for the standard install._
<!-- tabs:start -->
<!-- tab:STM32 LEGO -->
* [Screen Enclosure](https://www.printables.com/model/280617)  
* [Internal Component Housing](https://www.printables.com/model/269394)
<!-- tab:STM32 PCB -->
* [Screen Enclosure](https://www.printables.com/model/280617)
* [Protective Housing *(for Gaggia Classic or if you don't want to put the PCB into the Gaggia Classic Pro pump tower)*](https://www.printables.com/model/370513)
* [Pump Tower Clip *(holds the PCB in non-Eco Gaggia Classic Pro pump towers)*](https://www.printables.com/model/511272)
* [Boiler Terminal Shrouds *(for custom wire harness or to replace broken ones)*](https://www.printables.com/model/380256-gaggia-boiler-terminal-shroud)
<!-- tab:Arduino Nano -->
* [Screen Enclosure](https://www.printables.com/model/280617)  
* [Internal Component Housing](https://www.printables.com/model/269394)
* [Optocoupler Case *(for Gaggia Classic)*](https://www.printables.com/model/339542)
<!-- tabs:end -->

Additional Gaggiuino models can be found in the [Gaggiuino Model Collection](https://www.printables.com/social/340492-loogle/collections/265668) or on [Discord](community/community-media.md#community-discord) in the **#mod-3d-design-ideas** channel.
>

# Statistics

<details>
<div>
<a href="https://flagcounter.me/details/dj0"><img src="https://flagcounter.me/dj0/" alt="Flag Counter"></a>
</div>
</details>
