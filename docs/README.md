!> ***!! WARNING !!***

!> *First and foremost please do not underestimate the danger of electricity or overestimate your ability to work around it. Only start working on your machine while it's  completely disconnected from the mains power socket, also by agreeing to follow the below guide I cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, friend or gold fish and it will be entirely your fault!*

**_Total estimated install time will be based on understanding and experience._**

**_Documentation contributors:_**
* [mr.toor](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
* [Samir Kouider](https://github.com/samirkouider)

# Features / Completeness 
**BASE:**
- [x] Integrated Housings - **credits** [![I'm on Reddit](https://img.shields.io/reddit/user-karma/combined/LikeableBump1?style=social)](https://www.reddit.com/user/LikeableBump1 "I'm on Reddit")
- [x] Customised UI/UX - **credits** [![I'm on Reddit](https://img.shields.io/reddit/user-karma/combined/different-wishbone81?style=social)](https://www.reddit.com/user/different-wishbone81 "I'm on Reddit")
- [x] Brew/Steam temp control
- [x] Shot timer
- [x] Graphing
- [x] Realtime values update/save

**EXTENDED:**
- [x] Pre-infusion
- [x] Pressure profiling
- [x] Manual pressure control
- [x] Descale program
- [x] Integrated scales
- [ ] Saving/Loading profiles
- [ ] Web interface
- [ ] OTA updates
- [ ] Advanced Flow control

# Community speaks:
[![Video](https://img.youtube.com/vi/MxPNQRCxQZc/maxresdefault.jpg)](https://youtu.be/MxPNQRCxQZc)

***USAGE:***

 * **BOILER**      - sets the desired temperature at the boiler level
 * **OFFSET**      - sets the offset value used to calculate the real water temperature
 * **HPWR**        - sets the relay start pulse length
 * **M.C.DIV**     - sets the main cycle divider(aka non brew heating behaviour), used in conjunction with HPWR
 * **B.C.DIV**     - sets the brew cycle divider
 * **Brew(Auto)**  - all pressure settings are following the bellow:
   * PREINFUSION - enables pre-infusion
     * Time       - sets the length of the PI phase
     * Bar        - sets the max reachable pressure for the PI phase
     * Soak       - sets the length of the soaking(blooming) phase
   * P-PROFILING - enables AUTO pressure profiling mode
     * Start      - sets the desired starting point  of the PP phase, can be High->Low or Low->High.
     * Finish     - sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
     * Hold       - sets the length of the PP hold period, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
     * Length     - sets the length(aka speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.
 * **Brew(Manual)** - allows for manual pressure control at brew time.
 * **DESCALE**     - enables the descaling program, at this point there's only one default behaviour:

         flush - 10s x5 at 2bar
         flush - 20s x5 at 1 bar
         idle  - 5min at 0 bar
_Descaling should be done with a blind basket in the pf and the pf locked in the group, steam valve open for the water to flow in a separate reservoir and water tank fully loaded with water mixed with descale solution._
 

# **Deprecations:**
* NANO Development:
> Arduino NANO based development has reached EOL, if it's feature set is enough for your needs grab the code from [release-nano-final](https://github.com/Zer0-bit/gaggiuino/releases/tag/release-nano-final-v2)
* Pressure control:
> Pump actuation was switched form PWM to PSM and as a result, if PWM is preferred then **release-0.2.2** is the one to stay on. Static pressure control is only possible by using PWM as a result if there are no pressure sensing devices installed it's advised to stay on PWM. 

* **ACS712**
> As of **release-0.2.3** the hall effect sensor was deprecated due to it's unstable work and configuration complexity, it is highly recommended to update to the optocoupler board that took it's place as not doing that means being stuck on **realeas-0.2.2** feature set.

# TIMELINE
## Initial
> * Purchase the parts listed, from Ali and expect a wait of 21 days. Any parts purchased anywhere else are done so at your own risk (they've not been tested).
> * Connect test components described in the doc to Arduino - using the expansion board twist the ends of cables and connect to the screw terminals. At this point using DuPont connections is fine but please note later we will solder to the boards or pins.
> * Flash Arduino and LCD with code.
> * Plug in and test - check for a temp reading (it will contain the default offset of 7 degrees which means the initial temp will be room temp -7).

## Base
> * Plan out where the components will sit inside the machine to determine cable length
> * Create piggyback cables. Determine what switch points to piggyback from.
> * Wire in power delivery method - isolate the board using an enclosure or tape it up after wiring.
> * If you have the eco timer, disable it.
> * Swap out thermocouple - ease out the boiler (don't fully remove it) in order to gain more access.
> * Install the max temp board - isolate the board using an enclosure or tape it up after wiring.
> * Place and wire relay - attach the brew thermostat wires to the SSR relay and sit/attach the back plate or relay on the body of the machine, add some thermal paste
> * Re-Wire the steam switch for steam handling - you need to swap the brew thermostat wires (above step) for the steam thermostat wires and bridge the brew thermostat wires together then take some wires from the steam switch to the Arduino.
> * Wire brew switch for continuity 
> * Test.

## Extended
> * Install dimmer - isolate the board using an enclosure or tape it up after wiring.
> * Install the pressure sensor.
> * Install the load cells.

## Finish
> * Make sure all connections are proper i.e, no metal is exposed and well isolated, all soldering is perfect and wrapped in heat-shrink.
> * Flash the Arduino and LCD with the latest version from GitHub (there could have been changes since).
> * Record your first start. Post this to #first-start on discord.
> * Find out your regional settings and set them in the settings of the Arduino.
> * Check all other settings save correctly.
> * Record your first shot. Post this to #first-shot on discord.


# **BILL OF MATERIALS**
***The code has been designed to be plugable, meaning there is a minimal hardware configuration one can start with if certain features are not something of interest, it's all appropriately split under "BASE" or "EXTENDED" functionality (see bellow).***

#### **BASE FUNCTIONALITY** 
***
* [Arduino Nano AT328](https://bit.ly/3eXSfXZ)
  * [Arduino Nano expansion board](https://www.aliexpress.com/item/32831772475.html?spm=a2g0o.store_pc_allProduct.8148356.21.7ed173b9bTMew3)
* [2.4" Nextion LCD](https://bit.ly/3CAUzPj)
* [MAX6675 thermocouple](https://bit.ly/3ejTUIj) 
* [C-M4 screw K-Type thermocouple sensor](https://bit.ly/3nP1WMm)
* [40DA SSR Relay](https://bit.ly/33g1Pjr)
* [Thermo-resistant cables AWG15 and AWG20 ( 1m black/red ) and AWG26 ( 5m black/red/yellow/blue )](https://bit.ly/3tjSQbI)
* [Spade connectors M/F 6.3mm](https://bit.ly/2Sjrkhu)
* Power Supply:
  * [12v/1A Power Supply](https://www.aliexpress.com/item/33012749903.html) and [12v to 5v stepdown](https://a.aliexpress.com/_uAvaIl) (these two should only be used together)

#### **EXTENDED FUNCTIONALITY**
***
* [RobotDYN dimmer module - Dimmer 4A-400V ](https://bit.ly/3xhTwQy)
* [Pressure sensor - 0-1.2Mpa](https://www.aliexpress.com/item/4000756631924.html)
* **GC specific:**
  * [Fitting - 6-02/PCF ](https://www.aliexpress.com/item/4001338642124.html)
  * [Transducer Fitting - 6mm/PE](https://www.aliexpress.com/item/4001338085412.html)
  * [Hose - 6x4 - 1 meter](https://www.aliexpress.com/item/4000383354010.html)
  * [1-Bit AC 220V Optocoupler](https://www.aliexpress.com/item/1005003228104606.html)
* **GCP specific:**
  * [Hose - 4mm x 9mm](https://www.aliexpress.com/item/1005003157483270.html)
  * [Transducer Fitting - 6mm x 1/4](https://www.aliexpress.com/item/33059380672.html)
  * [T-fitting - 6mm](https://www.aliexpress.com/item/1005002749996345.html)
  * [Clamps - 100pcs and plier](https://www.aliexpress.com/item/1005003341137707.html)



#### **Housing variants**
 * [Gaggiuino v1](https://www.thingiverse.com/thing:4949471)
 * [Gaggiuino v2](https://www.thingiverse.com/thing:5236286)

 **Cheap services to order the prints if not owning a printer:**
   * [cloudcraft3d.com](https://craftcloud3d.com/)

<!-- # **[Gaggia Classic](https://zer0-bit.github.io/#/gc/gaggia-classic)**

# **[Gaggia Classic Pro / New Classic](https://zer0-bit.github.io/#/gcp/gaggia-classic-pro-new-classic)**

# **[Learnign Materials](https://zer0-bit.github.io/#/learning/learning-materials)** -->