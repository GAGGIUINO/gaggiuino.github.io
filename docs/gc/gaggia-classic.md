***
!> **Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project.**
***

### **SCHEMATICS & DIAGRAMS**

**Schematics:**
* [GAGGIA Classic **Nano** HV wiring](https://user-images.githubusercontent.com/42692077/161397293-82df427a-2ac2-4226-bdc6-fa831a962265.png)
* [GAGGIA Classic **STM32-Blackpill** HV wiring](https://user-images.githubusercontent.com/109426580/202476409-f76be79d-b51c-4130-adc1-d494a65e6114.jpeg)


**Diagrams:**
* [GAGGIA Classic **Nano** LV wiring](https://user-images.githubusercontent.com/42692077/160548957-88c93198-6d81-4081-8db6-552b6f6c5281.png)
* [GAGGIA Classic **STM32-Blackpill** LV wiring](https://user-images.githubusercontent.com/109426580/202657197-430f272b-d3cd-4502-926b-75b32c482dac.jpg)

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

   ***Relay ports [1] and [2] are the high voltage circuit breaker so not mentioned here as they get covered further in the guide.***
***
3. Nextion LCD

    Nextion  |  Arduino
    ---------|-----------
      TX     |   RX
      RX     |   TX
      VCC    |   5v
      GND    |   GND

   ***Nextion and Arduino TX/RX are reversed intentionally.***
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
!>**Note 4 - As always with such projects common sense should be applied at all times, it's expected people doing such sort of modifications will have some basic understanding.**
>
!> **Triple check your machine is disconnected from any power sources, even better just pull the power cable out of it if you haven't done so yet!**

#### *BASE FUNCTIONALITY BENCH TEST*
***
1. The first step will be to test the electronics outside the Gaggia. Connect the MAX6675 module, relay, and nextion to the arduino board using the pins defined above. You can also find them defined at the top of the .ino file.
For now only connect the low voltage circuit controlling ports of the relay to check whether the relay LED indicates the power states.

4. To flash the microcontroller Arduino Nano or the STM32 Blackpill, pls follow the video form the ***Prerequisites*** section of this site.

!> Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.

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
![PXL_20210527_181116200 1](https://user-images.githubusercontent.com/109426580/190676716-bf126fbc-2177-43d0-8300-3525e7daac8c.jpg)

2. Prepare 2 splitters like in the below image using the AWG15 cable, be sure one splitter to be black(negative) and one red(positive)
![PXL_20210527_183052740 1](https://user-images.githubusercontent.com/109426580/190676830-420e5ff8-d29b-4221-8c71-41de8c92c52a.jpg)

3. Be sure to mark your top left power connector so you don't mix them up. If you want to be sure, you can number all the connectors with a sharpie, to make for easier reconnections later down the road.
![PXL_20210527_181404819 1](https://user-images.githubusercontent.com/109426580/190676906-c9d34b70-ef66-4de1-a28d-7761502ebac8.jpg)

4. Disconnect all 3 of the power switch connectors. You'll use the middle and bottom ones for power sharing.
![PXL_20210527_181526240 1](https://user-images.githubusercontent.com/109426580/190677058-ee7538a3-82c5-4f3a-83a8-6897610f46db.jpg)

5. The hardest part will be now (in my opinion). You'll have to unscrew the bottom boiler stock thermostat and screw back in the new thermocouple. You may have to unscrew and move the boiler in order to do so. Be sure to apply some thermal paste on the thermocouple threads. (Just a teeny tiny bit). It is important to barely tighten the m4 bolt at **barely** fingertip strength.
![PXL_20210527_181116200 1](https://user-images.githubusercontent.com/109426580/190677178-fb9fdefc-731c-4a09-87b7-a5bfdf37f50b.png)


6. Prepare 2 cables you'll use to connect the cables disconnected from the bottom thermostat to ports 1 and 2 of the SSR relay. Use the red cable for that. They shouldn't be too long, about 10cm will suffice. One end should be crimped with a male spade connector and the loose end screwed to the relay. After this, attach the relay to the machine case itself with an M4 screw and nut, though smaller will work. Be sure to apply some thermal paste to the SSR backplate that will make contact with the metal case of the machine, not critical in any way of form but will provide better heat transfer if ever the needs is there.
![PXL_20210527_184425223_c](https://user-images.githubusercontent.com/109426580/190677929-aef4ced7-c3d8-4a1f-bf3e-c5d0e2af5a7c.jpg)

So you end up having them connected like this:
![PXL_20210527_181116200c (1)](https://user-images.githubusercontent.com/109426580/190678041-1c3b3d7f-d9b1-4289-aea2-f5623d323170.png)


7. Connect the front panel cables to any of the free male ends of the splitters, black one for the neutral wire (N) and red for the line wire (L).
![PXL_20210527_183052740 2](https://user-images.githubusercontent.com/109426580/190678786-d67b8034-f37e-41ed-a713-bbf2d4a2efb4.jpg)


8. To power the Arduino system I have used an old 5v mobile charger which I'm sure all of us have laying around. Just solder 2 cables to the 2 ends of the charger and for the other ends use 2 F spade connectors, after which plug them to the remaining 2 splitter (2) ends.
![PXL_20210527_183052740 2](https://user-images.githubusercontent.com/109426580/190678786-d67b8034-f37e-41ed-a713-bbf2d4a2efb4.jpg)

10. Next, you'll be setting up steam switch detection. First, disconnect the steam switch high voltage wires connected to poles 3 and 4.
![GC - brew handling](https://user-images.githubusercontent.com/42692077/154805193-76068521-3ad4-4020-b2ee-8dab9394d4fe.png)

11. Leave the wires connected to the steam switch poles 1 and 2 connected.

12. Bridge the steam thermostat wires. The steam thermostat is on the top of the boiler.
![image](https://user-images.githubusercontent.com/109426580/190679925-4bfb1574-1af0-414f-b38c-18a5d8c6f8c2.png)


13. Connect steam switch poles 3 and 4 to the arduino nano as listed above using some AWG26 wires.
![image](https://user-images.githubusercontent.com/109426580/190680352-503d1a21-676c-4ec2-95dc-9a12ee5161ac.png)

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
  The pressure sensor will be tapping into the PTFE tube connecting the **pump outlet** and the **boiler inlet**. How you connect it is up to you.
  
When installing the T-fitting:
  * Do not use diagonal cutters or pliers to cut the tube. These cutters pinch the tube out of round which can cause sealing problems. Use a very sharp razor blade or scalpel with a slow sawing motion to make a clean cut. To seal well in the T-fitting the cut hose ends must be smooth and square to the tube.
  * Try to install the T-fitting along a straighter section of the tube. If the tube bends sharply immediatley after exiting the T-fitting it may not seal.
  * If you see large scratches on the outside of your hose try to place the splice for the tee away from the scratches. The O-rings in the fitting may not seal well on scratched sections of tube. 

  When installing the transducer:
  * Connect the entire 1m length of PU tubing to the T-fitting and bundle it up inside the machine with a zip tie. Leaving this tube long helps smooth out the pressure transducer readings.
  * To get the transducer to seal to the brass push-to-connect fitting, wrap the threads in PTFE tape and place a dash 011 or similarly sized O-ring at the bottom of the brass push-to-connect fitting.
  * Place the transducer as low as possible in the case and far away from the boiler. Ensure the transducer is resting so that the push-to-connect fitting is pointing upwards or the transducer is sitting perpendicular to gravity to avoid noisy transducer readings.

***Its advisable after making the connections and just before connecting the transducer itself turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings. After the transducer is connected, be sure to test the fittings under pressure.***
  
  ![New Project (11) (1)](https://user-images.githubusercontent.com/42692077/146647799-f4887edb-95ec-4a33-8561-4e4afda6256e.png)
  

3. Install the RobotDYN dimmer module.

![dimmer_guide](https://user-images.githubusercontent.com/42692077/162638303-dd1333b0-212f-41b5-be64-de8543dc1153.png)
  
![dimmer-install-info](https://user-images.githubusercontent.com/42692077/147135452-fb3931c5-ac48-4a61-91ff-1b4275aaccb2.png)
</div>

>**The image above is provided as a reference to understand how the connection through the dimmer is made, please check whether your dimmer high voltage ports placement differs from the above image before connecting the dimmer, it's very important to feed the IN wires properly.**
