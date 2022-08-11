***
!> **Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project.**
***

### **SCHEMATICS & DIAGRAMS**

**Schematics:**
* [GAGGIA Classic](https://user-images.githubusercontent.com/42692077/161397293-82df427a-2ac2-4226-bdc6-fa831a962265.png)

**Diagrams:**
* [GAGGIA Classic](https://user-images.githubusercontent.com/42692077/160548957-88c93198-6d81-4081-8db6-552b6f6c5281.png)

***
!> **First and foremost, please do not underestimate the danger of electricity or overestimate your ability to work around it. Only start working on your machine while it's  completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or  your gold fish. It will be entirely your fault!**
***

### **ARDUINO CONNECTIONS**
***

1. MAX6675 (Temperature sensing)
    MAX6675  |  Arduino
    ---------|-----------
     VCC     |   5v
     GND     |   GND
     SCK     |   D6
     SO      |   D4
     CS      |   D5
***
2. Relay (Boiler power control)

    Relay Port  |  Arduino
    --------|-----------
      4     |   GND
      3     |   D8
      
   **Relay ports [1] and [2] are the high voltage circuit breaker**
***
3. Nextion LCD

    Nextion  |  Arduino
    ---------|-----------
      TX     |   RX
      RX     |   TX
      VCC    |   5v
      GND    |   GND

   ***Nextion and Arduino TX/RX are reversed intentionally***
***
4. Power delivery

    PS   |  Arduino
    -----|-----------
    5v   |   5v
    GND  |   GND

   ***Powering using the [ 12v ] power supply module + [ 5v ] stepdown convertor is the recommended way. Powering all the arduino connected boards through the Arduino's USB port is not recommended due to the low power capacity of the on-board voltage regulator. Doing so will kill your arduino eventually. You've been warned!***
*** 
5. Steam detection

   ![GC - steam handling](https://user-images.githubusercontent.com/42692077/147904917-feeb3230-3ea0-460c-82de-4ad16034a48e.png)

    GC SWITCH | Arduino
   -----------|-----------
   3          |   D7
   4          |   GND
***
6. Brew detection

   OPTOCOUPLER |  Arduino
   ------------|-----------
    VCC        |   5v
    GND        |   GND
    OUT        |   A0
   
  _The high voltage circuit control ports will splice into existing brew switch wires._
***
7. Pressure sensing

    Transducer|  Arduino
    ----------|-----------
     RED      |   5v
     BLACK    |   GND
     YELLOW   |   A1
***
8. Dimmer (pressure control)

    Dimmer  |  Arduino
    --------|-----------
    VCC     |   5v
    GND     |   GND
    Z-C     |   D2
    PSM     |   D9
  
_Dimmer high voltage circuit control ports will act as a passthrough for the pump LIVE and NEUTRAL wires_
   
***

### **ASSEMBLING**
First let's check that the setup works as expected while outside the machine so you don't have it all installed and realise just afterwards it's not reading any temperature because of a faulty component or the relay doesn't switch between the ON/OFF modes.

!>**Note 1 - No permanent connections are needed during testing, so no soldering needed for now.**
>
!>**Note 2 - All LV(low voltage) sides of the boards will connect to a single 5V and GND rail on the Arduino.**
>
!>**Note 3 - DO NOT FEED POWER TO ALL THE BOARDS THROUGH THE MCU USB PORT.**
>
!>**Note 4 - This page is a general guide, not an exhaustive, step-by-step tutorial. It is expected that anyone attempting has proficiency with the skills listed in the Recommendations page of this site.**

**ATTENTION !!!**

**As always with such projects common sense should be applied at all times, it's expected people doing such sort of modifications will have some basic understanding.**

!> **Triple check your machine is disconnected from any power sources, even better just pull the power cable out of it if you haven't done so yet!**

#### *BASE FUNCTIONALITY BENCH TEST*
***
1. The first step will be to test the electronics outside the Gaggia. Connect the MAX6675 module, relay, and nextion to the arduino board using the pins defined above. You can also find them defined at the top of the .ino file.
For now only connect the low voltage circuit controlling ports of the relay to check whether the relay LED indicates the power states.

4. Plug the arduino board in using the mini USB cable that came with it and upload the code to the arduino board, using your chosen IDE (Arduino or VSCode with PlatformIO).
    >*Note: uploading won't work with the LCD connected*

5. Upload the LCD ROM code to the Nextion.

    **Method 1** 

        Just copy the *.tft file on a FAT32 formatted microSD card and upload onthe LCD panel using the onboard card reader

    **Method2** 

        Open the .HMI file using Nextion Editor and using the File menu upload it on a microSD card
     >*Note: card needs to be FAT32 formatted*

6. After the upload is finished get the card out and power cycle the LCD.
7. You should see temp readings on your screen if everything went according to plan.
    >*Don't forget to test the thermocouple/relay combo operation, apply some heat to the thermocouple end and see whether the relay led operates in HIGH/LOW modes*

**At this point if all the above works as expected, then you're ready to install it all inside the machine. We'll be preparing some splitters that we'll use to connect to the Gaggia internals without introducing any permanent modifications so in the event of a desire to revert to stock it's a few disconnects away!**

#### *BASE FUNCTIONALITY*
***
1. Take off the top cover by unscrewing the 2 top screws. You should be able to see something similar to the below image minus the SSR relay:
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m4pob4r1pDtjBPqIyA-dqHOH_eZDJaf6W2dYdHlIh8G8OWusXig9WUKOA-iBCk2QRN-lL3ajrWDDUBASx_frpWqz_2z1dxeAnksAKKysKqL-eXE9PVRYeA2SdmS_DSkAA3TJ5ZVe3ybpkLYV0-PDKLjEhxNZluA_UX8ektw8kGW4PXKQeQU-UUJtjuaDSYKsG?width=3496&height=4656&cropmode=none" width="769" height="1024" />
</div>

2. Prepare 2 splitters like in the below image using the AWG15 cable, be sure one splitter to be black(negative) and one red(positive)
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4mGdTrz4hXNuu3rvDk5qro2WGn5xqy8ZVGwhJSXFSDqmJErI8dYufS1H-l_PnIIa0HffKXPuPkvbRjNHt_2OogxaW8UohuFKatz3BfjjK8NEGmynX2unmeZ6opV3_gd-u0f3cCAlgh9nF5spGDt12McFxpxzsatrSK2YuRgrFTfFnxMvMmiXss0XSLrZGx5xIa?width=769&height=1024&cropmode=none" width="769" height="1024" />
</div>

3. Be sure to mark your top left power connector so you don't mix them up. If you want to be sure, you can number all the connectors with a sharpie, to make for easier reconnections later down the road.
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4mM3HVfjbCIdcPtx16eN0pEgGC4Z0ih04agqfBwI-NLtpUWvmlBFI23fT2LPVagGHXYsgRiIVq8oSjJckuZscCcdTKqq7GNxCK5GxRqsp2pCZinopGHCdqJtnZqMCFBlSq-yOT-vNtsATxE734AN05DO47i1as2NSW4E-87r78gV7kpP_sy9tHiBqey26s9xP0?width=769&height=1024&cropmode=none" width="769" height="1024" />
</div>

4. Disconnect all 3 of the power switch connectors. You'll use the middle and bottom ones for power sharing.
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m9fZvq6wrObA7QFSkvQpfFyOinQbfs-u_E8DLZqp784cPLcUIlZKoZeqbLWn3JPAElseiwa0G1KuN-yXJfOx_4N-3k-IU0YprmK-YHBYEG-33CaUXTEWVPNVwjy6y7kMyaDvbEzH445Su6hSKNqZqAPXmwJQlIH8lAQmXaTduAk3WIsUrZSw2J0lPhRRVEqzX?width=769&height=1024&cropmode=none" width="769" height="1024" />
</div>

5. The hardest part will be now (in my opinion). You'll have to unscrew the bottom boiler stock thermostat and screw back in the new thermocouple. You may have to unscrew and move the boiler in order to do so. Be sure to apply some thermal paste on the thermocouple threads. (Just a teeny tiny bit). It is important to barely tighten the m4 bolt at **barely** fingertip strength.
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m9lHvLCobQ3DlmTfqYPJvV1M-z2T0_GMxgeE21-hqP3nfu5UwB1PTyPF6rIT5A6ebeyv9TXwEfCbB1SBwkyVy0r8AIbrLGogaWcebzjSpaskThwbn-S45n5E-IAkeKPJgYAjLMPYeQPjALL--D1CC60ZFaOGsaHtAOSNvcb1Y4X2IEWV7n4bUP4v40sKawusJ?width=496&height=660&cropmode=none" width="768" height="1024" />
</div>

6. Prepare 2 cables you'll use to connect the cables disconnected from the bottom thermostat to ports 1 and 2 of the SSR relay. Use the red cable for that. They shouldn't be too long, about 10cm will suffice. One end should be crimpled with a male spade connector and the loose end screwed to the relay. After this, attach the relay to the machine case itself with an M4 screw and nut, though smaller will work. Be sure to apply some thermal paste to the SSR backplate that will make contact with the metal case of the machine.
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m3ZmhHEobr2VPen1wScEO8AMLiaOVfWjsnW8Aw4645PaRXerrLpV8iZmZjzU88KDPmKEfPXbUBqYhn6ejVOfXIB7hgucmljyOLL54tqWKUahFoqnYEf2rBh0TRXjFEtzAvptdT3W8nSTzc96sfvD8hcK-pQEeEaYaLaq4gpNaKyXdWQtETpPtrzpMd1mLzuyb?width=2584&height=2140&cropmode=none" width="769" height="769" /> 
</div>

So you end up having them connected like this:
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m5HfjPvkFSOtSm8gkTJJ4saqEw8dcB1no2eoaHcDZjYD9OV95tBnrG8tqtRuOcor7aFZrIRw7167k4QGMUneOPATitBFctkgdklxWOohMyBir3zLdm9fkAnTQW8TquTZouRh9rzKSC0t5bkerK1g8AzlFYTfuZoDPQ3juFiOJ19JKiL6VpODn40Z1q8JwVpGy?width=2625&height=2831&cropmode=none" width="769" height="769" />
</div>

7. Prepare 2 more 10cm cables (also colour coded accordingly) which should be crimpled with M/F spade connectors at each end, the female end will go in Gaggia's front panel and the male end will go to the female end of the previously prepared (2) splitters, as in the below image:
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4m2LoENSwBicOmRtvdMKM9srnf4tfNECBkaNXWkkGxxEAMbc_BuQhQnYgVH7h0FZ52NIDiIudlx2NhDkm1747Y9wT60F7uoHMJu-lx_MF-mPXBbzOyeZNVuEdrISfsi56v7VYKNZIgby3qUD922gMJCI177q0IttLhWXn_VM9OamG0FvyKQ3T26uqOye6H50eV?width=769&height=1024&cropmode=none" width="769" height="1024" />
<img src="https://db3pap006files.storage.live.com/y4myMKUSADo1HIGEXQ42p9tP1UKzL2aUqI6gCv3st6cBqR921Y-xWkhHB9QYaUlubJC-wCs5swyMaXX-p9LJu0qDgOgMKwkMyW-KUdUkkQWZ7-VdJNZiWv2duaBEcFtGo34uX1_-mqF66PpgseniGFKGhJmO-o5n8Pb2TP2it0vyQBcLAgX00jzVl-H6L5NeVzE?width=769&height=1024&cropmode=none" width="769" height="1024" />
</div>

8. Connect the front panel cables to any of the free male ends of the splitters, black one for the negative cable and red for the positive one (on my machine the positive has 2 cables crimped together).

9. To power the Arduino system I have used an old 5v mobile charger which I'm sure all of us have laying around. Just solder 2 cables to the 2 ends of the charger and for the other ends use 2 F spade connectors, after which plug them to the remaining 2 splitter (2) ends.
<div align="center">
<img src="https://db3pap006files.storage.live.com/y4myMKUSADo1HIGEXQ42p9tP1UKzL2aUqI6gCv3st6cBqR921Y-xWkhHB9QYaUlubJC-wCs5swyMaXX-p9LJu0qDgOgMKwkMyW-KUdUkkQWZ7-VdJNZiWv2duaBEcFtGo34uX1_-mqF66PpgseniGFKGhJmO-o5n8Pb2TP2it0vyQBcLAgX00jzVl-H6L5NeVzE?width=769&height=1024&cropmode=none" width="769" height="1024" />
</div>

10. Next, you'll be setting up steam switch detection. First, disconnect all the steam switch high voltage wires

![GC - brew handling](https://user-images.githubusercontent.com/42692077/154805193-76068521-3ad4-4020-b2ee-8dab9394d4fe.png)

11. Bridge the wires connected to the steam switch poles 1 and 2.

12. Bridge the steam thermostat wires. The steam thermostat is on the top of the boiler.

13. Connect steam switch poles 3 and 4 to the arduino nano as listed above using some AWG26 wires.

14. Make sure you secure all the disconnected wires so they cannot make any accidental contact.

15. Now you're ready to connect the rest of the electronics to the Arduino like you did when testing everything. This time, it is recommended to solder all the Arduino connected cables, instead of using the provided dupont connectors, as during the machine operation there is quite a bit of vibration. This can introduce all sorts of noise/frequent disconnects to certain pins which will lead to unexpected behaviour.

#### *EXTENDED FUNCTIONALITY*
***
1. Install the Optocoupler, which will detect when the brew switch is flipped.

**Gaggia Classic(pre 2018) ONLY**

  * Prepare two **"Y"** splitters **BLACK** and **RED** with the ends crimped as follows: 
     * **RED SPLITTER:** 1 x **MALE**, 1 x **FEMALE**, 1 x **BARE**.
     * **BLACK SPLITTER:** 1 x **MALE**, 1 x **FEMALE**, 1 x **BARE**.
  * Connect the wire connected to **STEAM** button pole **4** to BREW button pole **5**. The original disconnected **BREW** pole **5** wire should be left disconnected but properly secured.
  * Connect the RED **"Y"** splitter to **BREW** switch pole **6** and plug the original connected wire to the **MALE** spade end, the **BARE** splitter end going to the optocoupler **L** terminal. 
  * Tap into the **PSU** splitter used for the **N** connection using the **BLACK** splitter and connect the bare end to the optocoupler **N**
***
2. Install the pressure transducer.
  The pressure sensor will be tapping into the hose connecting the **pump outlet** and the **boiler inlet**. How you connect it is up to you.

***It's advisable after making the connections and just before connecting the transducer itself turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings. After the transducer is connected, be sure to test the fittings under pressure.***
  
  ![New Project (11) (1)](https://user-images.githubusercontent.com/42692077/146647799-f4887edb-95ec-4a33-8561-4e4afda6256e.png)
  

3. Install the RobotDYN dimmer module.

![dimmer_guide](https://user-images.githubusercontent.com/42692077/162638303-dd1333b0-212f-41b5-be64-de8543dc1153.png)
  
![dimmer-install-info](https://user-images.githubusercontent.com/42692077/147135452-fb3931c5-ac48-4a61-91ff-1b4275aaccb2.png)
</div>

>**The image above is provided as a reference to understand how the connection through the dimmer is made, please check whether your dimmer high voltage ports placement differs from the above image before connecting the dimmer, it's very important to feed the IN wires properly.**
