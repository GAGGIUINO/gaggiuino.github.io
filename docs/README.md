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
> Relevant channels for orders : #diy-efi-co-uk, #peakcoffee-cc, #espressio-nl
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
  __Stop on Weight/Dose__<sup> 1</sup>|      :x:        |:heavy_check_mark:       
  __DreamSteam__<sup> 2</sup>        |       :x:        |:heavy_check_mark:  
  __Predictive scales__<sup> 3</sup> |       :x:        |:heavy_check_mark:  
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
_1_ __Stop on Weight/Dose__ - stops at a desired yield.  
_2_ __DreamSteam__ - software driven steam boosting.  
_3_ __Predictive scales__ - software driven predicted weight output.
<!-- panels:end -->

>

# Compatibility

Gaggiuino is designed for the Gaggia Classic family of espresso machines with 3-way valves (**NOT the Gaggia Classic V2, SIN035U RI9403**). Other espresso machines such as the Rancilio Silvia are also supported although no official installation instructions are available at this time.

Name                                      | Voltage   | Model Years | Model ID        | Notes  
------------------------------------------|-----------|-------------|-----------------|-------
:heavy_check_mark: Gaggia Classic         | 100-120 V | 1991-2018   | SIN035 RI9303   | Needs [Grounding](guides/machine-specific-guide.md#grounding) 
:heavy_check_mark: Gaggia Classic         | 220-240 V | 1991-2014   | SIN035 RI9303   |  
:x:                Gaggia Classic V2      | 220-240 V | 2015-2018   | SIN035U RI9403  | Avoid like the plague
:heavy_check_mark: Gaggia Classic Pro     | 100-120 V | 2019-2022   | SIN035R RI9380  | 
:heavy_check_mark: Gaggia Classic Pro     | 220-240 V | 2019-2022   | SIN035R RI9380  | Uncommon, easier to mod than models with eco PCB
:heavy_check_mark: Gaggia Classic Pro Eco | 220-240 V | 2019-2022   | SIN035UR RI9480 | [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) required and custom wiring recommended due to eco PCB
:heavy_check_mark: Gaggia Classic Evo Pro | 100-120 V | 2023-?      | SIN035R RI9380  | 9 bar OPV must be changed to be a [10-12 bar OPV](guides/machine-specific-guide.md#10-12-bar-opv) <br /> High-temp insulation required for [combined connector insulation](guides/machine-specific-guide.md#combined-connector-insulation) when doing stock wiring integration 
:heavy_check_mark: Gaggia Classic Evo Pro | 220-240 V | 2023-?      | SIN035UR RI9481 | [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) required and custom wiring recommended due to eco PCB

>

# Build Process

> [!TIP|style:callout|label:WHERE TO GO FOR HELP|iconVisibility:visible]
> If you need help (even during the planning phase) please make **one** [Discord](community/community-media.md#community-discord) help thread in [#install-help-gc](https://discord.com/channels/890339612441063494/996814638471708683) (for Gaggia Classic) or [#install-help-gcp](https://discord.com/channels/890339612441063494/996188987964268555) (for Gaggia Classic Pro/Eco/Evo).  
> Title the thread by *[username][machine type][control system] Thread Title* and include any links/pictures/videos that may apply to your question. As you have more questions, rename the *Thread Title* and add your question to the thread.  
> ***One help thread per person/machine, please!***

1. **Identify your espresso machine (or determine what to buy)**

  See the [Compatibility Table](#compatibility)

2. **Determine your build path.** 

  Decide if you're going to order a [PCB](pcb/singleboard.md) or build a [component (Lego)](guides-stm32/lego-component-build-guide.md) control system. In general the PCB is going to be much simpler, while the component build is more flexible for experimentation and less picky about thermocouples but requires significant wiring and soldering. 

  Decide how to integrate the control system with your espresso machine. It can either be [integrated into the stock wiring](guides-stm32/3pln-stock-wiring-integration.md) with a few jumpers (less wiring, but sometimes more confusing) or the stock wiring can be replaced with a [custom wiring harness](guides-stm32/3pln-custom-wiring.md) (more work, but results in a clean, straightforward install). It is recommended that you check the notes in the [Compatibility Table](#compatibility) for your machine and and read through the instructions before deciding.

3. **Select and Order Components**

  Order components based on your machine and install path. Make sure to check the [Bill of Materials](#bill-of-materials), the [custom wiring page](guides-stm32/3pln-custom-wiring.md) (if that's the route you're going), and the pages of any optional accessories ([HW Scales](accessories/hw-scales.md), [ToFnLED](accessories/tofnled.md)) that you'd like to install. 

  There are approved official suppliers for PCBs and Kits, and 3D printed parts linked in the sidebar. Select the 3D print provider closest to you for the lowest shipping cost. Alternatively, the BOM has sources linked so you can order components yourself and 3D print from the design files.

  > [!TIP|style:callout|label:NAMING TIP|iconVisibility:visible]
  > There are two main groups of Gaggia Classic espresso machines referred to in the BOM and instructions:  
  >   - Gaggia Classic (GC)  
  >   - Gaggia Classic Pro (GCP), which generally includes the Pro, Eco, and Evo models

4. **Parts are in, time to build!**

  > [!WARNING|style:callout|label:WARNING ABOUT VIDEOS|iconVisibility:visible]
  > There are no official build videos. It is highly recommended to only follow the instructions on this website.

  Follow the instructions for your control system selection

    * [A: PCB](pcb/singleboard.md)
    * [B: Component (Lego) build](guides-stm32/lego-component-build-guide.md)

  Follow the instructions for your wiring selection

    * [A: Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md)
    * [B: Custom Wiring Harness](guides-stm32/3pln-custom-wiring.md)

  Follow the instructions for any accessories that may have been selected

    * [HW Scales](accessories/hw-scales.md)
    * [ToFnLED](accessories/tofnled.md)

5. **Make Coffee!**

  Record your first start. Post this to [#first-start](https://discord.com/channels/890339612441063494/919183771079692328) on Discord.  
  Record your first shot. Post this to [#first-shot](https://discord.com/channels/890339612441063494/910972035205857320) on Discord.  
  Read the [Functions Guide](learning/functions-guide.md) for more information on the machine capabilities.  
  Check out [Espresso Aficionados](https://espressoaf.com/guides/profiling.html) for info on profiling that you can now implement!  

<!-- panels:start -->
<!-- div:title-panel -->
# Bill of Materials

> [!TIP|style:callout|label:Sourcing|iconVisibility:visible]
> PCBs, kits, and 3D-printed parts may be ordered from the **Approved Official Suppliers** in the sidebar.  
> Alternatively, components can be ordered from AliExpress and parts can be printed from the design files. 

<!-- tabs:start -->
<!-- tab:STM32 PCB -->
* [PCBv3 *(Approved Supplier or custom order)*](https://github.com/banoz/CoffeeHat/tree/main/Hardware/GaggiaBoard_V3)
* [STM32F411CEU6 | F411 25M HSE](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [2.4" Nextion LCD](https://www.aliexpress.com/item/3256803271061345.html)
* [Ungrounded Thermocouple Sensor | K-type, M4, 0.5 m long](https://www.aliexpress.com/item/3256805310471537.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant silicone wires](https://www.aliexpress.com/item/2255800441309579.html)
  * **22AWG - 5m:** Black, Red, Blue, Yellow, Orange, Purple
* [JST XH 4P](https://www.aliexpress.com/item/2251832768103991.html)
* [JST PH 3P, 4P & 5P](https://www.aliexpress.com/item/4000091077742.html)
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [Pressure sensor | 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [Flat gasket/o-ring | 1|4 inch pipe (11 x 6 mm), 3 mm thick](https://www.aliexpress.com/item/2255799841120591.html)

<!-- tab:STM32 LEGO -->
* [STM32F411CEU6 | F411 25M HSE](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html) **GET THE GREEN ONE**
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://www.aliexpress.com/item/3256803997020234.html) 
* [2.4" Nextion LCD](https://www.aliexpress.com/item/3256803271061345.html) **+ MicroSD card (Class 10 HC 8GB to 32GB)**
* [MAX6675 thermocouple board](https://www.aliexpress.com/item/2251832724065302.html) 
* [Ungrounded Thermocouple Sensor | K-type, M4, 0.5 m long](https://www.aliexpress.com/item/3256805310471537.html)
* [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
* [Heat-resistant Silicone Wire](https://www.aliexpress.com/item/2255800441309579.html)
  * **18AWG - 1m:** Black, Red, White
  * **22AWG - 5m:** Black, Red, Blue, Yellow, White
  * **26AWG - 5m:** Black, Red, Blue, Yellow
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [12v/1A Power Supply](https://www.aliexpress.com/item/33012749903.html)
* [12v to 5v stepdown](https://www.aliexpress.com/item/3256801635468667.html)
* [Snubber](https://www.aliexpress.com/item/3256803573244277.html)
* [Stripboard](https://www.aliexpress.com/item/2251832661583259.html)
* [RobotDYN dimmer module | Dimmer 4A-400V](https://www.aliexpress.com/item/2251832615710334.html)
* [Pressure sensor | 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [Flat gasket/o-ring | 1|4 inch pipe (11 x 6 mm), 3 mm thick](https://www.aliexpress.com/item/2255799841120591.html)
<!-- tabs:end -->

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
* [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
* [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
* [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)

<!-- tab:Gaggia Classic Pro -->
* **High Pressure braided hose (pick one)**
  * **Saeco OEM Braided Tube** [fiyo (UK)](https://www.fiyo.co.uk/saeco-hose-silicone-hose-5-x-8-9-for-coffee-machine-16000380-42169), [WLL (US)](https://www.wholelattelove.com/products/ga-16000380-reinforced-silicone-tube-5x9-mm) *(Search 996530009505 to find locally)* 
  * [Toyox high pressure braided hose](https://www.aliexpress.com/item/3256805661123272.html) *Aliexpress alternative if Saeco can't be found*
* [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
* [T-tee | 6mm](https://www.aliexpress.com/item/1005004145756673.html)
* [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 
<!-- tabs:end -->

<!-- tabs:start -->
<!-- tab:Stock Wiring Integration -->
* [Heat-resistant silicone wires](https://www.aliexpress.com/item/2255800441309579.html) **Amount is for minimal mistakes, extra is recommended**
  * **18AWG - 1m:** Black *(x2 if 230 VAC)*, White *(x2 if 230 VAC)*, Red, Blue, Yellow
* [Piggy Back spades 6.3mm](https://www.aliexpress.com/item/32800326782.html)
* [Fork Crimp Terminal | SV1.25-5s](https://www.aliexpress.com/item/3256805357612913.html)
* [Self-Fusing Silicone Tape | 25 mm W, 1.5+ m L](https://www.aliexpress.com/item/3256805094022385.html) **nice to have, needed for Evo**

<!-- tab:Custom Wiring -->
**This list assumes components will be taken from the stock wiring harness. For alternate components see the [Custom Wiring](guides-stm32/3pln-custom-wiring.md) page**
* [Heat-resistant silicone wires](https://www.aliexpress.com/item/2255800441309579.html) **For following schematic colors. Amount is for minimal mistakes, extra is recommended**
  * **18AWG - 1m:** Black, White *(x2 if 120 VAC)*, Red, Orange, Blue *(x2 if 230 VAC)*, Yellow, Green
* [BN1.25 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html)
* [BN2 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html)
* [Fork Crimp Terminal | 102PCS-SV *(SV1.25-5s & SV2-5s used)*](https://www.aliexpress.com/item/3256805357612913.html)
* [Silicone Heat Shrink Tube | 4, 5, 6 mm dia](https://www.aliexpress.com/item/3256801522005095.html) **OR** [Self-Fusing Silicone Tape | 25 mm W, 1.5+ m L](https://www.aliexpress.com/item/3256805094022385.html)

<!-- tabs:end -->
<!-- div:panel-end -->
> 

# 3D Printed Parts

BOM and assembly instructions for the recommended 3D printed parts used in the standard install are linked here.  

<!-- tabs:start -->
<!-- tab:STM32 PCB -->
* [Screen Enclosure](https://www.printables.com/model/280617)
* [PCBv3 Protective Housing](https://www.printables.com/model/370513)
<!-- tab:STM32 LEGO -->
* [Screen Enclosure](https://www.printables.com/model/280617)  
* [Internal Component Housing](https://www.printables.com/model/269394)
<!-- tabs:end -->

If you'd like to print yourself, order from CraftCloud, or use a local print shop **please carefully review the recommended print parameters** on the design pages. 

Additional Gaggiuino models can be found in the [Gaggiuino Model Collection](https://www.printables.com/social/340492-loogle/collections/265668) or on [Discord](community/community-media.md#community-discord) in the **#mod-3d-design-ideas** channel.
>

# Accessories

Accessories can be added to the base Gaggiuino build for additional features. BOM and instructions are linked below. 

* [Hardware Scales](accessories/hw-scales.md) sit below the drip tray and measure weight during shots. They're most useful for those who like to experiment with beans, grind, and profiles where predictive scales may have a difficult time
* [ToFnLED](accessories/tofnled.md) provides an RGB LED and sensor for measuring water tank level

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
