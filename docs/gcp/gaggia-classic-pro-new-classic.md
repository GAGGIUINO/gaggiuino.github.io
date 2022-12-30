***
!> **Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project.**
***

## **1.0.0 TEST INSTALL**
We are not installing inside the machine yet and we are doing minimal soldering at this point. We just want to test as much as we can to make sure we've not got any duds from a base functionality point of view.

We need to understand what goes where. The schematics in (**3.0.1 Schematics & Diagrams**) aren't really rocket science but for someone who's never disassembled or has no experience working with electrical circuits it might get confusing really fast. 

Note 1 - No permanent connections are needed during testing so no soldering needed for now.
Note 2 - The 5v/GND Arduino board pins will be shared between all the connected devices.

### *1.0.1 Arduino Config* 
Place Arduino into the expansion board the correct way round. Power it through USB adapter for now during the testing phase.

Image of Arduino with pins soldered:

![image](https://user-images.githubusercontent.com/53577819/154988207-3d54e924-3ab0-4e47-a4e9-188f7e839610.jpg ':size=500')

Image of expansion with pins (solder from the bottom):

![image](https://user-images.githubusercontent.com/53577819/154988218-26160147-e821-47e7-8152-d8ec0a8f0d43.png ':size=500')

Make sure the terminals are correct way round and place the Arduino into the expansion board.

If you have to solder your pins then take the time now to get your soldering perfect. It'll save time in the long run. REFER TO APPENDIX *3.0.3 Recommendations* FOR SOLDERING GUIDES!

![image](https://user-images.githubusercontent.com/53577819/154988330-430df58d-773c-4084-b7b3-921ca43909f2.jpg ':size=500')

_**Attention! You are not soldering the Arduino to the expansion board itself. You are only soldering the pins to the Arduino and pins to the expansion board. The Arduino then just sits/connects into the expansion board pins.**_

### *1.0.2 MAX6675 Config*
***
For the below section you are using **26AWG** cable to connect to the Arduino board.
 
**Refer to the appendix 3.2 for component wiring.**
***

You should have bought and received a MAX6675 board which comes with a test thermocouple. We're swapping this for the "C-M4 screw K-Type thermocouple sensor" as this is what will be replacing the original that's in the machine.
 
![image](https://user-images.githubusercontent.com/53577819/154988392-619a5bc2-99cc-499d-8ad8-42792b094fd2.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154988423-f741a369-ec60-4266-9544-0effedb57292.jpg ':size=500')

### *1.0.3 Nextion Config*
***
For the below section you are using **26AWG** cable to connect to the Arduino board. 
 
**Refer to the appendix 3.2 for component wiring.**
***

The correct screen size is **2.4**". If yours does not have markings for wiring then please see below image

![image](https://user-images.githubusercontent.com/53577819/154988491-28c1e861-46bc-433b-a5f8-8e9eeb8b51ed.png ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154988514-13a1d7af-f704-49b6-975b-aeee1318cf36.jpg ':size=500')

### *1.0.4 Relay Config*
***
For the below section you are using **26AWG** cable to connect to the Arduino board. 
 
**Refer to the appendix 3.2 for component wiring.**
***

This relay is what manages the temp by cutting the voltage when the thermocouple is at a set temp. 

![image](https://user-images.githubusercontent.com/53577819/154988554-5be0bb0a-dcf2-4bf7-a70f-4c356d00eea6.jpg ':size=500')

### *1.0.5 Software Install*
To flash the microcontroller Arduino Nano or the STM32 Blackpill, pls follow the video form the ***Prerequisites*** section of this site.

!> Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.

**Flashing the Nextion LCD Software Upload**

_Uploading the LCD ROM code_

**Method** 1 - Download and unzip the *.tft file on a FAT32(MS-DOS (FAT32)) formatted microSD card and upload on the LCD panel using the onboard card reader.

**Method 2** - Open the .HMI file using Nextion Editor and using the File menu upload it on a microSD card

1. Plug LCD back into Arduino Board Setup
2. Locate “nextion-discovery-lcd.tft” or “nextion-basic-lcd.tft” (depends on what you purchased)
3. Copy the file to a FAT32 formatted MicroSD card
* If on Mac for some reason it adds a second file beginning with a "." use terminal to change directory to the microSD and use "rm ._nextion-*YOUR-VERSION*-lcd.tft" to remove that file.
4. Place MicroSD card inside the Nextion display
5. Power on the Arduino Board Setup and installation should occur automatically
6. Once “successed” reboot the Arduino

### *1.0.6 Test*

You should now see the Gaggiuino project on the LCD. If your connections are all right (and well secured), you should see a temperature reading from the thermocouple (temp reading will contain the default offset of 7 which means the initial temp will be - room temp -7)

Try applying heat with your hand and you should see the temperature respond (if not, I recommend confirming all connections are correct and adequately tightened.  Mine did not respond at first and turned out one of the connections to the Arduino board was not tight enough)

If everything looks good, move on to Installing into the Gaggia Classic Pro

_**If all the above works as expected you're ready to install it inside the machine.**_

## **2.0.0 INSTALL**
***

!> **Do not underestimate the danger of electricity or overestimate your ability to work around it. Only start working on your machine while it's completely disconnected from the mains power socket, also by agreeing to follow the below guide I cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, friend or goldfish and it will be entirely your fault!**

***

Undo everything as we will now install into the machine. 

All components except the Arduino and LCD will be internal to the machine. Remember this when wiring the LCD. 
For each of the components we want to start guesstimating on cable length. You can do this by placing components where you want to place them. Close together components can share similar wiring i.e. 5v and GND.

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on pin connections to the Arduino. 

**Base Functionality**
### *2.0.1 Power Delivery*
Take off the top cover of your machine by unscrewing the 2 top screws. Be sure to mark your top left power connector so you don't mix them up (even though it's not that hard to understand which one is which).

Prepare splitter cables with the below specs:
1. Black splitter, 18AWG, 10cm, female end, male end, male end
2. Red splitter, 18AWG, 10cm, female end, male end, male end

Example of a red and black splitter:

![image](https://user-images.githubusercontent.com/53577819/154988645-5f1da175-7d09-437a-ac2c-f64e16f3a564.jpg ':size=500')

The female end will go in Gaggia's front panel. One male splitter end will go into the connection that came out of the switch position the other male will be for some more wires further down.


![image](https://user-images.githubusercontent.com/53577819/154988784-7ddbc106-4744-4d9f-8879-b9a107a9fe7c.jpg ':size=500')


**Before trying to copy piggyback locations from below it’s recommended to check what the schematics say (3.0.1 Schematics & Diagrams).** 


By way of context, if looking inside the machine from the back, the left of the power switch is the brew switch. 
On the power switch - wire in the middle left as LIVE and middle right as GND 


![image](https://user-images.githubusercontent.com/53577819/154979422-f78d41c4-87f4-4474-ab68-a3466d5e9e5e.jpeg ':size=500')

The above translates to the following (**please be aware the image below has top connectors removed for clarity)**:

![image](https://user-images.githubusercontent.com/53577819/154979529-eae513b2-00e3-40c9-a581-47be4da68edc.jpg ':size=500')



If above standard schematics do not work it can be that your wiring is different. It is recommended to use a multimeter to test. 

![image](https://user-images.githubusercontent.com/53577819/154982423-82b4bdb4-ca78-4077-90c0-77b349c8c3d2.JPG ':size=500')



* Set it to 600V~ (AC) as shown above and test the connectors on the switches
* Just wiggle the connector on the switch out a touch to expose a tiny bit of metal where you put your lead on
* Use schematic to find a GND point
* Your live piggyback will show no voltage until the machine is switched on

As stated you want to find the connector that only shows voltage after flipping the machine machine on. 

If your LCD is on even though you've not flipped the machine switch on, this means you've piggybacked into the mains live which is constantly got voltage - this is not correct!



Please see some examples of known differences but really you should be testing with a multimeter.

**KNOWN - ECO - EU/UK - piggyback locations non-schematic:**

![image](https://user-images.githubusercontent.com/53577819/154988901-b79270da-5bb3-4507-9ef2-57bf2e791d77.JPG ':size=500')


Prepare 2 more cables with the below spec:
1. Black, 18AWG, about 15cm, female end, exposed end
2. Red, 18AWG, about 15cm, female end, exposed end

Connect the female end to the male end of the splitter cable from above step (match the colours)

If using the 5v PS - the 2 AC IN ports will be where the exposed end of your red or black piggyback cable go, it doesn't matter which way round (yes, you need to fiddle about getting wires in and solder correctly - recommended to trim, twist, tin and apply heat shrink).

![image](https://user-images.githubusercontent.com/53577819/154989029-59ab20c6-fdda-4510-a9e0-50579b8e4a54.jpg ':size=500')

Prepare more cables with the below spec:
1. Black, 26AWG, about 25cm, exposed ends
2. Red, 26AWG, about 25cm, exposed ends

In relation to the image above - the black will be connected to the GND and the red to the VCC the other ends are going to the Arduino. Please use the tables in **3.0.2 Appendix - Component Wiring** for details on wiring VCC and GND connections to the Arduino. 

_**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on! **_

**_If you have the ECO version (the machine turns off automatically after 20mins) bridge your brew switch with a 18AWG cable with two male ends, as per below:_**

![image](https://user-images.githubusercontent.com/53577819/154989122-6237e1af-62d1-4289-901c-47c69ea3b1b9.jpg ':size=500')

### *2.0.2 Thermocouple and MAX6675 Config* 

Prepare the following cable to the below spec:

1. Black, 18AWG, 5cm, two male ends

[Detach the boiler](https://www.youtube.com/watch?v=0ipvBdWaVzQ) (only watch as far as the 5min mark) to gain enough access to remove the thermocouple and replace it with the m4 bolted thermocouple sensor. 

You’ll obviously need to remove the two connectors from the original thermostat first - which is located at the bottom of the boiler on the side closest to the power on switch.  

The small black cable you prepared with the male ends is used to bridge the two wires that you just disconnected from the brew thermostat. 


![image](https://user-images.githubusercontent.com/53577819/154983715-46b1332f-f88a-4ef3-a625-b7f2788caf97.jpeg ':size=500')


Now unscrew the original thermostat and replace with the m4 brass thermocouple. Be sure to apply some thermal paste (just a teeny tiny bit) on the _**threads only**_. It is important to barely tighten the m4 bolt at **barely** fingertip strength. 

![image](https://user-images.githubusercontent.com/53577819/154989188-6bc38c2c-60df-47f6-98d9-b121f28438d6.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154989228-2f9a3669-551b-4f45-a82a-22b4fe41fa89.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154984016-714b6532-e31d-42d3-b2ee-cf064487db66.jpeg ':size=500')


Now re-attach the boiler.
Check the appendix section **## 3.0.2 Component Wiring  2. MAX6675 WIRING**

_**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**_

### *2.0.3 Relay Config* 

Prepare cables with below spec:

1. Red, 18AWG, 10cm, one male end, one exposed end
2. Red, 18AWG, 10cm, one male end, one exposed end

The 2 are used to connect the steam thermostat connections to port 1 and 2 of the SSR relay, so:

![image](https://user-images.githubusercontent.com/53577819/154989308-14e9ea82-8a60-4f3d-bd9f-05dda6fa15c8.JPG ':size=500')


Optional: might be a good idea to either tape up the exposed steam thermostat or remove it and tape up the exposed location.


![image](https://user-images.githubusercontent.com/53577819/154989373-57093be0-ac48-4ac6-ad0b-d88adc2415d9.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154989357-ec8c4853-0bb9-4eec-8629-dfc76e72e725.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154989336-76f91fb5-2fdd-4c53-b968-e860af3f8505.jpg ':size=500')

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on 3 & 4 connections to the Arduino. 

### *2.0.4 Steam Config*

_**Very important to not turn on the machine until we check the steam switch wire positions**_

**NON-ECO VERSION**

Image of the steam switch schematic:

![image](https://user-images.githubusercontent.com/53577819/154989457-f5ac859e-5aa5-4554-be46-fba6ad4fa1f0.png ':size=500')

1. Move steam switch wire 4 to steam switch pole 1.
2. Unplug and secure steam switch wire 5.
3. Connect steam switch poles 4 and 5 to the Arduino nano as shown in **3.0.2 Component Wiring - 5. STEAM HANDLING WIRING**, using 26AWG wires.

**ECO VERSION**

Prepare a black splitter with below spec:

1. Black splitter, 18AWG, 5cm, two male ends and one female end


1. Disconnect the two top poles (1 & 4)
2. Use the splitter to bridge the connections you just removed and plug the female into pole 1
3. The connector with two white wires is not on the side of the orange wire (which is at the bottom) then make it so (to match schematics) - i.e move pole 5 connector into pole 2's location (should be two white wires going into the connector)
4. Leave the single white wire disconnected which was in pole 2's location
3. Connect steam switch poles 4 and 5 to the Arduino nano as shown in **3.0.2 Component Wiring - 5. STEAM HANDLING WIRING**, using 26AWG wires.

Image for reference below:

![image](https://user-images.githubusercontent.com/53577819/155016949-a070e451-2bd8-45e8-9acb-669b7cc28bab.jpg ':size=500')


### *2.0.5 Continuity Brew Detection*

Prepare 2 cables with the below spec:
1. Green (not red or black), 26AWG, length from brew to Arduino, one exposed end, one female end 
2. Black, 26AWG, length from brew to Arduino, one exposed end, one female end

As shown below plug your cables in to the circled connections on the brew switch  

![image](https://user-images.githubusercontent.com/53577819/154985120-fe503708-50c1-4376-9459-d72312fbbadc.jpeg ':size=500')

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on GND and OUT connections to the Arduino.

**Extended Functionality**

### *2.0.6 RobotDYN Dimmer Config*
Prepare 3 cables with the below spec:
1. Red, 18AWG, 15cm, one exposed end, one female end 
2. Red, 18AWG, 15cm, one exposed end, one male end 
3. Black splitter, 18AWG, 15cm, one exposed end, one male end, one female end

Please check whether your dimmer ports placement in the case it differs from the images before connecting the dimmer, it's very important to feed the IN and OUT wires correctly!

Example of dimmer ports:

![image](https://user-images.githubusercontent.com/53577819/154989499-7e95ca82-f8eb-4f63-b57b-3ca1e7e14eeb.png ':size=500')

Remove the connections detailed in the image below from the pump (mark the connector either L or R for where it was located either left or right in relation to the pump):-

![image](https://user-images.githubusercontent.com/53577819/154989519-4e5ba059-22a4-4397-8dfb-5b7dff411bbf.jpg ':size=500')

With the cables you prepared:
* Cable 1: From the dimmer positive line Out - single red wire with the female end going into one of (choose the left connection according to the image above) the pump connections itself. 

* Cable 2: From the dimmer positive line In - single red wire with the male end going into the connector that was removed from the pump above (in this case it would be the left connector).

* Cable 3: From the dimmer neutral line In - with the black splitter with the male into the connector taken out of the pump (right connector) and female into the (right) remaining connection on the pump itself.

_**Triple check your dimmer board on what is marked as IN and OUT. 100% need to make sure they are connected properly.**_

![image](https://user-images.githubusercontent.com/53577819/155005284-b22a6652-87b0-42db-9d35-5d2bc8b9247e.jpg ':size=500')


![image](https://user-images.githubusercontent.com/53577819/155005572-1d7c2ef1-ed1e-4c6e-9004-2fc22c73d83b.jpg ':size=500')



_**Again!!! Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**_

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on VCC, GND, Z-C and PSM connections to the Arduino. 

### *2.0.7 Pressure Transducer Config*
Installing the pressure transducer. T

The pressure sensor will be tapping into the orange braided hose connecting the pump outlet and the boiler inlet. 

**There is no need to take off your original saeco hose.** 

Splice into it from the centre and add the T fitting with clamps. Add the additional/new hose to the free T end with clamps and to the other side, the fitting with clamps and tighten the pressure sensor on to it with teflon tape. 

It's advisable after making the connections and just before connecting the transducer itself turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings.

**Try to keep the sensor itself away from HV lines and also the pump itself. This will help reduce noise. **

<img width="334" alt="image" src="https://user-images.githubusercontent.com/53577819/210058187-e04d976e-cc38-43f1-90fd-3a380e603ef7.png">

<img width="339" alt="image" src="https://user-images.githubusercontent.com/53577819/210058289-44393a75-a9c4-4ef7-b5c1-c558a574a1c6.png">

![GCP TRANSDUCER](https://user-images.githubusercontent.com/42692077/146647809-970c0ccd-47c6-430c-9c71-9b651bab4bf4.png ':size=500')

Please use the tables in **3.0.2 Appendix - Component Wiring** for details on RED, BLACK and YELLOW wire connections to the Arduino. 

### *2.0.8 Finish*
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

## **3.0 Appendix**

### *3.0.1 Schematics & Diagrams*
**Schematics:**
* [GAGGIA Classic Pro **Nano** wiring](https://user-images.githubusercontent.com/109426580/202481338-a90ea5db-dfe9-44e8-8209-f97dd5e7960c.png ':size=500')

**Diagrams:**
* [GAGGIA Classic Pro **Nano** wiring](https://user-images.githubusercontent.com/109426580/202481332-a040752f-0d45-41fd-b6ec-3d84a332f097.png ':size=500')

### *3.0.2 Component Wiring* 
You can find the defined pins at the top of the .ino file.

A suggestion on wiring; components that are inside same enclosure, the same connection can be linked i.e. solder a cable to the 5v pin then take the other end and solder to the 5V of the other component, from there take one cable to the Arduino. An alternative way is to  solder similar connections and apply heat-shrink before the exit to the machine then take one wire through the machine to the Arduino.

1. POWER DELIVERY RECOMMENDATION
Method 1 - If choosing to power the system using the AC adapter then the Arduino board and all the connected components will receive power by the means of the regulated 5v the AC adapter delivers through the USB port.

| PS | Arduino | 
| --- | --- |
| VCC OUT | 5v | 
| GND OUT | GND |

Method 2 - If powering using the [ 12v ] power supply module + [ 9v ] step-down convertor follow the bellow scheme:

| Stepdown | Arduino | 
| -------- | ------- |
| OUT +    | 5v      | 
| OUT -    | GND     |

All the other boards should be connected to the same GND / 5v plane as arduino.

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

4 & 5 are the switch points from 2.0.4 Steam Config

| GCP SWITCH | ARDUINO |
| --- | --- |
| 4 | D7 | 
| 5 | GND |

6. CONTINUITY WIRING

| BREW SWITCH | ARDUINO |
| --- | --- |
|TOP | A0 |
|BOTTOM | GND |

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

***
