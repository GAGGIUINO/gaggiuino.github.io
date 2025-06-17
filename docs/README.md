# HOME

![img1](media/gcp_install.jpg ':size=24%')
![img2](media/gaggiuino_tray_shot.jpg ':size=24%')
![img3](media/spro_plot.jpg ':size=24%')
![img4](media/blackpill_shot.jpg ':size=24%')

Gaggiuino is a community-driven project to add high-end features to Gaggia Classic espresso machines. Implementing the Gaggiuino mod improves performance and precision with temp control, profiling, profile sharing, and other features (see below).

# Features

Advanced pressure and flow profiling, web interface, shot history, OTA updates, Bluetooth scales... so many features we decided to put them under a dropdown. 

<details>
<summary><b>Gaggiuino Features Comparison Table</b> <i>(Click to expand)</i></summary>

  Feature                |Gen 1<br/>Nano & Nextion|Gen 2<br/>STM32 & Nextion|Gen 3<br/>STM32 & ESP32
-----------------------  |:----------------------:|:-----------------------:|:----------------------:
  Neat integration       |:heavy_check_mark:|:heavy_check_mark:  |:heavy_check_mark:      
  Embedded UI            |:heavy_check_mark:|:heavy_check_mark:  |:heavy_check_mark:       
  Full temp control      |:white_check_mark:|:white_check_mark:  |:heavy_check_mark:       
  Auto Shot Timer        |:heavy_check_mark:|:heavy_check_mark:  |:heavy_check_mark:       
  Graphing               |:white_check_mark:|:white_check_mark:  |:heavy_check_mark:                
  Pressure profiling     |:white_check_mark:|:white_check_mark:  |:heavy_check_mark:   
  Manual flow control    |:white_check_mark:|:heavy_check_mark:  |:heavy_plus_sign:       
  Settings persistence   |:white_check_mark:|:heavy_check_mark:  |:heavy_check_mark: 
  Descale program        |:white_check_mark:|:white_check_mark:  |:heavy_check_mark:  
  Integrated scales      |:white_check_mark:|:heavy_check_mark:  |:heavy_check_mark: 
  Stop on Weight/Dose<sup> 1</sup>|:x:      |:heavy_check_mark:  |:heavy_check_mark:       
  DreamSteam<sup> 2</sup>         |:x:      |:white_check_mark:  |:heavy_check_mark:  
  Predictive scales<sup> 3</sup>  |:x:      |:white_check_mark:  |:heavy_check_mark:            
  Flow profiling         |:x:               |:heavy_check_mark:  |:heavy_check_mark:  
  Advanced profiling     |:x:               |:white_check_mark:  |:heavy_check_mark:  
  Profile Management     |:x:               |:white_check_mark:  |:heavy_check_mark:    
  Unlimited<sup> 4</sup> profiling  |:x:    |:x:                 |:heavy_check_mark:
  Unlimited<sup> 4</sup> phases     |:x:    |:x:                 |:heavy_check_mark:
  Advanced phase limits  |:x:               |:x:                 |:heavy_check_mark:
  Bluetooth scales<sup> 5</sup>    |:x:     |:x:                 |:heavy_check_mark:
  Profiles sharing       |:x:               |:x:                 |:heavy_check_mark: 
  Web interface          |:x:               |:x:                 |:heavy_check_mark: 
  OTA updates            |:x:               |:x:                 |:heavy_check_mark: 
  REST API               |:x:               |:x:                 |:heavy_check_mark: 

__Explanation__       
:white_check_mark: Available in a limited form             
:heavy_check_mark:  Available      
:x:  Not available       
:heavy_plus_sign: Planned   
>
_1_ __Stop on Weight/Dose__ - stops at a desired yield.  
_2_ __DreamSteam__ - software driven steam boosting.  
_3_ __Predictive scales__ - software driven predicted weight output.  
_4_ __Unlimited__ - probably has a limit, but we haven't found it yet.   
_5_ __Bluetooth scales__ - [find the currently supported scales here](https://github.com/Zer0-bit/esp-arduino-ble-scales).   

</details>

>

# Compatibility

Gaggiuino is designed for the Gaggia Classic family of espresso machines with 3-way valves (**NOT the Gaggia Classic V2, SIN035U RI9403**). Other espresso machines such as the Rancilio Silvia are also supported although no official installation instructions are available at this time.  
Gaggiuino is **not** designed for espresso machines that use a heat exchanger, thermoblock, thermocoil, group/check valve,  or rotary pump.  

Name                                      | Voltage   | Model Years | Model ID        | Notes  
------------------------------------------|-----------|-------------|-----------------|-------
:heavy_check_mark: Gaggia Classic         | 100-120 V | 1991-2018   | SIN035 RI9303   | Needs [Grounding](guides/machine-specific-guide.md#grounding) 
:heavy_check_mark: Gaggia Classic         | 220-240 V | 1991-2014   | SIN035 RI9303   |  
:x:                Gaggia Classic V2      | 220-240 V | 2015-2018   | SIN035U RI9403  | <details><summary><b>Avoid like the plague</b> <i>(Click for image)</i></summary>![avoid_like_plague_v2](https://github.com/user-attachments/assets/64fff151-a350-4bfc-804c-dd938b5e02b6 ':size=50%')</details> 
:heavy_check_mark: Gaggia Classic Pro     | 100-120 V | 2019-2022   | SIN035R RI9380  | 
:heavy_check_mark: Gaggia Classic Pro     | 220-240 V | 2019-2022   | SIN035R RI9380  | Uncommon, easier to mod than models with eco PCB
:heavy_check_mark: Gaggia Classic Pro Eco | 220-240 V | 2019-2022   | SIN035UR RI9480 | [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) required and custom wiring recommended due to eco PCB
:heavy_check_mark: Gaggia Classic Evo Pro | 100-120 V | 2023-2024   | SIN035R RI9380  | 9 bar OPV must be changed to be a [10-12 bar OPV](guides/machine-specific-guide.md#10-12-bar-opv) <br /> High-temp insulation required for [combined connector insulation](guides/machine-specific-guide.md#combined-connector-insulation) when doing stock wiring integration 
:heavy_check_mark: Gaggia Classic Evo Pro | 220-240 V | 2023-2024   | SIN035UR RI9481 | [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) required and custom wiring recommended due to eco PCB
:heavy_check_mark: Gaggia Classic Pro E24 | 100-120 V | 2024-?      | SIN035R RI9380  | 9 bar OPV must be changed to be a [10-12 bar OPV](guides/machine-specific-guide.md#10-12-bar-opv) <br /> High-temp insulation required for [combined connector insulation](guides/machine-specific-guide.md#combined-connector-insulation) when doing stock wiring integration <br /> Brass boiler behavior is not fully characterized 
:heavy_check_mark: Gaggia Classic Pro E24 | 220-240 V | 2024-?      | SIN035UR RI9481 | [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) required and custom wiring recommended due to eco PCB <br /> Brass boiler behavior is not fully characterized 

>

# Build Process

> [!TIP|style:callout|label:WHERE TO GO FOR HELP|iconVisibility:visible]
> If you need help (even during the planning phase) please make **one** [Discord](community/community-media.md#community-discord) help thread in [#install-help-gc](https://discord.com/channels/890339612441063494/996814638471708683) (for Gaggia Classic) or [#install-help-gcp](https://discord.com/channels/890339612441063494/996188987964268555) (for Gaggia Classic Pro/Eco/Evo/E24).  
> Title the thread by *[username][machine type][control system] Thread Title* and include any links/pictures/videos that may apply to your question. As you have more questions, rename the *Thread Title* and add your question to the thread.  
> ***One help thread per person/machine, please!***

1. **Identify your espresso machine (or determine what to buy)**

  See the [Compatibility Table](#compatibility) and take note of any [Machine-Specific Instructions](guides/machine-specific-guide.md) that are mentioned there. 

2. **Determine your build path** 

  Select the Gaggiuino generation (see [Features](#features) and [Announcements](announcements/) to compare Gen 2 and Gen 3).  
  Gen 3 is recommended for Gaggia Classic and Rancilio Silvia variants - it's newest, has more features, and is being actively worked on.  
  Gen 2 is recommended if attempting a Gaggiuino install on machines that aren't officially compatible - it provides a stable code base to start with.  

  Decide if you're going to order a [PCB](guides-stm32/pcb-guide.md) or build a [component (Lego)](guides-stm32/lego-component-build-guide.md) control system. PCBv4 is recommended for Gen 3 builds, while PCBv3.1 is recommended for Gen 2 builds. 
  The component build is slightly more flexible for experimentation and less picky about thermocouple grounding, however, it adds significant effort and makes reliability dependent on the maker's skill. 

  Decide how to integrate the control system with your espresso machine. It can either be [integrated into the stock wiring](guides-stm32/3pln-stock-wiring-integration.md) with a few jumpers (less wiring, but sometimes more confusing) or the stock wiring can be replaced with a [custom wiring harness](guides-stm32/3pln-custom-wiring.md) (more work, but results in a clean, straightforward install). It is recommended that you check the *notes* in the [Compatibility Table](#compatibility) for your machine and and read through the instructions before deciding.

  If you're building Gen 3, decide which interface option you prefer. For an on-machine (embedded) and web UI, select the 4.3" IPS [touchscreen](guides/interface-screen.md) and one of its mounting options. For a "stealth" install with web UI only, select the [headless](guides/interface-headless.md) PCB.

3. **Select and Order Components**

  Order components based on your machine and install path. Make sure to check the [Bill of Materials](#bill-of-materials), the [custom wiring page](guides-stm32/3pln-custom-wiring.md) (if that's the route you're going), and the pages of any optional accessories ([HW Scales](accessories/hw-scales.md), [ToFnLED](accessories/tofnled.md)) that you'd like to install. 

  There are approved official suppliers for PCBs and Kits, and 3D printed parts linked in the sidebar. Select the 3D print provider closest to you for the lowest shipping cost. Alternatively, the BOM has sources linked so you can order components yourself and 3D print from the design files.

  > [!TIP|style:callout|label:NAMING TIP|iconVisibility:visible]
  > There are two main groups of Gaggia Classic espresso machines referred to in the BOM and instructions:  
  >   - Gaggia Classic (GC)  
  >   - Gaggia Classic Pro (GCP), which generally includes the Pro, Eco, Evo, and E24 models

4. **Parts are in, time to build!**

  > [!WARNING|style:callout|label:WARNING ABOUT VIDEOS|iconVisibility:visible]
  > There are no official build videos. It is highly recommended to only follow the instructions on this website.

  Follow the instructions for your control system selection

    * [A: PCB](guides-stm32/pcb-guide.md)
    * [B: Component (Lego) build](guides-stm32/lego-component-build-guide.md)

  Follow the instructions for your wiring selection

    * [A: Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md)
    * [B: Custom Wiring Harness](guides-stm32/3pln-custom-wiring.md)

  Follow the instructions for your interface selection

    * [Interface: Screen](guides/interface-screen.md)
    * [Interface: Headless](guides/interface-headless.md)

  Follow the instructions for any accessories that may have been selected

    * [HW Scales](accessories/hw-scales.md)
    * [ToFnLED](accessories/tofnled.md)

5. **Make Coffee!**

  Record your first start. Post this to [#first-start](https://discord.com/channels/890339612441063494/919183771079692328) on Discord.  
  Record your first shot. Post this to [#first-shot](https://discord.com/channels/890339612441063494/910972035205857320) on Discord.  
  Read the [User Manual Gen 3](learning/user-manual-gen3.md) or [User Manual Gen 2](learning/user-manual-gen2.md) for more information on the machine capabilities.  
  Check out [Espresso Aficionados](https://espressoaf.com/guides/profiling.html) for info on profiling that you can now implement!  

<!-- panels:start -->
<!-- div:title-panel -->
# Bill of Materials

> [!TIP|style:callout|label:Sourcing|iconVisibility:visible]
> PCBs, kits, and 3D-printed parts may be ordered from the **Approved Official Suppliers** in the sidebar.  
> Head over to the community [Discord](community/community-media.md#community-discord) for updates in the relevant channels:  
> * #diy-efi-co-uk
> * #peakcoffee-cc
> * #espressio-nl  
>
> Alternatively, components can be ordered from AliExpress and parts can be printed from the design files. 

<!-- tabs:start -->
<!-- tab:STM32 PCB -->
* **PCB (Pick one)**
  * **PCBv4 (recommended, available at approved suppliers)**
  * [PCBv3 *(custom order)*](https://github.com/banoz/CoffeeHat/tree/main/Hardware/GaggiaBoard_V3) and [STM32U585CIU6 *(for Gen 3)*](https://www.aliexpress.com/item/3256807730943902.html) or [BlackPill | F411 25M HSE *(for Gen 2)*](https://www.aliexpress.com/item/1005001456186625.html)
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [Ungrounded Thermocouple Sensor | K-type, M4, 0.5 m long](https://www.aliexpress.com/item/3256805310471537.html)
* [SSR-40DA Relay](https://www.aliexpress.com/item/3256806134543825.html)
* [M4x10 Screw, washer, and nut](https://www.aliexpress.com/item/2255801137435920.html) **or an 8-32 set from a local store**
* [Heat-resistant silicone wires](https://www.aliexpress.com/item/2255800441309579.html)
  * **22AWG - 5m:** Black, Red, Blue, Yellow, Orange, Purple
* [JST PH 3P, 4P](https://www.aliexpress.com/item/4000091077742.html)
* [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
* [Pressure sensor | 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* [Flat gasket/o-ring | 1/4 inch pipe (11 x 6 mm), 3 mm thick](https://www.aliexpress.com/item/2255799841120591.html)

<!-- tab:STM32 LEGO -->
* [STM32U585CIU6 *(for Gen 3)*](https://www.aliexpress.com/item/3256807730943902.html) or [BlackPill | F411 25M HSE *(for Gen 2)*](https://www.aliexpress.com/item/1005001456186625.html)
* [ST-Link-STM32](https://www.aliexpress.com/item/1005005303809188.html)
* [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html) **GET THE GREEN ONE**
* [ADS1115](https://www.aliexpress.com/item/32869421559.html)
* [5V RELAY](https://www.aliexpress.com/item/3256803997020234.html) 
* [MAX6675 thermocouple module](https://www.aliexpress.com/item/3256805086341859.html) 
* [Ungrounded Thermocouple Sensor | K-type, M4, 0.5 m long](https://www.aliexpress.com/item/3256805310471537.html)
* [SSR-40DA Relay](https://www.aliexpress.com/item/3256806134543825.html)
* [M4x10 Screw, washer, and nut](https://www.aliexpress.com/item/2255801137435920.html) **or an 8-32 set from a local store**
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
* [PTFE Tube 1 meter | 4x6mm White](https://www.aliexpress.com/item/2251832544541096.html)

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
* * [Self-Fusing Silicone Tape | 25 mm W, 1.5+ m L](https://www.aliexpress.com/item/3256805094022385.html) **OR** [Silicone Heat Shrink Tube | 4, 5, 6 mm dia](https://www.aliexpress.com/item/3256801522005095.html) and a heat gun

<!-- tabs:end -->

<!-- tabs:start -->
<!-- tab:Gen 3 -->
* Interface (pick one)
  * 4.3" ESP32-S3 Screen & cable - **must be activated by [PeakCoffee](https://www.peakcoffee.cc/) or [DIY-EFI](https://diy-efi.co.uk/product-category/gaggiuino/)**
  * Headless E177 PCB & cable- **must be activated by [PeakCoffee](https://www.peakcoffee.cc/) or [DIY-EFI](https://diy-efi.co.uk/product-category/gaggiuino/)**
* MicroSD card | 1-8 GB, FAT32 (FAT32 cards ≤32 GB may work) - optional, for shot history

<!-- tab:Gen 2 -->
* [2.4" Nextion LCD](https://www.aliexpress.com/item/3256803271061345.html) **+ MicroSD card (Class 10 HC 2GB to 32GB)**
<!-- tabs:end -->
<!-- div:panel-end -->
> 

# 3D Printed Parts

BOM and assembly instructions for the recommended 3D printed parts used in the standard install are linked here.  

<!-- tabs:start -->
<!-- tab:STM32 PCB -->
* [PCBv3.1/v4 Housing](https://www.printables.com/model/894339) **OR** [PCBv3 Protective Housing](https://www.printables.com/model/370513)
<!-- tab:STM32 LEGO -->
* [Internal Component Housing](https://www.printables.com/model/269394)
<!-- tabs:end -->

<!-- tabs:start -->
<!-- tab:Gen 3 -->

<!-- tabs:start -->
<!-- tab:Screen -->
* [Gen 3 Screen Housing](https://www.printables.com/model/356026)  
  There are 3 mount options that all use the same screen housing. Pick one.  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/888b31f2-d0e5-48d8-af31-7133bd122f70">
  
  <!-- tabs:start -->
  <!-- tab:Front Mount -->
  * 6 [20x10x3 mm magnets](https://www.aliexpress.com/item/3256806984976303.html) (N35-N52, rectangular)  
    *consider buying locally - magnets have had issues being shipped internationally*
  * [Kapton tape, 20 mm wide](https://www.aliexpress.com/item/3256803012935630.html)
  * Cyanoacrylate (super glue) or Epoxy

  > [!TIP|style:callout|label:Non-magnetic Machines|iconVisibility:visible]
  > For non-magnetic espresso machines, sub double-sided tape with a long-term temp rating of at least 80° C for the magnets
  > * VHB 4611/5952/4910, Gorilla Tape, Alien Tape are options

  <!-- tab:Funnel Mount -->
  * 3 [M3x30 socket head cap screws](https://www.aliexpress.com/item/2251832782719381.html)
  * 5 [M3 washers (OD ≤7 mm)](https://www.aliexpress.com/item/3256804576158708.html)
  * 5 [M3 split lock washers](https://www.aliexpress.com/item/2251832789389968.html)
  * 2 [M3 nylock nuts](https://www.aliexpress.com/item/2251832802681129.html)
  * 1 [M3 Heat Set Insert Nut, 4.5 or 4.6 mm OD, 5 or 6 mm L](https://www.aliexpress.com/item/3256804684678316.html)
  * Cyanoacrylate (super glue) or Epoxy
  <!-- tab:Rear Mount -->
  * 2 [M3x30 socket head cap screws](https://www.aliexpress.com/item/2251832782719381.html)
  * 4 [M3 washers (OD ≤7 mm)](https://www.aliexpress.com/item/3256804576158708.html)
  * 4 [M3 split lock washers](https://www.aliexpress.com/item/2251832789389968.html)
  * 2 [M3 nylock nuts](https://www.aliexpress.com/item/2251832802681129.html)
  <!-- tabs:end -->

<!-- tab:Headless -->
* [Headless PCB Housing](https://www.printables.com/model/1132631) (2 mounting options, pick one)
  * VentClips - Recommended for all Gaggia Classic variants. Clips into the rear vents, no extra components required.
  * Magnets - Recommended for non-Classic machines. Attach magnet(s) to the back with cyanoacrylate or high-temp double-side tape.  
    2 [20x10x3 mm magnets](https://www.aliexpress.com/item/3256806984976303.html) (N35-N52, rectangular) work well, but magnet shape and size are flexible.  
    *consider buying locally - magnets have had issues being shipped internationally*

<!-- tabs:end -->
<!-- tab:Gen 2 -->
* [Screen Enclosure](https://www.printables.com/model/280617)
  * 2 M4x10 button-head screws
  * 2 M4 nuts
<!-- tabs:end -->

If you'd like to print the files yourself instead of purchasing from the official suppliers **please carefully review the recommended print parameters** on the design pages.

Additional Gaggiuino models can be found in the [Gaggiuino Model Collection](https://www.printables.com/social/340492-loogle/collections/265668) or on [Discord](community/community-media.md#community-discord) in the **#mod-3d-design-ideas** channel.
>

# Accessories

Accessories can be added to the base Gaggiuino build for additional features. BOM and instructions are linked below. 

* [Hardware Scales](accessories/hw-scales.md) sit below the drip tray and measure weight during shots. They're most useful for those who like to experiment with beans, grind, and profiles where predictive scales may have a difficult time
* [ToFnLED](accessories/tofnled.md) provides an RGB LED and sensor for measuring water tank level



# Support & Contributors

**Support project development efforts.**
<!-- ko-fi :id=zer0bit :color=<color> -->
    Support the development efforts
<!-- ko-fi -->
>

**Thank you to everyone who has contributed their time and effort to the project!**

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
