> [!Warning]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. 

!>**By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!**

# 1.0.0 TEST INSTALL
We are not installing inside the machine yet. We need to ensure our nano and expansion board are soldered to a good standard. We just want to test as much as we can to make sure we've not got any duds from a base functionality point of view.

We need to understand what goes where. The schematics in [3.1.0 Schematics and Diagrams](#_310-schematics-and-diagrams) aren't really rocket science but for someone who's never disassembled or has no experience working with electrical circuits it might get confusing really fast. 

> [!NOTE]
>1. No permanent connections are needed during testing.
>2. Your microcontroller and expansion board header pins need to be soldered perfectly, see [Recommendations](/learning/learning-sources.md)
>3. The 5v/GND Arduino board pins will be shared between all the connected devices.
>4. All component wiring tables are in the appendix at the end [3.2.0 Component Wiring](#_320-component-wiring).

## 1.0.1 Arduino Config 
Place Arduino into the expansion board the correct way round. Power it through USB adapter for now during the testing phase.

Image of Arduino with pins soldered:

![image](https://user-images.githubusercontent.com/53577819/154988207-3d54e924-3ab0-4e47-a4e9-188f7e839610.jpg ':size=500')

Image of expansion with pins (solder from the bottom):

![image](https://user-images.githubusercontent.com/53577819/154988218-26160147-e821-47e7-8152-d8ec0a8f0d43.png ':size=500')

Make sure the terminals are correct way round and place the Arduino into the expansion board.

?>You must solder your pins and take the time now to get your soldering perfect. It'll save time in the long run. **Refer to [Recommendations](learning/learning-sources.md) for soldering!**

!>**Attention! You are not soldering the Arduino to the expansion board itself. You are only soldering the pins to the Arduino and pins to the expansion board. The Arduino then just sits/connects into the expansion board pins.**

## 1.0.2 Thermocouple MAX6675 Config
You should have bought and received a MAX6675 board which comes with a test thermocouple. We're swapping this for the **C-M4 screw K-Type thermocouple sensor** as this is what will be replacing the original that's in the machine.
 
![image](https://user-images.githubusercontent.com/53577819/154988423-f741a369-ec60-4266-9544-0effedb57292.jpg ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154988392-619a5bc2-99cc-499d-8ad8-42792b094fd2.jpg ':size=500')

?>Refer to the [3.2.2 Component Wiring](#_322-thermocouple-max6675) section on wiring to the arduino.
## 1.0.3 Solid State Relay Config
This relay is what manages the temp by cutting the voltage when the thermocouple is at a set temp. 

![image](https://user-images.githubusercontent.com/53577819/154988554-5be0bb0a-dcf2-4bf7-a70f-4c356d00eea6.jpg ':size=500')

?>Refer to the [3.2.3 Component Wiring](#_323-solid-state-relay) section on wiring to the arduino.
## 1.0.4 Nextion LCD Config
The correct screen size is **2.4"**. If yours does not have markings for wiring then please see below image

![image](https://user-images.githubusercontent.com/53577819/154988491-28c1e861-46bc-433b-a5f8-8e9eeb8b51ed.png ':size=500')

![image](https://user-images.githubusercontent.com/53577819/154988514-13a1d7af-f704-49b6-975b-aeee1318cf36.jpg ':size=500')

?>Refer to the [3.2.4 Component Wiring](#_324-nextion-lcd-display) section on wiring to the arduino.
## 1.0.5 Software Install
?>To flash the Arduino Nano microcontroller, pls follow the video from the [Prerequisites](prereq/prerequisites.md) section of this site.

!>Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.

Download and unzip the *.tft file on a FAT32(MS-DOS (FAT32)) formatted microSD card and upload on the LCD panel using the onboard card reader.

1. Plug LCD back into Arduino Board Setup.
2. Locate “nextion-discovery-lcd.tft” or “nextion-basic-lcd.tft” (depends on what you purchased).
3. Copy the file to a FAT32 formatted MicroSD card.
* If on Mac for some reason it adds a second file beginning with a "." use terminal to change.directory to the microSD and use "rm ._nextion-*YOUR-VERSION*-lcd.tft" to remove that file.
4. Place MicroSD card inside the Nextion display.
5. Power on the Arduino Board Setup and installation should occur automatically.
6. Once “**successed**” turn power off and remove the MicroSD card, only now setup can be powered.

## 1.0.6 Test
You should now see the Gaggiuino project on the LCD. 
If your connections are sound and well secured, you should see a temperature reading on screen. The expected temp reading will contain the default offset of 7 (which means the initial temp will be = room temp -7)

Try applying heat with your hand and you should see the temperature respond (if not, I recommend confirming all connections are correct and adequately tightened.  Mine did not respond at first and turned out one of the connections to the Arduino board was not tight enough)

If everything looks good, move on to Installing into the Gaggia Classic Pro

**If all the above works as expected you're ready to install it inside the machine.**

# 2.0.0 Install
Undo everything as we will now install into the machine. 

All components except the Arduino and LCD will be internal to the machine. Remember this when wiring the LCD. 

For each of the components we want to start guesstimating on cable length. You can do this by placing components where you want to place them. Close together components can share similar wiring i.e. 5v and GND.

?>Please use the tables in [3.2.0 Component Wiring](#_320-component-wiring) for details on pin connections to the Arduino. 

## 2.1.0 Base Functionality

> [!NOTE]
> If you have the GAGGIA New Classic 2018/2019 (auto shut-off after 20mins), then you will need to fully bypass the ECO PCB that is on board. Steps are shown here [Bypass ECO Board](#_212-bypass-eco-board).

### 2.1.1 Power Delivery
Take off the top cover of your machine by unscrewing the 2 top screws. Be sure to mark your top left power connector so you don't mix them up (even though it's not that hard to understand which one is which).

Prepare splitter cables with the below specs:
1. Black splitter, 18AWG, 10cm, female end, male end, male end.
    - Female end to N front power switch panel.
2. Red splitter, 18AWG, 10cm, female end, male end, male end.
    - Female end to L front power switch panel.

Example of a red and black splitter:

![image](https://user-images.githubusercontent.com/53577819/154988645-5f1da175-7d09-437a-ac2c-f64e16f3a564.jpg ':size=350')

To determine where piggyback locations are check what the schematics say [3.1.0 Schematics & Diagrams](#_310-schematics-and-diagrams).

Whilst following schematics it's important to **test** you have found the correct piggyback locations. In order to do this please follow the below instructions before turning on your machine.

![image](https://user-images.githubusercontent.com/53577819/154982423-82b4bdb4-ca78-4077-90c0-77b349c8c3d2.JPG ':size=350')

* Set it to 600V~ (AC) as shown above and test the connectors on the switches
* Just wiggle the connector on the switch out a touch to expose a tiny bit of metal where you put your lead on
* Use schematic to find a GND point
* Your live piggyback will show no voltage until the machine is switched on

As stated you want to find the connector that only shows voltage after flipping the machine machine on. 

If your LCD is on even though you've not flipped the machine switch on, this means you've piggybacked into the mains live which has constantly got voltage - **this is not correct!**

!>Below are snippets of the power switch which are in [Schematics and Diagrams](#_310-schematics-and-diagrams).

<!-- tabs:start -->
<!-- tab:Gaggia Classic Pro -->
On the power switch - wire in switch pole 2 as LIVE piggyback and switch pole 5 as GND.

![image](https://user-images.githubusercontent.com/53577819/220789498-d8372d09-30b6-4a2a-ba05-2bad4f847aaf.png ':size=350')

<!-- tab: Gaggia New Classic (auto shut-off) -->
> [!NOTE]
>Firstly refer to section [2.1.2 Bypass ECO Board](#_212-bypass-eco-board). 

After bypassing the eco board you can then use **power** switch poles 1 as LIVE and 4 as GND.

<img width="470" alt="image" src="https://user-images.githubusercontent.com/53577819/217042451-28d73f79-0eda-45e0-a6f5-f5784cfe840f.png">

<!-- tabs:end -->

Now that you have tapped into the machine power only when it is switched on you can now wire up the 12v PSU.

![image](https://user-images.githubusercontent.com/53577819/210059859-be0135a8-7041-48ab-a2a5-daa8c86d04a1.png" ':size=500')


?> Below cables have exposed ends. It is recommended to twist, tin and push these through holes before soldering.

Prepare 2 more cables with the below spec:
1. Black, 22AWG, about 25cm, female spade end, exposed end.
    - Connect female spade to your neutral piggyback spade. Exposed end goes into 12v PSU AC terminal.
2. Red, 22AWG, about 25cm, female spade end, exposed end.
    - Connect female spade to your live piggyback spade. Exposed end goes into remaining 12v PSU AC terminal.

Prepare more cables with the below spec:
1. Black, 22AWG, about ~5cm, exposed ends.
    - Connects from 12v GND/- to 5V IN - 
2. Red, 22AWG, about ~5cm, exposed ends.
    - Connects from 12v VCC/+ to 5V IN +  
3. Black, 26AWG, about ~10cm, exposed ends.
    - Connects from 5v OUT- to the GND of expansion.
4. Red, 26AWG, about ~10cm, exposed ends.
    - Connects from 5v OUT+ to the 5V of expansion. 

!>**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**

?>Refer to the [3.2.1 Component Wiring](#_321-power-delivery) section on wiring to the arduino.
### 2.1.2 Bypass ECO Board
!>Skip this section if you **DO NOT** have a Gaggia New Classic 2018/19

?>You can identify if you have an ECO machine (usually sold in EU/UK) if your machine turns off automatically after 20mins. This requires you to look at the [Gaggia New Classic 2018/19 Nano Wiring](#_310-schematics-and-diagrams). 

Prepare the following cables to the below spec:

1. Red, 18AWG, 5cm, male spade ends.
    - Refer to you **brew** switch. With this cable bridge poles 1 & 2 (on left of the brew switch). This will disable the 20mins timer. It does not however completely bypass ECO board. 
2. Red 18AWG, female spade ends.
    - Remove the L line from the back of the machine and connect to power switch poles 2 (LIVE)
3. Black 18AWG female spade ends.
    - Remove the N line from the back of the machine and connect to power switch poles 5 (NEUTRAL).

_Length for these cables is to cover the distance from the back to the front of machine + extra._

?>If you're struggling to follow schematics you can follow [this](https://www.youtube.com/watch?v=WNs3uSLA4Ts&t=199s) video. Steps for physically removing the ECO PCB are not provided as there are other resources on the web on how to do this.

!>**Remember to remove the middle spring from your power switch.**

### 2.1.3 Thermocouple MAX6675
Prepare the following cable to the below spec:

1. Black, 18AWG, 5cm, two male ends.
    - Bridge the two wires disconnected from the brew thermostat. 

Watch this video on how to [detach the boiler](https://www.youtube.com/watch?v=0ipvBdWaVzQ) until the 5min mark. This will allow enough access to remove the thermocouple and replace it with the m4 bolted thermocouple sensor. 

Remove the two connectors from the original thermostat which are to be bridge.

![image](https://user-images.githubusercontent.com/53577819/154983715-46b1332f-f88a-4ef3-a625-b7f2788caf97.jpeg ':size=350')

Now unscrew the original thermostat and replace with the m4 brass thermocouple. Be sure to apply some thermal paste (just a teeny tiny bit) on the _**threads only**_. 

!>It is important to tighten the m4 bolt at **barely** fingertip strength. 

![image](https://user-images.githubusercontent.com/53577819/154989188-6bc38c2c-60df-47f6-98d9-b121f28438d6.jpg ':size=350')

![image](https://user-images.githubusercontent.com/53577819/154989228-2f9a3669-551b-4f45-a82a-22b4fe41fa89.jpg ':size=350')

![image](https://user-images.githubusercontent.com/53577819/154984016-714b6532-e31d-42d3-b2ee-cf064487db66.jpeg ':size=350')

?>Consider installing the pressure sensor now whilst the boiler is out [Pressure Transducer](#_222-pressure-transducer).

Now re-attach the boiler.

!>**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**

?>Refer to the [3.2.2 Component Wiring](#_322-thermocouple-max6675) section on wiring to the arduino.
### 2.1.4 Solid State Relay

?>Recommended to use U type spade to connect wires to SSR.
> Optional: might be a good idea to either tape up the exposed steam thermostat or remove it and tape up the exposed location.

Remove the steam thermostat connections cables:

![image](https://user-images.githubusercontent.com/53577819/154989308-14e9ea82-8a60-4f3d-bd9f-05dda6fa15c8.JPG ':size=350')

Prepare cables with below spec:
1. Red, 18AWG, 10cm, one male spade end, one exposed end (or U spade).
    - Male end goes to steam thermostat connection. Other end goes to port 1 of SSR
2. Red, 18AWG, 10cm, one male spade end, one exposed end (or U spade).
    - Male end goes to steam thermostat connection. Other end goes to port 2 of SSR

![image](https://user-images.githubusercontent.com/53577819/154989357-ec8c4853-0bb9-4eec-8629-dfc76e72e725.jpg ':size=350')

![image](https://user-images.githubusercontent.com/53577819/154989336-76f91fb5-2fdd-4c53-b968-e860af3f8505.jpg ':size=350')

?>Refer to the [3.2.3 Component Wiring](#_323-solid-state-relay) section on wiring to the arduino.
### 2.1.5 Steam Handling
!>**Very important to NOT turn on the machine until we check the steam switch wire positions**

<!-- tabs:start -->
<!-- tab:Gaggia Classic Pro -->
Image of the steam switch schematic:
1. Move steam switch wire 4 to steam switch pole 1.
2. Unplug and secure steam switch wire 5.
3. Connect steam switch poles 4 and 5 to the Arduino nano as shown in [3.2.5 Component Wiring](#_325-steam-handling), using 26AWG wires.

![image](https://user-images.githubusercontent.com/53577819/154989457-f5ac859e-5aa5-4554-be46-fba6ad4fa1f0.png ':size=350')

<!-- tab:Gaggia New Classic (auto shut-off) -->
1. Unplug and secure the green connector (steam poles 1).
2. Move the single black connector on switch pole 4 to switch pole 1.
3. Unplug and secure the single white connector (possibly on switch pole 2 or 5).
4. Move the double white connector to switch pole 2. 
5. Move the orange connector on to switch pole 3. 
6. Connect steam switch poles 4 and 5 to the Arduino nano as shown in [3.2.5 Component Wiring](#_325-steam-handling), using 26AWG wires.

![image](https://user-images.githubusercontent.com/53577819/221423529-7c64604f-0a47-4989-857a-09ce6ce9e2b2.png ':size=350')

<!-- tabs:end -->

### 2.1.6 Continuity Brew Detection
Prepare 2 cables with the below spec:
1. Green (just not red or black), 26AWG, length from brew to Arduino, one exposed end, one female spade end.
2. Black, 26AWG, length from brew to Arduino, one exposed end, one female spade end.

As shown below plug your cables in to the circled connections on the brew switch:  

![image](https://user-images.githubusercontent.com/53577819/154985120-fe503708-50c1-4376-9459-d72312fbbadc.jpeg ':size=350')

?>Refer to the [3.2.6 Component Wiring](#_326-continuity-brew-detection) section on wiring to the arduino.
## 2.2.0 Extended Functionality
### 2.2.1 RobotDYN Dimmer
Prepare 3 cables with the below spec:
1. Red, 18AWG, 15cm, one exposed end, one female spade end.
    - From the dimmer positive line OUT with the female end going into one of the pump connections itself. 
2. Red, 18AWG, 15cm, one exposed end, one male spade end.
    - From the dimmer L line IN with the male end going into the connector that was removed from the pump.
3. Black splitter, 18AWG, 15cm, one exposed end, one male spade end, one female spade end.
    - From the dimmer N line IN with the male into the connector that was removed from the pump and female into the remaining connection on the pump itself.

!>Please check whether your dimmer ports placement in the case it differs from the images before connecting the dimmer, it's very important to feed the IN and OUT wires correctly!

Example of dimmer ports:

![image](https://user-images.githubusercontent.com/53577819/154989499-7e95ca82-f8eb-4f63-b57b-3ca1e7e14eeb.png ':size=350')

Connections detailed in the image below from the pump (mark the connector either L or R for where it was located either left or right in relation to the pump):-

![image](https://user-images.githubusercontent.com/53577819/154989519-4e5ba059-22a4-4397-8dfb-5b7dff411bbf.jpg ':size=350')


> [!Warning]
> Triple check your dimmer board on what is marked as IN and OUT. You need to make sure they are connected properly. **IF YOU DO NOT YOU WILL DESTROY THIS COMPONENT.**

![image](https://user-images.githubusercontent.com/53577819/155005284-b22a6652-87b0-42db-9d35-5d2bc8b9247e.jpg ':size=350')

![image](https://user-images.githubusercontent.com/53577819/155005572-1d7c2ef1-ed1e-4c6e-9004-2fc22c73d83b.jpg ':size=350')

!>**Make sure this component is well insulated and enclosed. You do not want to touch it or let it make contact with anything whilst the machine is on!**

?>Refer to the [3.2.7 Component Wiring](#_327-robotdyn-dimmer) section on wiring to the arduino.
### 2.2.2 Pressure Transducer
The pressure sensor will be tapping into the orange braided hose connecting the pump outlet and the boiler inlet. 

!>**There is no need to take off your original saeco hose.** 

Splice into it from the centre and add the T fitting with clamps. Add the additional/new hose to the free T end with clamps and to the other side, the fitting with clamps and tighten the pressure sensor on to it with teflon tape. 

It's advisable after making the connections and just before connecting the transducer itself turn on the machine and while cold engage the pump to fill the transducer hose with water as well, leaving a lot of air in the system might play funny with the readings.

**Try to keep the sensor itself away from HV lines and also the pump itself. This will help reduce noise.**

![image](https://user-images.githubusercontent.com/53577819/210058187-e04d976e-cc38-43f1-90fd-3a380e603ef7.png ':size=500')

Make sure to push the hose all the way up to the ends on each side, the T and the pressure sensor.

![image](https://user-images.githubusercontent.com/53577819/210059113-91543a43-2b47-4828-8e3b-59ab303a4449.png ':size=500')

![image](https://user-images.githubusercontent.com/53577819/210632536-762bff36-2776-4a6c-8c40-ea43f9e2f1d3.png ':size=500')

?>Refer to the [3.2.8 Component Wiring](#_328-pressure-transducer) section on wiring to the arduino.
### 2.2.3 Finish
If you haven't already, you're ready to connect everything to the Arduino. Use [3.2.0 Component Wiring](#_320-component-wiring) for quickly referencing all components. 

One piece of advice would be to solder all cables to their respective boards as during the machine operation there is quite a bit of vibration which can introduce noise/frequent. This can lead to unexplained behaviours.

Any components sitting next to each other can have their equivalent pins linked with a cable.

You will be expected to solder similar pins i.e. all GND and all 5v together in order to fit into and screw down on the expansion board terminals. You can use either WAGOS for this or using some strip-board. 

?>Please refer to [Lego Component Housing Guide](guides/lego-component-build-guide.md) on how to setup and house your components for best fit into the machine.

On first start up record and send to **#first-start** channel of discord. This helps with diagnosing issues.

Remember to change and save your correct region settings.

Configure you PP and PI settings and get prepped for a shot if all is well. Record and upload to **#first-shot** on the discord. 

All going well, feel like an absolute coffee titan each and every time you pull a shot.

?>If you have any issues, firstly check the rules on the discord and then open an **#install-help...** for your respective machine. Try to make sure you do some research with the use of the powerful search function on discord to search for keywords with images or links etc...

# 3.0.0 Appendix
## 3.1.0 Schematics and Diagrams
> [!NOTE]
>**THE SCHEMATIC DRAWINGS HAVE BEEN DRAWN FLIPPED AND UPSIDE DOWN. BLAME GAGGIA.**

**Schematics:**
* [GAGGIA New Classic 2018/19](https://user-images.githubusercontent.com/53577819/214380779-ec53b99b-2b7c-4781-acdc-90c3879353c0.png)
* [GAGGIA New Classic 2018/19 **Nano** Wiring](https://user-images.githubusercontent.com/53577819/221353183-6b389c6e-dd53-4594-b504-79460aa15fda.png)
* [GAGGIA Classic Pro **Nano** Wiring](https://user-images.githubusercontent.com/53577819/221353191-ebc47b06-96c2-4775-8fcd-23f7a583fc2a.png)

**Diagrams:**
* [GAGGIA Classic Pro **Nano** Wiring](https://user-images.githubusercontent.com/53577819/210629022-76457adc-3575-4a9c-8d6f-a8f7bc18fd2a.png)

## 3.2.0 Component Wiring
You can find the defined pins at the top of the .ino file.

A suggestion on wiring; components that are inside same enclosure, the same connection can be linked i.e. solder a cable to the 5v pin then take the other end and solder to the 5V of the other component, from there take one cable to the Arduino. An alternative way is to  solder similar connections and apply heat-shrink before the exit to the machine then take one wire through the machine to the Arduino.

?>Any wires going to the expansion board itself will be **26AWG**.
### 3.2.1 Power Delivery
| 12v | 5V IN | 5V OUT | NANO | 
| ---- | ---- | ---- | ---- |
| VCC   | IN +  | OUT +  | 5v      | 
| GND   | IN -  | OUT -  | GND     |

All the other boards should be connected to the same GND / 5V plane as NANO.
### 3.2.2 Thermocouple MAX6675
| MAX6675 | NANO |
| ------- | ------- |
| VCC | 5V |
| GND | GND |
| SCK | D6 |
| SO  | D4 |
| CS  | D5 | 
### 3.2.3 Solid State Relay 
| SSR | NANO |
| --- | --- |
| 4 | GND |
| 3 | D8 |
### 3.2.4 Nextion LCD Display
| NEXTION | NANO |
| --- | --- |
|TX | RX |
|RX | TX |
|VCC/5V | 5V |
|GND | GND |
### 3.2.5 Steam Handling
4 & 5 are the steam switch points from [2.1.5 Steam Handling](#_215-steam-handling)

| GCP SWITCH | NANO |
| ----- | ---- |
|   4   | D7 | 
|   5   | GND |
### 3.2.6 Continuity Brew Detection
| BREW SWITCH | NANO |
| --- | --- |
|TOP  | A0 |
|BOTTOM | GND |
### 3.2.7 RobotDYN Dimmer
| DIMMER | NANO |
| --- | --- |
| VCC | 5V |
| GND | GND |
| Z-C | D2 |
| PSM/DIM | D9 |
### 3.2.8 Pressure Transducer
| TRANSDUCER | NANO |
| --- | --- |
| RED | 5V |
| BLACK | GND |
| YELLOW | A1 |
***
