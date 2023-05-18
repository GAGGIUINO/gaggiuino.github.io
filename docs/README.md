> [!NOTE]
>This site is a general guide and not a exhaustive, step-by-step tutorial. It is expected that anyone attempting has proficiency with the skills listed in the [Recommendations](learning/learning-sources.md) page. For anyone attempting the install it's strongly recommended to read the planned install route in it's entirety.

**Contribute to better docs written by a professional technical writer.**
<!-- ko-fi :id=zer0bit :color=<color> -->
    Support better docs
<!-- ko-fi -->
>
# Features

  Feature                |  Arduino Nano    |  STM32 Blackpill
-----------------------  |------------------|-----------------
  Integrated Housing     |:heavy_check_mark:|:heavy_check_mark:       
  Embedded UI            |:heavy_check_mark:|:heavy_check_mark:       
  Brew/Steam control     |:heavy_check_mark:|:heavy_check_mark:       
  Auto Shot Timer        |:heavy_check_mark:|:heavy_check_mark:       
  Graphing               |:heavy_check_mark:|:heavy_check_mark:             
  Pre-infusion           |:heavy_check_mark:|:heavy_check_mark:       
  Pressure profiling     |:heavy_check_mark:|:heavy_check_mark:   
  Manual flow control    |:heavy_check_mark:|:heavy_check_mark:       
  Settings persistence   |:heavy_check_mark:|:heavy_check_mark: 
  Descale program        |:heavy_check_mark:|:heavy_check_mark:       
  Integrated scales      |:heavy_check_mark:|:heavy_check_mark:      
  Flow profiling         |       :x:        |:heavy_check_mark:       
  Stop on Weight/Dose*   |       :x:        |:heavy_check_mark:       
  Steam Boost*           |       :x:        |:heavy_check_mark:  
  Predictive scales*     |       :x:        |:heavy_check_mark:  
  Saving/Loading profiles|       :x:        |:heavy_plus_sign: 
  Web interface          |       :x:        |:heavy_plus_sign: 
  OTA updates            |       :x:        |:heavy_plus_sign: 

:heavy_check_mark:  Available
:x:  Not available
:heavy_plus_sign: Planned

_*1_ __Stop on Weight/Dose__ - requires the relay that's part of the STM32 UPGRADE.
>
_*2_ __Steam Boost__ - software driven steam boosting, requires the relay that's part of the STM32 UPGRADE.
>
_*3_ __Predictive scales__ - software driven predicted weight output, doesn't need any scales hardware.

# Releases

  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)


> 1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.
>
> 2. Make sure you **ALWAYS** flash both the microcontroller as well as the LCD unit.

> [!TIP]
> Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.

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

> [!TIP]
> The current recommendation is to perform the Nano build first, after which one can easily upgrade to STM32 if further functionality is desired, jumping straight into STM32 is not encouraged for the inexperienced due to the documentation targeting a direct Nano install at this point in time.
<!-- tabs:start -->
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
  * **22AWG - 5m:** Black, Red, Blue, White
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
* [O Ring - OD 11mm](https://www.aliexpress.com/item/1005003662931218.html) 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* [Saeco OEM high pressure braided hose](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169) **HIGHLY RECOMMENDED ORIGINAL PART**
* [ID4mm x OD9mm](https://www.aliexpress.com/item/1005001729453617.html)**THIS ALTERNATE HOSE OPTION IS A LAST RESORT - READ BELOW WARNING** 
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

> [!WARNING]
> The Aliexpress hose IS NOT rated as high as the original SAECO hose, please use common sense when operating the machine if you can't buy the recommended original SAECO hose use the exact size recommended here as pressure resistance is determined by the hose diameter as well.
<!-- tabs:end -->

<!-- tab:STM32 Blackpill -->
### BASE FUNCTIONALITY
_Will enable brew and steam temperature control as well as pump control based on active pressure feedback (this enables pressure and flow profiling as well as other functionality)._
>
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link V2](https://www.aliexpress.com/item/32860702733.html)
* [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html) **GET THE GREEN ONE**
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://a.aliexpress.com/_vpUdrT) 
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj) **+ MicroSD card (Class 10 HC 8GB to 32GB)**
* [MAX6675 thermocouple](https://bit.ly/3ejTUIj) 
* [C-M4 screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant Silicone Wire](https://bit.ly/3tjSQbI)
  * **18AWG - 1m:** Black, Red, White
  * **22AWG - 5m:** Black, Red, Blue, White
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
* [ID4mm x OD9mm](https://www.aliexpress.com/item/1005001729453617.html)**THIS ALTERNATE HOSE OPTION IS A LAST RESORT - READ BELOW WARNING**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

> [!WARNING]
> The Aliexpress hose IS NOT rated as high as the original SAECO hose, please use common sense when operating the machine if you can't buy the recommended original SAECO hose use the exact size recommended here as pressure resistance is determined by the hose diameter as well.
<!-- tabs:end -->
<!-- tab:Nano to STM32 Upgrade -->
* [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link V2](https://www.aliexpress.com/item/32860702733.html)
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://a.aliexpress.com/_vpUdrT) 
* [Snubber](https://www.aliexpress.com/item/3256803573244277.html)
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
* [ID4mm x OD9mm](https://www.aliexpress.com/item/1005001729453617.html)**THIS ALTERNATE HOSE OPTION IS A LAST RESORT - READ BELOW WARNING**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

> [!WARNING]
> The Aliexpress hose IS NOT rated as high as the original SAECO hose, please use common sense when operating the machine if you can't buy the recommended original SAECO hose use the exact size recommended here as pressure resistance is determined by the hose diameter as well.
<!-- tabs:end -->
<!-- tabs:end -->
<!-- div:panel-end -->
> 

## 3D Printed Parts
_BOM and assembly instructions for the 3D printed parts are linked here.  
Additional Gaggiuino models can be found in the [Gaggiuino Model Collection](https://www.printables.com/social/340492-loogle/collections/265668) or on Discord in the **#mod-3d-design-ideas** channel._

### Base Functionality
_Parts used for the standard component install._
  * [Screen Enclosure](https://www.printables.com/model/280617)
  * [Internal Component Housing](https://www.printables.com/model/269394)

### Hardware Scales Functionality
_The STM32 build has software emulated **predictive scales** enabled that are sufficient for users with dialed in grind and settings after calibration.  
Hardware scales offer accurate sensing of the first drops into the cup as well as realtime shot weight tracking and stop-on-weight across a variety of settings and less traditional shot profiles._

> [!WARNING]
> This is an advanced installation step that requires accurate 3D-printed parts, good installation practices, and an in-depth understanding to achieve optimal results.

* [Gaggia Classic & Classic Pro scales housing](https://www.printables.com/model/285370-gaggia-classic-pro-scales) *(BOM and models)*
>

### **Print services**
_Places to get your 3D prints if you don't have a printer. Gaggiuino print service partner(s) are reviewed by the Gaggiuino team for service, print quality, and cost before approval._
  * [Gaggiuino print service (US Based)](https://gaggiuino.hudsoncreativegroup.com/)
  * [CraftCloud print shop aggregator](https://craftcloud3d.com/)

# Statistics

<details>
<div>
<a href="https://flagcounter.me/details/dj0"><img src="https://flagcounter.me/dj0/" alt="Flag Counter"></a>
</div>
</details>