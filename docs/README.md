**Contribute to better docs written by a professional documenattion writer.**
<!-- ko-fi :id=zer0bit :color=<color> -->
    Support better docs
<!-- ko-fi -->
>
!>**This site is a general guide and *ABSOLUTELY NOT* an exhaustive, step-by-step tutorial. It is expected that anyone attempting has proficiency with the skills listed in the _Recommendations_ page of this site. For anyone attempting the install it's strongly recommended to read the planned install route in it's entirety.**




**_Total estimated install time will be based on understanding and experience._**

## Features / Completeness

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

>_*1_ __Stop on Weight/Dose__ - requires the relay that's part of the STM32 UPGRADE.
>
>_*2_ __Steam Boost__ - software driven steam boosting, requires the relay that's part of the STM32 UPGRADE.
>
>_*3_ __Predictive scales__ - software driven predicted weight output, doesn't need any scales hardware.

## CODE VERSIONS

  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)


> 1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.
>
> 2. Make sure you **ALWAYS** flash both the microcontroller as well as the LCD unit.

!> Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.

## Community Speaks
<iframe width="560" height="315" src="https://www.youtube.com/embed/MxPNQRCxQZc" title="GAGGIUINO Upgrade Show" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

!> The below video shows extensive use of duponts during the install which can lead to many issues if left like that for the actual install, it's recommended to solder all those terminals.
<iframe width="560" height="315" src="https://www.youtube.com/embed/EJFadpL9aOE" title="GAGGIUINO BUILD LOG" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<details>

<summary><b>MORE FROM THE COMMUNITY</b> <i>(Click to expand)</i></summary>

<iframe width="560" height="315" src="https://www.youtube.com/embed/hpxB1Q6AFkY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</details>

<details>

<summary><b>MOD FUNCTIONS AND USAGE</b> <i>(Click to expand)</i></summary>

 - **BOILER**: Sets the desired temperature at the boiler level
 - **OFFSET**: Sets the offset value used to calculate the real water temperature
 - **HPWR**: Sets the relay start pulse length
 - **M.C.DIV**: Sets the main cycle divider (aka non brew heating behaviour), used in conjunction with HPWR
 - **B.C.DIV**: Sets the brew cycle divider
 - **Brew(Auto)**: All pressure settings are following the below:
   - **PREINFUSION**: Enables pre-infusion
     - **Time**: Sets the length of the PI phase
     - **Bar**: Sets the max reachable pressure for the PI phase
     - **Soak**: Sets the length of the soaking (blooming) phase
   - **P-PROFILING**: Enables AUTO pressure profiling mode
     - **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
     - **Finish**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
     - **Hold**: Sets the length of the PP hold period, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
     - **Length**: Sets the length (AKA speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.

**Here is a classic prexample of how a declining profile can be used once the mod is installed.**

![PressureGraph](https://user-images.githubusercontent.com/109426580/204081504-90cd4961-5a0f-4911-b4db-00411437ff2f.png)


 - **Brew(Manual)**: Allows for manual pressure control at brew time.
 - **DESCALE**: Enables the descaling program.

  >Descaling should be done with a blind basket portafilter locked in the group, steam valve slightly open for the water to flow in a separate reservoir and water tank fully loaded with water mixed with descale solution.
</details>

## EOL
- **NANO Development**

  > Arduino NANO based development has reached EOL, if its featureset is enough for your needs grab the code from [release-nano-final](https://github.com/Zer0-bit/gaggiuino/releases/tag/release-nano-final-v2)

## Timeline

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
> 

# Bill of Materials

> The code has been designed to be modular, meaning there is a minimal hardware configuration one can start with if certain features are not something of interest, it's all appropriately split under "BASE" or "EXTENDED" functionality (see below).

!> The current recommendation is to do the Nano build first, after which one should upgrade to STM32 if further functionality is desired, jumping straight inot STM32 is not encouraged for the inexperienced.

### BASE FUNCTIONALITY
_Will enable only brew and steam temperature control_

  * [Arduino Nano AT328](https://bit.ly/3eXSfXZ)  _Not needed if one wants to jump straight to STM32_ 
  * [Arduino Nano expansion board](https://www.aliexpress.com/item/32325724150.html)
  * [2.4" Nextion LCD](https://bit.ly/3CAUzPj) **+ MicroSD card(Class 10 HC 8GB to 32GB)**
  * [MAX6675 thermocouple](https://bit.ly/3ejTUIj) 
  * [C-M4 screw K-Type thermocouple sensor](https://www.aliexpress.com/item/1005004948080451.html)
  * [40DA SSR Relay](https://www.aliexpress.com/item/4000045425145.html)
  * [Thermo-resistant cables AWG18 (1m black & red) and AWG22 ( 5m black,red,yellow & blue )](https://www.aliexpress.com/item/4000627624331.html)
  * [Spade connectors M/F 6.3mm](https://www.aliexpress.com/item/1005002765359666.html)
  * [Piggy Back spades](https://www.aliexpress.com/item/32800326782.html)
  * Power Supply: _Just one of the two options is needed_
    * OPTION 1 - _PREFERRED_
      * [12v/1A Power Supply](https://www.aliexpress.com/item/33012749903.html)
      * [12v to 5v stepdown](https://a.aliexpress.com/_uAvaIl)
    * OPTION 2
      * [5V/2A PSU](https://www.aliexpress.com/item/4001068579272.html)
      * [Plug Wires](https://www.aliexpress.com/item/1005001727355478.html)

### EXTENDED FUNCTIONALITY
_Will enable pump control based on active pressure feedback, thies enables pressure and flow profiling as well as other functionality._

  * [RobotDYN dimmer module - Dimmer 4A-400V](https://bit.ly/3xhTwQy)
  * [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)

* **Gaggia Classic Specific:**

  * [T-fitting | PE/6mm ](https://www.aliexpress.com/item/1005003750203358.html)
  * [Transducer Fitting | PLF/6-02 (6mm-1l4)](https://www.aliexpress.com/item/1005003753827787.html)
  * [Hose 1 meter | ID 4mmx6](https://www.aliexpress.com/item/1005004639155885.html)
  * [1-Bit AC 220V Optocoupler](https://www.aliexpress.com/item/1005003228104606.html)  _Not needed if one wants to jump straight to STM32_ 

!> If planning on adding scales check the scales section as the optocoupler is not the right choice then.

* **Gaggia Classic Pro Specific:**
<div style='color: red'>:heavy_exclamation_mark:Please read the warning related to the hose choice.</div>

  * **Hose:**  _Just one of the two hose options is needed_ 
    * [ID4mm x OD9mm](https://www.aliexpress.com/item/1005001729453617.html) **READ BELOW WARNING**
    * [Saeco](https://www.ebay.co.uk/itm/115431428020) **HIGHLY RECOMMENDED ORIGINAL PART, PROBABLY AVAILABLE LOCALLY**
  * [Transducer Fitting | 6mm Barb x 1/4"](https://www.aliexpress.com/item/32827914331.html)
  * [T-fitting | 6mm](https://www.aliexpress.com/item/1005002749996345.html)
  * [Clamps | 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html) 

!> The Aliexpress hose IS NOT rated as high as the original SAECO hose, please use common sense when operating the machine if you can't buy the recommended original SAECO hose use the exact size recommended here as pressure resistance is determined by the hose diameter as well.

* **STM32 UPGRADE PACK:**

_Will allow for all the additional features listed in the Featrures table under the STM32 column_

<div style='color: red'>:heavy_exclamation_mark:Please read the warning related to the STM32 availability.</div>

  * [STM32F411CEU6](https://www.aliexpress.com/item/1005001456186625.html) **MAKE SURE THE PROPER BOARD IS SELECTED**
  * [ST-Link V2](https://www.aliexpress.com/item/32860702733.html)
  * [ADS1115](https://www.aliexpress.com/item/32869421559.html)
  * [5V RELAY](https://a.aliexpress.com/_vpUdrT) **Supersedes the 1-bit opto**

  !>Due to global shortages the semiconductors sector was hit hard, as a result STM32 chips are quite hard to obtain, be wary of resources selling fakes or low quality clones which will lead to either bad experience or no experience.
  If the reccommended seller doesn't have it in stock you will have to shop around.

* **SCALES:**

_Will enable for realtime shot weight tracking without external scales, be aware this is a highly advanced installation step and requires in depth understanding to achieve optimal results, it can't be simplified due to the higly sensitive nature scales require in terms of both installation as well as various tolerances._

<details>
<summary>Scales V1 (Click to expand)</summary>

  * [500g LOADCELLS x 2](https://www.aliexpress.com/item/32670225988.html)
  * [HX711 amplifier x 2](https://www.aliexpress.com/item/33041823995.html)

  * **Printing materials**
    * [Gaggia Classic Load Cell Integration (no drill)](https://www.thingiverse.com/thing:5276489)
    * [Gaggia Classic Pro Load Cell Integration (no drill)](https://www.thingiverse.com/thing:5276492)
</details>

<details>
<summary>Scales V2 (Click to expand)</summary>

  * [750g LOADCELLS x 2](https://www.aliexpress.com/item/1644918827.html)
  * [HX711 amplifier x 2](https://www.aliexpress.com/item/33041823995.html)

  * **Printing materials**
    * [Gaggia Classic & Classic Pro scales housing](https://www.printables.com/model/285370-gaggia-classic-pro-scales)
</details>


* **Gaggiuino Housings**

_Choose what's best for you, naturally you can mix and match as well, for example the LCD enclosure printed from the Gaggiuino v2 files set and all the components going inside the machine using the INTERNAL COMPONENTS HOUSING designs._
  * **HOUSINGS**
    * [Gaggiuino v2 GCP LCD Enclosure](https://www.thingiverse.com/thing:5236286)
    * [Gaggiuino v2 GC LCD Enclosure](https://www.printables.com/model/280617-gaggiuino-gaggia-classic-touchscreen-housing-and-f)

  * **INTERNAL COMPONENTS ONLY HOUSING**
    * [Gaggiuino **Nano** Internal Component Housing](https://www.printables.com/model/262346-gaggiuino-nano-internal-component-housing)
    * [Gaggiuino **STM32-Blackpill** Internal Component Housing](https://www.printables.com/model/269394-gaggiuino-stm32-internal-component-housing)

**Cheap services to order the prints if not owning a printer:**

  * [cloudcraft3d.com](https://craftcloud3d.com/)
