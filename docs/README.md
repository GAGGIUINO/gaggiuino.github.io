***!! WARNING !!***

!> *First and foremost please do not underestimate the danger of electricity or overestimate your ability to work around it. Only start working on your machine while it's completely disconnected from the mains power socket, also by agreeing to follow the below guide I cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, friend or gold fish and it will be entirely your fault!*

**_Total estimated install time will be based on understanding and experience._**

**_Documentation contributors:_**

- [mr.toor](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
- [Samir Kouider](https://github.com/samirkouider)

## Features / Completeness

### BASE

- [x] Integrated Housings - **credits** [![I'm on Reddit](https://img.shields.io/reddit/user-karma/combined/LikeableBump1?style=social)](https://www.reddit.com/user/LikeableBump1 "I'm on Reddit")
- [x] Customised UI/UX - **credits** [![I'm on Reddit](https://img.shields.io/reddit/user-karma/combined/different-wishbone81?style=social)](https://www.reddit.com/user/different-wishbone81 "I'm on Reddit")
- [x] Brew/Steam temp control
- [x] Shot timer
- [x] Graphing
- [x] Realtime values update/save

### EXTENDED

- [x] Pre-infusion
- [x] Pressure profiling
- [x] Manual pressure control
- [x] Descale program
- [x] Integrated scales
- [ ] Saving/Loading profiles
- [ ] Web interface
- [ ] OTA updates
- [ ] Advanced Flow control

## Community Speaks

[![Video](https://img.youtube.com/vi/MxPNQRCxQZc/maxresdefault.jpg)](https://youtu.be/MxPNQRCxQZc)

## Usage

 - **BOILER**: Sets the desired temperature at the boiler level
 - **OFFSET**: Sets the offset value used to calculate the real water temperature
 - **HPWR**: Sets the relay start pulse length
 - **M.C.DIV**: Sets the main cycle divider (aka non brew heating behaviour), used in conjunction with HPWR
 - **B.C.DIV**: Sets the brew cycle divider
 - **Brew(Auto)**: All pressure settings are following the bellow:
   - **PREINFUSION**: Enables pre-infusion
     - **Time**: Sets the length of the PI phase
     - **Bar**: Sets the max reachable pressure for the PI phase
     - **Soak**: Sets the length of the soaking (blooming) phase
   - **P-PROFILING**: Enables AUTO pressure profiling mode
     - **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
     - **Finish**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
     - **Hold**: Sets the length of the PP hold period, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
     - **Length**: Sets the length (AKA speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.
 - **Brew(Manual)**: Allows for manual pressure control at brew time.
 - **DESCALE**: Enables the descaling program. At this point there's only one default behaviour:

   ```none
   flush - 10s x5 at 2bar
   flush - 20s x5 at 1 bar
   idle - 5min at 0 bar
   ```

   Descaling should be done with a blind basket in the portafilter and the portafilter locked in the group, steam valve open for the water to flow in a separate reservoir and water tank fully loaded with water mixed with descale solution.

## Deprecations

- NANO Development:

  > Arduino NANO based development has reached EOL, if its featureset is enough for your needs grab the code from [release-nano-final](https://github.com/Zer0-bit/gaggiuino/releases/tag/release-nano-final-v2)

- Pressure control

  > Pump actuation was switched from PWM to PSM and as a result, if PWM is preferred then `release-0.2.2` is the one to stay on. Static pressure control is only possible by using PWM as a result if there are no pressure sensing devices installed it's advised to stay on PWM.

- **ACS712**

  > As of `release-0.2.3` the hall effect sensor was deprecated due to its unstable work and configuration complexity. It is highly recommended to update to the optocoupler board that took its place as not doing that means being stuck on `release-0.2.2` feature set.

## Timeline

### Initial

1. Purchase the parts listed from Ali and expect a wait of 21 days.

   Any parts purchased anywhere else are done so at your own risk (they've not been tested).

2. Connect test components described in the doc to Arduino.

   Using the expansion board, twist the ends of cables and connect to the screw terminals. At this point using DuPont connections is fine but please note later we will solder to the boards or pins.

3. Flash Arduino and LCD with code.

4. Plug in and test.

   Check for a temp reading. It will contain the default offset of 7 degrees which means the initial temp will be room temp -7.

### Base

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

### Extended

1. Install dimmer - isolate the board using an enclosure or tape it up after wiring.
2. Install the pressure sensor.
3. Install the load cells.

### Finish

1. Make sure all connections are proper i.e., no metal is exposed and well isolated, all soldering is perfect and wrapped in heat-shrink.
2. Flash the Arduino and LCD with the latest version from GitHub (there could have been changes since).
3. Record your first start. Post this to [#first-start](https://discord.com/channels/890339612441063494/919183771079692328) on Discord.
4. Find out your regional settings and set them in the settings of the Arduino.
5. Check all other settings save correctly.
6. Record your first shot. Post this to [#first-shot](https://discord.com/channels/890339612441063494/910972035205857320) on Discord.

# **Bill of Materials**
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



#### **Housing variants:**
 * [Gaggiuino v1](https://www.thingiverse.com/thing:4949471)
 * [Gaggiuino v2](https://www.thingiverse.com/thing:5236286)

 **Cheap services to order the prints if not owning a printer:**
   * [cloudcraft3d.com](https://craftcloud3d.com/)


# Gaggia Classic

## Requirements

### Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)

  Needed to upload the code `.ino` to the arduino ROM.

  [Libraries](https://www.arduino.cc/en/Guide/Libraries?setlang=en) to add:

    - Library manager:
      - Easy Nextion Library
      - MAX6675 by Adafruit
      - TimerInterrupt_Generic

    - External libraries:
      - PSM: https://github.com/banoz/PSM.Library
      - HX711: https://github.com/banoz/HX711

- [Nextion Editor](https://nextion.tech/nextion-editor/)

  - Only necessary if planning on editing the ".HMI" file to ammend the LCD functionality*

- [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)

  - USB driver so your system recognizes the Arduino clone board. Let's say I have found this the hard way as apparently the majority of cloned Arduinos use a cheaper USB controller compared to "genuino".


## Schematics & Diagrams

### Schematics

[GAGGIA Classic](https://user-images.githubusercontent.com/42692077/161397293-82df427a-2ac2-4226-bdc6-fa831a962265.png)

### Diagrams

[GAGGIA Classic](https://user-images.githubusercontent.com/42692077/160548957-88c93198-6d81-4081-8db6-552b6f6c5281.png)

---

!> First and foremost please do not underestimate the danger of electricity or overestimate your ability to work around it. Only start working on your machine while it's completely disconnected from the mains power socket, also by agreeing to follow the below guide I cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, friend or gold fish and it will be entirely your fault!

## Pre-Assembly

First we need to understand what goes where. The schematics aren't really rocket science but for someone who's never disassembled or has no experience working with electrical circuits, it might get confusing really fast so I will try to describe it as simple as possible yet limited by my vocabulary.

First let's check that the setup works as expected while outside the machine so you don't have it all installed and realise just afterwards it's not reading any temperature because of a faulty component or the relay doesn't switch between the ON/OFF modes.

>**Note 1 - no permanent connections are needed during testing so no soldering needed for now.**
>
>**Note 2 - the 5v/GND Arduino board pins will be shared between all the connected devices.**

### Arduino Connections

1. Connect the MAX6675 module to the Arduino board using the pins defined in the code. You can find them defined at the top of the `.ino` file:

    MAX6675  |  Arduino
    ---------|-----------
     VCC     |   5v
     GND     |   GND
     SCK     |   D6
     SO      |   D4
     CS      |   D5

2. Connect the relay. For now only connect the circuit controlling ports to check whether the relay LED indicates the power states:

    Relay   |  Arduino
    --------|-----------
      4     |   GND
      3     |   D8
      
   **Relay ports [1] and [2] are the high voltage circuit breaker**

3. Plug the arduino board in using the mini USB cable that came with it and upload the code to the Arduino board. 
   - Note: Uploading won't work with the LCD connected.

4. Nextion LCD wiring:

    Nextion  |  Arduino
    ---------|-----------
      TX     |   RX
      RX     |   TX
      VCC    |   5v
      GND    |   GND
      
5. Upload the LCD ROM code:

    **Method 1** 

      - Copy the `.tft` file to a FAT32 formatted microSD card and upload onto the LCD panel using the onboard card reader.

    **Method2** 

      - Open the `.HMI` file using Nextion Editor and using the **File** menu upload it to a microSD card.
      >*Note: card needs to be FAT32 formatted*

6. After the upload is finished get the card out and power cycle the LCD.

7. You should see temp readings on your screen if everything went according to plan.

8. Test the thermocouple/relay combo operation:

    Apply some heat to the thermocouple end and see whether the relay LED operates in HIGH/LOW modes.
    
    Due to the way the Arduino design works as well as the nature of how the on-board ADC functions, in order to avoid a loop in regards to the **BREW MODE**, it's required to connect the pins A0 -> GND, this is only needed if the ACS712 sensor board is not connected to the Arduino.

At this point if all the above works as expected you're ready to install it all inside the machine. For this we'll need to prepare some splitters that we'll use to connect to the Gaggia internals without introducing any permanent modifications so in the event of a desire to revert to stock it's a few disconnects away!

### Power Delivery

Powering using the [ 12v ] power supply module + [ 5v ] stepdown convertor is the recommended way.

Follow the scheme:

| PS  | Arduino |
|-----|---------|
| 5v  |   5v    |
| GND |   GND   |

!> Do not use the USB port to power the Arduino-connected boards. The low power capacity of the on-board voltage regulator will eventually lead your Arduino to fail. You've been warned!

### Steam Detection

1. Disconnect all the steam switch high voltage wires
2. Bridge the wires connected to the steam switch poles 1 and 2.
3. Bridge the steam thermostat wires.
4. Connect steam switch poles 3 and 4 to the arduino nano like in the table bellow using some AWG26 wires.
5. Make sure you secure all the left disconnected wires so they don't make any accidental contact.

![GC - steam handling](https://user-images.githubusercontent.com/42692077/147904917-feeb3230-3ea0-460c-82de-4ad16034a48e.png)

GC SWITCH| Arduino
---------|-----------
   3     |   D7
   4     |   GND

### Brew Detection

The high voltage circuit control ports will splice into existing brew switch wires.

OPTOCOUPLER|  Arduino
---------|-----------
VCC   |   5v
GND   |   GND
OUT   |   A0   

### Dimmer

Dimmer high voltage circuit control ports will act as a passthrough for the pump LIVE and NEUTRAL wires.

Dimmer  |  Arduino
--------|-----------
VCC   |   5v
GND   |   GND
Z-C   |   D2
PSM   |   D9
   
### Pressure Handling

Transducer|  Arduino
----------|-----------
RED      |   5v
BLACK    |   GND
YELLOW   |   A1

## On-Machine Assembly

### Don't Electrocute Yourself

Disconnect your machine from the power source.

As always with such projects, common sense should be applied at all times, it's expected people doing such sort of modifications will have some basic understanding.

!> AGAIN!!! Triple check your machine is disconnected from any power sources, even better just pull the power cable out of it if you haven't done so yet!

### Base Functionality

1. Take off the top cover by unscrewing the 2 top screws. You should be able to see something similar to the below image minus the SSR relay:
  ![Top-down view into the disassembled Gaggia Classic](https://db3pap006files.storage.live.com/y4m4pob4r1pDtjBPqIyA-dqHOH_eZDJaf6W2dYdHlIh8G8OWusXig9WUKOA-iBCk2QRN-lL3ajrWDDUBASx_frpWqz_2z1dxeAnksAKKysKqL-eXE9PVRYeA2SdmS_DSkAA3TJ5ZVe3ybpkLYV0-PDKLjEhxNZluA_UX8ektw8kGW4PXKQeQU-UUJtjuaDSYKsG?width=3496&height=4656&cropmode=none)

2. Prepare 2 splitters like in the below image using the AWG15 cable, be sure one splitter to be black(negative) and one red(positive)
  ![Prepared splitter](https://db3pap006files.storage.live.com/y4mGdTrz4hXNuu3rvDk5qro2WGn5xqy8ZVGwhJSXFSDqmJErI8dYufS1H-l_PnIIa0HffKXPuPkvbRjNHt_2OogxaW8UohuFKatz3BfjjK8NEGmynX2unmeZ6opV3_gd-u0f3cCAlgh9nF5spGDt12McFxpxzsatrSK2YuRgrFTfFnxMvMmiXss0XSLrZGx5xIa?width=769&height=1024&cropmode=none)

3. Mark your top left power connector so you don't mix them up (even though it's not that hard to understand which one is which)
  ![Wiring harness assembly on back of button panel](https://db3pap006files.storage.live.com/y4mM3HVfjbCIdcPtx16eN0pEgGC4Z0ih04agqfBwI-NLtpUWvmlBFI23fT2LPVagGHXYsgRiIVq8oSjJckuZscCcdTKqq7GNxCK5GxRqsp2pCZinopGHCdqJtnZqMCFBlSq-yOT-vNtsATxE734AN05DO47i1as2NSW4E-87r78gV7kpP_sy9tHiBqey26s9xP0?width=769&height=1024&cropmode=none)

4. Disconnect all 3 of them as you'll use the middle and bottom ones for power sharing.
  ![More disconnected connectors](https://db3pap006files.storage.live.com/y4m9fZvq6wrObA7QFSkvQpfFyOinQbfs-u_E8DLZqp784cPLcUIlZKoZeqbLWn3JPAElseiwa0G1KuN-yXJfOx_4N-3k-IU0YprmK-YHBYEG-33CaUXTEWVPNVwjy6y7kMyaDvbEzH445Su6hSKNqZqAPXmwJQlIH8lAQmXaTduAk3WIsUrZSw2J0lPhRRVEqzX?width=769&height=1024&cropmode=none)

5. The hardest part will be now in my opinion as you'll have to unscrew the bottom boiler stock thermostat and screw back in the new thermocouple. Be sure to apply some thermal paste on the thermocouple threads. (Just a teeny tiny bit.)
  ![Top-down view of disconnected connectors](https://db3pap006files.storage.live.com/y4m9lHvLCobQ3DlmTfqYPJvV1M-z2T0_GMxgeE21-hqP3nfu5UwB1PTyPF6rIT5A6ebeyv9TXwEfCbB1SBwkyVy0r8AIbrLGogaWcebzjSpaskThwbn-S45n5E-IAkeKPJgYAjLMPYeQPjALL--D1CC60ZFaOGsaHtAOSNvcb1Y4X2IEWV7n4bUP4v40sKawusJ?width=496&height=660&cropmode=none)

6. Prepare 2 cables you'll use to connect the cables disconnected from the thermostat to the port 1 and 2 of the SSR relay. Use the red cable for that. They shouldn't be too long, about 10cm will suffice, one end should be crimped with a male spade connector and the loose end screwed to the relay and attach the relay to the machine case itself, I have no clue what screw size I used as I have just matched one by trial and error lol, but be sure to apply some thermal paste to the SSR backplate that will make contact with the metal case of the machine.
  ![Solid-state relay (SSR)](https://db3pap006files.storage.live.com/y4m3ZmhHEobr2VPen1wScEO8AMLiaOVfWjsnW8Aw4645PaRXerrLpV8iZmZjzU88KDPmKEfPXbUBqYhn6ejVOfXIB7hgucmljyOLL54tqWKUahFoqnYEf2rBh0TRXjFEtzAvptdT3W8nSTzc96sfvD8hcK-pQEeEaYaLaq4gpNaKyXdWQtETpPtrzpMd1mLzuyb?width=2584&height=2140&cropmode=none)

  So you end up having them connected like this:
    ![alt](https://db3pap006files.storage.live.com/y4m5HfjPvkFSOtSm8gkTJJ4saqEw8dcB1no2eoaHcDZjYD9OV95tBnrG8tqtRuOcor7aFZrIRw7167k4QGMUneOPATitBFctkgdklxWOohMyBir3zLdm9fkAnTQW8TquTZouRh9rzKSC0t5bkerK1g8AzlFYTfuZoDPQ3juFiOJ19JKiL6VpODn40Z1q8JwVpGy?width=2625&height=2831&cropmode=none)

7. Prepare 2 more 10cm cables (also colour coded accordingly) which should be crimped with M/F spade connectors at each end, the female end will go in Gaggia's front panel and the male end will go to the female end of the previously prepared (2) splitters, as in the below image:
  ![alt](https://db3pap006files.storage.live.com/y4m2LoENSwBicOmRtvdMKM9srnf4tfNECBkaNXWkkGxxEAMbc_BuQhQnYgVH7h0FZ52NIDiIudlx2NhDkm1747Y9wT60F7uoHMJu-lx_MF-mPXBbzOyeZNVuEdrISfsi56v7VYKNZIgby3qUD922gMJCI177q0IttLhWXn_VM9OamG0FvyKQ3T26uqOye6H50eV?width=769&height=1024&cropmode=none)

  ![alt](https://db3pap006files.storage.live.com/y4myMKUSADo1HIGEXQ42p9tP1UKzL2aUqI6gCv3st6cBqR921Y-xWkhHB9QYaUlubJC-wCs5swyMaXX-p9LJu0qDgOgMKwkMyW-KUdUkkQWZ7-VdJNZiWv2duaBEcFtGo34uX1_-mqF66PpgseniGFKGhJmO-o5n8Pb2TP2it0vyQBcLAgX00jzVl-H6L5NeVzE?width=769&height=1024&cropmode=none)

8. Connect the front panel cables to any of the free male ends of the splitters as well, black one for the negative cable and red for the positive one (on my machine the positive is having 2 cables crimped together).

9. To power the Arduino system I have used an old 5v mobile charger which I'm sure all of us have laying around. Just solder 2 cables to the 2 ends of the charger and for the other ends use 2 F spade connectors, after which plug them to the remaining 2 splitter (2) ends.
  ![alt](https://db3pap006files.storage.live.com/y4myMKUSADo1HIGEXQ42p9tP1UKzL2aUqI6gCv3st6cBqR921Y-xWkhHB9QYaUlubJC-wCs5swyMaXX-p9LJu0qDgOgMKwkMyW-KUdUkkQWZ7-VdJNZiWv2duaBEcFtGo34uX1_-mqF66PpgseniGFKGhJmO-o5n8Pb2TP2it0vyQBcLAgX00jzVl-H6L5NeVzE?width=769&height=1024&cropmode=none)

10. Now you're ready to connect everything to the Arduino like you did, when testing everything.

  One piece of advice would be to solder all the Arduino connected cables as during the machine operation there is quite a bit of vibration and that can introduce all sorts of noise/frequent disconnects to certain pins which will lead to unexplained behaviours.

### Extended Functionality

#### Brew Detection

Gaggia Classic(pre 2018) ONLY

![GC - brew handling](https://user-images.githubusercontent.com/42692077/154805193-76068521-3ad4-4020-b2ee-8dab9394d4fe.png)

  * Prepare two **"Y"** splitters **BLACK** and **RED** with the ends crimped as follows: 
     * **RED SPLITTER:** 1 x **MALE**, 1 x **FEMALE**, 1 x **BARE**.
     * **BLACK SPLITTER:** 2 x **FEMALE**, 1 x **BARE**.
  * Wire connected to **STEAM** button pole **4** connects to BREW button pole **5**, original disconnected **BREW** pole **5** wire should be left disconnected but properly secured.
  * Connect the RED **"Y"** splitter to **BREW** switch pole **6** and plug the original connected wire to the **MALE** spade end, the **BARE** splitter end going to the optocoupler **L** terminal. 
  * Tap into the **PSU** splitter used for the **N** connection using the **BLACK** splitter and connect the bare end to the optocoupler **N**

#### Install The Robotdyn Dimmer Module

These image above is provided as a reference to understand how the connection through the dimmer is made, please check whether your dimmer high voltage ports placement differs from the above image before connecting the dimmer, it's very important to feed the IN wires properly.

![dimmer_guide](https://user-images.githubusercontent.com/42692077/162638303-dd1333b0-212f-41b5-be64-de8543dc1153.png)
  
![dimmer-install-info](https://user-images.githubusercontent.com/42692077/147135452-fb3931c5-ac48-4a61-91ff-1b4275aaccb2.png)

#### Install The Pressure Transducer

The pressure sensor will be tapping into the hose connecting the **pump outlet** and the **boiler inlet**, the way people connect it is up to individuals.

It's advisable after making the connections and just before connecting the transducer itself, turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings.

![New Project (11) (1)](https://user-images.githubusercontent.com/42692077/146647799-f4887edb-95ec-4a33-8561-4e4afda6256e.png)
  
<!-- this belongs in the GCP section

![New Project (12)](https://user-images.githubusercontent.com/42692077/146647809-970c0ccd-47c6-430c-9c71-9b651bab4bf4.png)

-->

# **Gaggia Classic PRO (New Classic)**


## 1.0 PROJECT REQUIREMENTS

### 1.1 Software requirements
1. [Arduino IDE](https://www.arduino.cc/en/software)
    >*Needed to upload the code ".ino" to the arduino ROM*


   **Libraries to [add](https://www.arduino.cc/en/Guide/Libraries?setlang=en):**
   
         Library manager:
          - Easy Nextion Library
          - MAX6675 by Adafruit
          - TimerInterrupt_Generic

         External libraries:
          - PSM > https://github.com/banoz/PSM.Library
          - HX711 > https://github.com/banoz/HX711

2. [Nextion Editor](https://nextion.tech/nextion-editor/)
    >*Only necessary if planning on editing the ".HMI" file to ammend the LCD functionality*
3. [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)
    >*USB driver so your system recognizes the Arduino clone board, let's say i have found this the hard way as apparetly the majority of cloned arduinos use a cheaper USB controller comparing to "genuino"*


# 2.0.0 TEST INSTALL
We are not installing inside the machine yet and we are doing minimal soldering at this point. We just want to test as much as we can to make sure we've not got any duds from a base functionality point of view.

We need to understand what goes where. The schematics in (**3.0.1 Schematics & Diagrams**) aren't really rocket science but for someone who's never disassembled or has no experience working with electrical circuits it might get confusing really fast. 

Note 1 - No permanent connections are needed during testing so no soldering needed for now.
Note 2 - The 5v/GND Arduino board pins will be shared between all the connected devices.

### 2.0.1 Arduino Config 
Place Arduino into the expansion board the correct way round. Power it through USB adapter for now during the testing phase.

Image of Arduino with pins soldered:

<img src="https://user-images.githubusercontent.com/53577819/154988207-3d54e924-3ab0-4e47-a4e9-188f7e839610.jpg" width="400" height="250">

Image of expansion with pins (solder from the bottom):

<img src="https://user-images.githubusercontent.com/53577819/154988218-26160147-e821-47e7-8152-d8ec0a8f0d43.png" width="400" height="250">

Make sure the terminals are correct way round and place the Arduino into the expansion board.

If you have to solder your pins then take the time now to get your soldering perfect. It'll save time in the long run. REFER TO APPENDIX *3.0.3 Recommendations* FOR SOLDERING GUIDES!

<img src="https://user-images.githubusercontent.com/53577819/154988330-430df58d-773c-4084-b7b3-921ca43909f2.jpg" width="400" height="250">

_**Attention! You are not soldering the Arduino to the expansion board itself. You are only soldering the pins to the Arduino and pins to the expansion board. The Arduino then just sits/connects into the expansion board pins.**_

### 2.0.2 MAX6675 Config
***
For the below section you are using **26AWG** cable to connect to the Arduino board.
 
**Refer to the appendix 3.2 for component wiring.**
***

You should have bought and received a MAX6675 board which comes with a test thermocouple. We're swapping this for the "C-M4 screw K-Type thermocouple sensor" as this is what will be replacing the original that's in the machine.
 
<img src="https://user-images.githubusercontent.com/53577819/154988392-619a5bc2-99cc-499d-8ad8-42792b094fd2.jpg" width="400" height="250">

<img src="https://user-images.githubusercontent.com/53577819/154988423-f741a369-ec60-4266-9544-0effedb57292.jpg" width="400" height="250">

### 2.0.3 Nextion Config
***
For the below section you are using **26AWG** cable to connect to the Arduino board. 
 
**Refer to the appendix 3.2 for component wiring.**
***

The correct screen size is **2.4**". If yours does not have markings for wiring then please see below image

<img src="https://user-images.githubusercontent.com/53577819/154988491-28c1e861-46bc-433b-a5f8-8e9eeb8b51ed.png" width="400" height="250">

<img src="https://user-images.githubusercontent.com/53577819/154988514-13a1d7af-f704-49b6-975b-aeee1318cf36.jpg" width="400" height="250">

### 2.0.4 Relay Config
***
For the below section you are using **26AWG** cable to connect to the Arduino board. 
 
**Refer to the appendix 3.2 for component wiring.**
***

This relay is what manages the temp by cutting the voltage when the thermocouple is at a set temp. 

<img src="https://user-images.githubusercontent.com/53577819/154988554-5be0bb0a-dcf2-4bf7-a70f-4c356d00eea6.jpg" width="600" height="450">

### 2.0.5 Software Install
#### Arduino Software Upload
Plug the Arduino board into PC/Mac using the mini-USB cable that came with it and upload the code to the Arduino board.
Note: Uploading won't work with the LCD connected

1. Download/Install [Arduino IDE](https://www.arduino.cc/en/software)
2. Download/Install [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)
3. Download the latest version of Gaggiuino from the GitHub main repository.  Copy the unzipped files to an easily accessible location
4. Add Libraries:
* Click Sketch\Include Libraries\Manage Libraries
* Type in the Library name and install most recent version
* Install 2 Libraries:
  * Easy Nextion Library
  * MAX6675 by Ada-fruit
5. Add External Libraries:
* Download Library Zip Files:
  * PSM
**Files must be unzipped** to the Arduino Library folder (default path is located in your local documents folder.  You should see the added libraries from step 4 here as well.)
6. Open Gaggiuino.ino (located in Gaggiuino folder from step 3). If prompted to create a sketch folder, press OK

**AT THIS POINT AFTER INSTALLING LIBRARIES RESTART THE IDE SOFTWARE**

7. Unplug the LCD from our Arduino Board mock setup
8. Plug the Arduino in via USB cable (must be a data transfer cable, not just a power cable)
9. Set Board, Processor, Port:  Navigate to “Tools” in the top menu: 
* Board: “Arduino Nano”
* Processor: “ATmega328P”
* * Use the “Old Bootloader” version, but results may vary depending on your hardware.
* * When plugged in and the “port” section should be active and something should be selected.  If not manually select the port that contains the Arduino.  Mine was on “Com4”. Try unplugging then plugging in again if it doesn't work.

<img src="https://user-images.githubusercontent.com/53577819/154988600-334dd985-f9c1-4aed-a55c-ab5c03ef51ab.png" width="600" height="450">
 
10. Press Upload (***Make sure LCD is UNPLUGGED before uploading otherwise upload will fail***)
11. If upload is Successful, unplug Arduino Board from computer

#### Flashing the Nextion LCD Software Upload
_Uploading the LCD ROM code_
Method 1 - Download and unzip the *.tft file on a FAT32(MS-DOS (FAT32)) formatted microSD card and upload on the LCD panel using the onboard card reader.

Method 2 - Open the .HMI file using Nextion Editor and using the File menu upload it on a microSD card

1. Plug LCD back into Arduino Board Setup
2. Locate “nextion-discovery-lcd.tft” or “nextion-basic-lcd.tft” (depends on what you purchased)
3. Copy the file to a FAT32 formatted MicroSD card
* If on Mac for some reason it adds a second file beginning with a "." use terminal to change directory to the microSD and use "rm ._nextion-*YOUR-VERSION*-lcd.tft" to remove that file.
4. Place MicroSD card inside the Nextion display
5. Power on the Arduino Board Setup and installation should occur automatically
6. Once “successed” reboot the Arduino

### 2.0.6 Test

You should now see the Gaggiuino project on the LCD. If your connections are all right (and well secured), you should see a temperature reading from the thermocouple (temp reading will contain the default offset of 7 which means the initial temp will be - room temp -7)

Try applying heat with your hand and you should see the temperature respond (if not, I recommend confirming all connections are correct and adequately tightened.  Mine did not respond at first and turned out one of the connections to the Arduino board was not tight enough)

If everything looks good, move on to Installing into the Gaggia Classic Pro

_**If all the above works as expected you're ready to install it inside the machine.**_

# 2.1.0 INSTALL
***

_**!! WARNING !!**_

_**Do not underestimate the danger of electricity or overestimate your ability to work around it.**_

_**Only start working on your machine while it's completely disconnected from the mains power socket, also by agreeing to follow the below guide I cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, friend or goldfish and it will be entirely your fault!**_

***

Undo everything as we will now install into the machine. 

All components except the Arduino and LCD will be internal to the machine. Remember this when wiring the LCD. 
For each of the components we want to start guesstimating on cable length. You can do this by placing components where you want to place them. Close together components can share similar wiring i.e. 5v and GND.

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on pin connections to the Arduino. 

### Base Functionality
#### 2.1.1 Power Delivery
Take off the top cover of your machine by unscrewing the 2 top screws. Be sure to mark your top left power connector so you don't mix them up (even though it's not that hard to understand which one is which).

Prepare splitter cables with the below specs:
1. Black splitter, 15AWG, 10cm, female end, male end, male end
2. Red splitter, 15AWG, 10cm, female end, male end, male end

Example of a red and black splitter:

<img src="https://user-images.githubusercontent.com/53577819/154988645-5f1da175-7d09-437a-ac2c-f64e16f3a564.jpg" width="600" height="450">

The female end will go in Gaggia's front panel. One male splitter end will go into the connection that came out of the switch position the other male will be for some more wires further down.


<img src="https://user-images.githubusercontent.com/53577819/154988784-7ddbc106-4744-4d9f-8879-b9a107a9fe7c.jpg" width="600" height="450">


**Before trying to copy piggyback locations from below it’s recommended to check what the schematics say (3.0.1 Schematics & Diagrams).** 


By way of context, if looking inside the machine from the back, the left of the power switch is the brew switch. 
On the power switch - wire in the middle left as LIVE and middle right as GND 


<img src="https://user-images.githubusercontent.com/53577819/154979422-f78d41c4-87f4-4474-ab68-a3466d5e9e5e.jpeg" width="600" height="450">

The above translates to the following (**please be aware the image below has top connectors removed for clarity)**:

<img src="https://user-images.githubusercontent.com/53577819/154979529-eae513b2-00e3-40c9-a581-47be4da68edc.jpg" width="600" height="450">



If above standard schematics do not work it can be that your wiring is different. It is recommended to use a multimeter to test. 

<img src="https://user-images.githubusercontent.com/53577819/154982423-82b4bdb4-ca78-4077-90c0-77b349c8c3d2.JPG" width="600" height="450">



* Set it to 600V~ (AC) as shown above and test the connectors on the switches
* Just wiggle the connector on the switch out a touch to expose a tiny bit of metal where you put your lead on
* Use schematic to find a GND point
* Your live piggyback will show no voltage until the machine is switched on

As stated you want to find the connector that only shows voltage after flipping the machine machine on. 

If your LCD is on even though you've not flipped the machine switch on, this means you've piggybacked into the mains live which is constantly got voltage - this is not correct!



Please see some examples of known differences but really you should be testing with a multimeter.

**KNOWN - ECO - EU/UK - piggyback locations non-schematic:**

<img src="https://user-images.githubusercontent.com/53577819/154988901-b79270da-5bb3-4507-9ef2-57bf2e791d77.JPG" width="600" height="450">


Prepare 2 more cables with the below spec:
1. Black, 18/20AWG, about 15cm, female end, exposed end
2. Red, 18/20AWG, about 15cm, female end, exposed end

Connect the female end to the male end of the splitter cable from above step (match the colours)

If using the 5v PS - the 2 AC IN ports will be where the exposed end of your red or black piggyback cable go, it doesn't matter which way round (yes, you need to fiddle about getting wires in and solder correctly - recommended to trim, twist, tin and apply heat shrink).

<img src="https://user-images.githubusercontent.com/53577819/154989029-59ab20c6-fdda-4510-a9e0-50579b8e4a54.jpg" width="600" height="450">

Prepare more cables with the below spec:
1. Black, 26AWG, about 25cm, exposed ends
2. Red, 26AWG, about 25cm, exposed ends

In relation to the image above - the black will be connected to the GND and the red to the VCC the other ends are going to the Arduino. Please use the tables in **3.0.2 Appendix - Component Wiring** for details on wiring VCC and GND connections to the Arduino. 

_**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on! **_

**_If you have the ECO version (the machine turns off automatically after 20mins) bridge your brew switch with a 15AWG cable with two male ends, as per below:_**

<img src="https://user-images.githubusercontent.com/53577819/154989122-6237e1af-62d1-4289-901c-47c69ea3b1b9.jpg" width="600" height="350">

### 2.1.2 Thermocouple and MAX6675 Config 

Prepare the following cable to the below spec:

1. Black, 15AWG, 5cm, two male ends

[Detach the boiler](https://www.youtube.com/watch?v=0ipvBdWaVzQ) (only watch as far as the 5min mark) to gain enough access to remove the thermocouple and replace it with the m4 bolted thermocouple sensor. 

You’ll obviously need to remove the two connectors from the original thermostat first - which is located at the bottom of the boiler on the side closest to the power on switch.  

The small black cable you prepared with the male ends is used to bridge the two wires that you just disconnected from the brew thermostat. 


<img src="https://user-images.githubusercontent.com/53577819/154983715-46b1332f-f88a-4ef3-a625-b7f2788caf97.jpeg" width="600" height="450">


Now unscrew the original thermostat and replace with the m4 brass thermocouple. Be sure to apply some thermal paste (just a teeny tiny bit) on the _**threads only**_. It is important to barely tighten the m4 bolt at **barely** fingertip strength. 

<img src="https://user-images.githubusercontent.com/53577819/154989188-6bc38c2c-60df-47f6-98d9-b121f28438d6.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154989228-2f9a3669-551b-4f45-a82a-22b4fe41fa89.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154984016-714b6532-e31d-42d3-b2ee-cf064487db66.jpeg" width="600" height="450">


Now re-attach the boiler.
Check the appendix section **## 3.0.2 Component Wiring  2. MAX6675 WIRING**

_**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**_

### 2.1.3 Relay Config 

Prepare cables with below spec:

1. Red, 15AWG, 10cm, one male end, one exposed end
2. Red, 15AWG, 10cm, one male end, one exposed end

The 2 are used to connect the steam thermostat connections to port 1 and 2 of the SSR relay, so:

<img src="https://user-images.githubusercontent.com/53577819/154989308-14e9ea82-8a60-4f3d-bd9f-05dda6fa15c8.JPG" width="600" height="450">


Optional: might be a good idea to either tape up the exposed steam thermostat or remove it and tape up the exposed location.


<img src="https://user-images.githubusercontent.com/53577819/154989373-57093be0-ac48-4ac6-ad0b-d88adc2415d9.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154989357-ec8c4853-0bb9-4eec-8629-dfc76e72e725.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154989336-76f91fb5-2fdd-4c53-b968-e860af3f8505.jpg" width="600" height="450">

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on 3 & 4 connections to the Arduino. 

### 2.1.4 Steam Config

_**Very important to not turn on the machine until we check the steam switch wire positions**_

**NON-ECO VERSION**

Image of the steam switch schematic:

<img src="https://user-images.githubusercontent.com/53577819/154989457-f5ac859e-5aa5-4554-be46-fba6ad4fa1f0.png" width="600" height="450">

1. Move steam switch wire 4 to steam switch pole 1.
2. Unplug and secure steam switch wire 5.
3. Connect steam switch poles 4 and 5 to the Arduino nano as shown in **3.0.2 Component Wiring - 5. STEAM HANDLING WIRING**, using 26AWG wires.

**ECO VERSION**

Prepare a black splitter with below spec:

1. Black splitter, 15AWG, 5cm, two male ends and one female end


1. Disconnect the two top poles (1 & 4)
2. Use the splitter to bridge the connections you just removed and plug the female into pole 1
3. The connector with two white wires is not on the side of the orange wire (which is at the bottom) then make it so (to match schematics) - i.e move pole 5 connector into pole 2's location (should be two white wires going into the connector)
4. Leave the single white wire disconnected which was in pole 2's location
3. Connect steam switch poles 4 and 5 to the Arduino nano as shown in **3.0.2 Component Wiring - 5. STEAM HANDLING WIRING**, using 26AWG wires.

Image for reference below:

<img src="https://user-images.githubusercontent.com/53577819/155016949-a070e451-2bd8-45e8-9acb-669b7cc28bab.jpg" width="600" height="450">


### 2.1.5 Continuity Brew Detection

Prepare 2 cables with the below spec:
1. Green (not red or black), 26AWG, length from brew to Arduino, one exposed end, one female end 
2. Black, 26AWG, length from brew to Arduino, one exposed end, one female end

As shown below plug your cables in to the circled connections on the brew switch  

<img src="https://user-images.githubusercontent.com/53577819/154985120-fe503708-50c1-4376-9459-d72312fbbadc.jpeg" width="600" height="450">

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on GND and OUT connections to the Arduino.

## Extended Functionality

### 2.1.6 RobotDYN Dimmer Config
Prepare 3 cables with the below spec:
1. Red, 18/20AWG, 15cm, one exposed end, one female end 
2. Red, 18/20AWG, 15cm, one exposed end, one male end 
3. Black splitter, 18/20AWG, 15cm, one exposed end, one male end, one female end

Please check whether your dimmer ports placement in the case it differs from the images before connecting the dimmer, it's very important to feed the IN and OUT wires correctly!

Example of dimmer ports:

<img src="https://user-images.githubusercontent.com/53577819/154989499-7e95ca82-f8eb-4f63-b57b-3ca1e7e14eeb.png" width="600" height="450">

Remove the connections detailed in the image below from the pump (mark the connector either L or R for where it was located either left or right in relation to the pump):-

<img src="https://user-images.githubusercontent.com/53577819/154989519-4e5ba059-22a4-4397-8dfb-5b7dff411bbf.jpg" width="600" height="450">

With the cables you prepared:
* Cable 1: From the dimmer positive line Out - single red wire with the female end going into one of (choose the left connection according to the image above) the pump connections itself. 

* Cable 2: From the dimmer positive line In - single red wire with the male end going into the connector that was removed from the pump above (in this case it would be the left connector).

* Cable 3: From the dimmer neutral line In - with the black splitter with the male into the connector taken out of the pump (right connector) and female into the (right) remaining connection on the pump itself.

_**Triple check your dimmer board on what is marked as IN and OUT. 100% need to make sure they are connected properly.**_

<img src="https://user-images.githubusercontent.com/53577819/155005284-b22a6652-87b0-42db-9d35-5d2bc8b9247e.jpg" width="600" height="450">


<img src="https://user-images.githubusercontent.com/53577819/155005572-1d7c2ef1-ed1e-4c6e-9004-2fc22c73d83b.jpg" width="600" height="450">



_**Again!!! Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**_

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on VCC, GND, Z-C and PSM connections to the Arduino. 

### 2.1.7 Pressure Transducer Config
Installing the pressure transducer. The pressure sensor will be tapping into the orange braided hose connecting the pump outlet and the boiler inlet. I would generally advise to take out the original hose and use the one ordered together with the pressure sensor, cut a similarly sized one out of the hose purchased and use the rest of the left length as additional transducer buffer.

It's advisable after making the connections and just before connecting the transducer itself turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings (please be careful to do this outside the machine as water spill out...).

(INSERT IMAGES - of pressure transducer set up)

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on RED, BLACK andYELLOW wire connections to the Arduino. 

### 2.1.8 Load Cells Config
_**TO DO**_

### 2.1.9 Finish
***
If you haven't already, you're ready to connect everything to the Arduino. Use 3.0.2 Appendix for **Component Wiring** tables. 

One piece of advice would be to solder all cables to their respective boards as during the machine operation there is quite a bit of vibration which can introduce noise/frequent. This can lead to unexplained behaviours.

Any components sitting next to each other can have their equivalent pins linked with a cable.

You will be expected to solder similar pins i.e. GND and 5v together in order to fit into and screw down on the expansion board terminals.
***

On first start up record and send to #first-start channel of discord. This helps with diagnosing issues.

Remember to change and save your correct region settings.

Configure you PP and PI settings and get prepped for a shot if all is well. Record and upload to #first-shot on the discord. 

All going well, feel like an absolute coffee titan each and every time you pull a shot.

## 3.0 Appendix
### 3.0.1 Schematics & Diagrams
#### Schematics
[GAGGIA Classic Pro](https://github.com/Zer0-bit/gaggiuino/blob/release-0.2.2/schematics/gcp-schematics.png)

### Diagrams
[GAGGIA Classic Pro](https://github.com/Zer0-bit/gaggiuino/blob/release-0.2.2/schematics/GCP-CONNECTIONS-DIAGRAM.png)

### 3.0.2 Component Wiring 
You can find the defined pins at the top of the .ino file.

A suggestion on wiring; components that are inside same enclosure, the same connection can be linked i.e. solder a cable to the 5v pin then take the other end and solder to the 5V of the other component, from there take one cable to the Arduino. An alternative way is to  solder similar connections and apply heat-shrink before the exit to the machine then take one wire through the machine to the Arduino.

1. POWER DELIVERY RECOMMENDATION
Method 1 - If choosing to power the system using the AC adapter then the Arduino board and all the connected components will receive power by the means of the regulated 5v the AC adapter delivers through the USB port.

| PS | Arduino | 
| --- | --- |
| VCC OUT | 5v | 
| GND OUT | GND |

Method 2 - If powering using the [ 12v ] power supply module + [ 9v ] step-down convertor follow the bellow scheme:

| PS | Arduino | 
| --- | --- |
| 9v | VIN | 
| GND | GND |

All the other boards below will get their power from the Arduino 5v / GND pins and it's extremely important they are powered using those outputs.

2. MAX6675 WIRING

| MAX6675 | Arduino |
| ------- | ------- |
| VCC | 5v |
| GND | GND |
| SCK | D6 |
| SO  | D4 |
| CS  | D5 | 

3. RELAY WIRING 

| RELAY | ARDUINO |
| --- | --- |
| 4 | GND |
| 3 | D8 |

4. NEXTION WIRING

| NEXTION | ARDUINO |
| --- | --- |
|TX | RX |
|RX | TX |
|VCC | 5v |
|GND | GND |

5. STEAM HANDLING WIRING

4 & 5 are the switch points from 2.1.4 Steam Config

| GCP SWITCH | ARDUINO |
| --- | --- |
| 4 | D7 | 
| 5 | GND |

6. CONTINUITY WIRING

| BREW SWITCH | ARDUINO |
| --- | --- |
|TOP | GND |
|BOTTOM | A0 |

7. ROBOTDYN DIMMER WIRING

| DIMMER | ARDUINO |
| --- | --- |
| VCC | 5v |
| GND | GND |
| Z-C | D2 |
| PSM | D9 |

8. TRANSDUCER WIRING

| TRANSDUCER | ARDUINO |
| --- | --- |
| RED | 5v |
| BLACK | GND |
| YELLOW | A1 |

9. LOAD CELLS

TO DO

***


## Recommendations
### Soldering 
* Take your time soldering perfectly
* Use the "Western Union" splice to link wires (GND and 5v)
* Tin your wires to make them easier to solder.

<img src="https://user-images.githubusercontent.com/53577819/154989813-02169bfd-99c6-4695-a255-67f93cf57097.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154989830-7402a644-e4f8-489b-82db-735552c757df.jpg" width="600" height="450">

<img src="https://user-images.githubusercontent.com/53577819/154989847-822f76da-f33a-455e-95d1-ff173c4f1b8e.jpg" width="600" height="450">

### Resources
* GitHub: https://github.com/Zer0-bit/gaggiuino
* Discord: https://discord.com/channels/890339612441063494/890339612441063497
* Soldering 1: https://youtu.be/Fb7ONG08BUk
* Soldering 2: https://youtu.be/Fp37DPZVdRI
* Crimping : https://youtu.be/nvPESov0HbY
* Nextion : https://nextion.tech/faq-items/using-nextion-microsd/
