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

> [!Info]
> When buying from any of the approved suppliers you can head over to the community [Discord](community/community-media.md#community-discord) for order updates or install-help in the relevant channels.
> 
> Relevant channels for orders : #dyi-efi-co-uk, #peakcoffee-cc, #espressio-nl
> 
> Relevant channels for install-help: #install-help-xxx



**Contribute to the project development efforts.**
<!-- ko-fi :id=zer0bit :color=<color> -->
    Support the development efforts
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
  Profiles sharing       |       :x:        |:heavy_plus_sign: 
  Web interface          |       :x:        |:heavy_plus_sign: 
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


# Compatibility

Gaggiuino is designed for the Gaggia Classic family of espresso machines with 3-way valves (**NOT the Gaggia Classic V2, SIN035U RI9403**). Other espresso machines such as the Rancilio Silvia are also supported although no official installation instructions are available at this time.

<details>
<summary><b>Compatibility table</b> <i>(Click to expand)</i></summary>

Name                                      | Voltage   | Model Years | Model ID        | Notes  
------------------------------------------|-----------|-------------|-----------------|-------
:heavy_check_mark: Gaggia Classic         | 100-120 V | 1991-2018   | SIN035 RI9303   |  
:heavy_check_mark: Gaggia Classic         | 220-240 V | 1991-2014   | SIN035 RI9303   |  
:x:                Gaggia Classic V2      | 220-240 V | 2015-2018   | SIN035U RI9403  | Avoid like the plague
:heavy_check_mark: Gaggia Classic Pro     | 100-120 V | 2019-2022   | SIN035R RI9380  | 
:heavy_check_mark: Gaggia Classic Pro     | 220-240 V | 2019-2022   | SIN035R RI9380  | Uncommon, easier to mod than models with eco PCB
:heavy_check_mark: Gaggia Classic Pro Eco | 220-240 V | 2019-2022   | SIN035UR RI9480 | Power switch mod required and custom wiring recommended due to eco PCB
:heavy_check_mark: Gaggia Classic Evo Pro | 100-120 V | 2023-?      | SIN035R RI9380  | 9 bar OPV spring must be replaced with 10-12 bar spring or spring force increased with washers.
:heavy_check_mark: Gaggia Classic Evo Pro | 220-240 V | 2023-?      | SIN035UR RI9481 | Power switch mod required and custom wiring recommended due to eco PCB

</details>

>

# Releases

  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

# Build Process

> [!TIP|style:callout|label:Tip|iconVisibility:visible]
> If you need help (even during the planning phase), please use a thread in [#install-help-gc](https://discord.com/channels/890339612441063494/996814638471708683) (for Gaggia Classic), [#install-help-gcp](https://discord.com/channels/890339612441063494/996188987964268555) (for Gaggia Classic Pro/Eco/Evo).  
> Make sure to title the thread [username][machine type][control system] Thread Title and include any links/pictures/videos that may apply to your question.  
> ***One help thread per person/machine, please!***

1. Identify your espresso machine (or determine what to buy) 

  See the [Compatibility Table](#compatibility)

2. Determine your build path. 

  Decide if you're going to order a [PCB](pcb/singleboard.md) or build a [component (Lego)](guides-stm32/lego-component-build-guide.md) control system. In general the PCB is going to be much simpler, while the component build is more flexible for experimentation and less picky about thermocouples but requires significant wiring and soldering. 

  Decide how to integrate the control system with your espresso machine. It can either be [integrated into the stock wiring](guides-stm32/3pln-stock-wiring-integration.md) with a few jumpers (less wiring, but sometimes more confusing) or the stock wiring can be replaced with a [custom wiring harness](guides-stm32/3pln-custom-wiring.md) (more work, but results in a clean, straightforward install). It is recommended that you check the notes in the compatibility table for your machine and and read through the instructions before deciding.

3. Select and Order Components

  Order components based on your machine and install path. Make sure to check the [Bill of Materials](#bill-of-materials), the [custom wiring page](guides-stm32/3pln-custom-wiring.md) (if that's the route you're going), and the pages of any optional accessories ([HW Scales](accessories/hw-scales.md),[ToFnLED](accessories/tofnled.md)) that you'd like to install. 

  Note that there are separate approved suppliers for PCBs/Kits and 3D prints. 

4. Parts are in - do the build!

  Follow the instructions for your control system selection

    * [PCB](pcb/singleboard.md)
    * [component (Lego) build](guides-stm32/lego-component-build-guide.md)

  Follow the instructions for your wiring selection

    * [Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md)
    * [Custom Wiring Harness](guides-stm32/3pln-custom-wiring.md)

  Follow the instructions for any accessories that may have been selected

    * [HW Scales](accessories/hw-scales.md)
    * [ToFnLED](accessories/tofnled.md)

5. Make Coffee!

  Record your first start. Post this to [#first-start](https://discord.com/channels/890339612441063494/919183771079692328) on Discord.
  Record your first shot. Post this to [#first-shot](https://discord.com/channels/890339612441063494/910972035205857320) on Discord.
  Read the [Functions Guide](learning/functions-guide.md) for more information on the machine capabilities.
  Check out [Espresso Aficionados](https://espressoaf.com/guides/profiling.html) for info on profiling that you can now implement!

<!-- panels:start -->
<!-- div:title-panel -->
# Bill of Materials

<!-- tabs:start -->
<!-- tab:STM32 PCB -->
### BASE FUNCTIONALITY
_Will enable brew and steam temperature control as well as pump control based on active pressure feedback (this enables pressure and flow profiling as well as other functionality)._
>

> [!Note] 
> PCBs and kits can be ordered from __Approved Official Suppliers__ shown in the sidebar.
>

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
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high quality hose alternative if Saeco can't be bought locally**
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

<!-- tabs:end -->
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
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high quality hose alternative if Saeco can't be bought locally**
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
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high quality hose alternative if Saeco can't be bought locally**
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
* [Alternative high pressure braided hose](https://www.aliexpress.com/item/32370998797.html) **Aliexpress based high quality hose alternative if Saeco can't be bought locally**
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
> If you prefer to purchase printed parts the officially approved providers in the __Approved Official Suppliers__ sidebar section use recommended materials and print settings.

_BOM and assembly instructions for the 3D printed parts are linked here._  
If you'd like to print yourself, order from CraftCloud, or use a local print shop please carefully review the recommended print parameters on the design pages. 

### Base Functionality
_Parts used for the standard install._
<!-- tabs:start -->
<!-- tab:STM32 PCB -->
* [Screen Enclosure](https://www.printables.com/model/280617)
* [Protective Housing *(for Gaggia Classic or if you don't want to put the PCB into the Gaggia Classic Pro pump tower)*](https://www.printables.com/model/370513)
* [Pump Tower Clip *(holds the PCB in non-Eco Gaggia Classic Pro pump towers)*](https://www.printables.com/model/511272)
* [Boiler Terminal Shrouds *(for custom wire harness or to replace broken ones)*](https://www.printables.com/model/380256-gaggia-boiler-terminal-shroud)
<!-- tab:STM32 LEGO -->
* [Screen Enclosure](https://www.printables.com/model/280617)  
* [Internal Component Housing](https://www.printables.com/model/269394)
<!-- tab:Arduino Nano -->
* [Screen Enclosure](https://www.printables.com/model/280617)  
* [Internal Component Housing](https://www.printables.com/model/269394)
* [Optocoupler Case *(for Gaggia Classic)*](https://www.printables.com/model/339542)
<!-- tabs:end -->

Additional Gaggiuino models can be found in the [Gaggiuino Model Collection](https://www.printables.com/social/340492-loogle/collections/265668) or on [Discord](community/community-media.md#community-discord) in the **#mod-3d-design-ideas** channel.
>

# Contributors

Thank you to everyone who has contributed to the project!

<a href="https://github.com/Zer0-bit/gaggiuino/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Zer0-bit/gaggiuino" />
</a>
<a href="https://github.com/GAGGIUINO/gaggiuino.github.io/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=GAGGIUINO/gaggiuino.github.io" />
</a>

Made with [contrib.rocks](https://contrib.rocks).

# Statistics

<details>
<div>
<a href="https://flagcounter.me/details/dj0"><img src="https://flagcounter.me/dj0/" alt="Flag Counter"></a>
</div>
</details>
