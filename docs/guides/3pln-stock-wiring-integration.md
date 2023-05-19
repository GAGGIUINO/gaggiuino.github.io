> [!Warning]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. 
>Following the guide you agree that any damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish will be entirely your fault!

These instructions detail how to integrate a 3PLN + SSR Gaggiuino control system (such as the [component build](/guides/lego-component-build-guide.md), PCBv2, or PCBv3) into a Gaggia Classic | Pro | Eco espresso machine. They assume that you already have an assembled control system that has successfully completed a bench test.

# What is 3PLN + SSR?

3PLN + SSR (often noted as "3PLN") describes the AC integration points of a Gaggiuino control system into an espresso machine. Through these points the Gaggiuino control device can control the espresso machine AC components either by connecting into the stock wire harness or by replacing the stock wire harness with a custom one. 


Abbr. |Name               |Description 
------|-------------------|-----------
3     | 3-Way Valve       | 3-Way Solenoid Valve that controls flow between the group head, boiler, and vent tube
P     | Pump              | Vibratory pump that pumps the water
L     | Line              | AC Line voltage
N     | Neutral           | AC Neutral voltage
SSR   | Solid-State Relay | Relay placed in-line with the boiler heaters for control

With this doc update the PCB and component installs have been synchronized to both utilize 3PLN, harmonizing the install process. Although the images shown in this guide may use the component build the install principles and machine connection points are the same for the PCB when using the stock wire harness.

# Schematics

These schematics show the connection points for integrating into the stock wiring harness with 3PLN + SSR. Study both HV and LV pages for your specific machine, as well as the notes on the schematic. In general, HV wiring changes must be made before LV.

> [!Note]
> Only one version (120 V) of the Gaggia Classic and Classic Pro schematics are shown as the integration points are identical between 120/230 V. The wire colors may be different, but those differ between models of the same voltage type as well

* **Gaggia Classic** [HV page](https://user-images.githubusercontent.com/117388662/239174929-500fe13f-d38d-4114-81c2-2f6c646aaf91.JPG), [LV page](https://user-images.githubusercontent.com/117388662/239174935-32adbe15-4ab5-4c39-809d-cf627ea36842.JPG)
* **Gaggia Classic Pro** [HV page](https://user-images.githubusercontent.com/117388662/239175752-60352cd0-ad81-4e7e-8c4c-a79a1765a7da.JPG), [LV page](https://user-images.githubusercontent.com/117388662/239175755-da160ec4-a330-4ecb-b488-fc8de6eda263.JPG)
* **Gaggia Classic Pro Eco** [HV page](https://user-images.githubusercontent.com/117388662/239175935-786110a0-635a-4afb-ad39-ff62def08d82.JPG), [LV page](https://user-images.githubusercontent.com/117388662/239175943-91f78e93-c2ea-4e9d-a445-e375ffe4b45d.JPG)

# Integration

> [!Warning]
> At this point you should have already completed a test of your system (especially if doing the component build). It's much easier to resolve issues prior to integration.

## Open machine

Take off the top cover by unscrewing the 2 top screws. You should be able to see something similar to the below image. 

> [!Note]
> If you have a US Gaggia Classic check whether you have a ground connection on your power input. If it's a 2 pole plug as seen in the image adding a ground is recommended prior to starting the integration. BOM and instructions can be found at [Grounding a Gaggia Classic](guides/grounding-a-gaggia-classic.md)

![Opened Machine](https://user-images.githubusercontent.com/117388662/239368163-aa737736-51b5-43ed-86f9-cb834e031d2a.png ':size=500')

Optional, but I recommend labeling the stock connectors with a permanent marker for ease of troubleshooting and reversal. Here are the labels I used:

Component         |Prefix |Labels <br />_see images and schematic for detail_
------------------|:-----:|:-------:
Switch Assem. (GC)|-      |1   3      7 <br />P(1-2) P(3-4) P(5-6) P(7-8)<br />2      6   8
Switches (GCP/Eco)|P - Power <br />B - Brew/Coffee <br />S - Steam |1    4<br /> 2    5<br /> 3    6
Heaters           |H      |3    4 <br />1    2
Steam TS          |S      |a    b
Brew TS           |B      |a    b
Pump              |P      |a    b <br /> _a is from fuse, unlabeled_ <br />_b is a single red wire in most machines_
Fuse (GC)         |F      |_there should be 2 wires_ <br />_in the connector to the fuse_

Here are the GC stock pump connections for clarity. Note that most connections are made at the pump, so make sure the pump wiring matches the stock [schematic](#schematics) for your machine before continuing.

![Stock pump connections](https://user-images.githubusercontent.com/117388662/239372268-1605be4b-5a0c-414d-bdc2-3524ef26b11e.png ':size=250')

## Brew Thermostat Replacement
Make a short jumper wire with male spades on both ends. Remove the wires attached to the brew thermostat (Ba and Bb) and jumper them together. Heat shrink the connections as required to prevent electrical faults. 

![Brew Thermostat Jumper Wire](https://user-images.githubusercontent.com/117388662/239383435-9a3407bc-7455-4a2d-86db-e12ea441fcfc.png ':size=500')

Unscrew the brew thermostat and replace it with the thermocouple. ***Gently** screw in the thermocouple barely finger-tight (**do not over-tighten**). This can be done in-place, but it's easier to remove the boiler (4 SHCS up from below the sheet metal), steam knob, and steam wand so that the boiler can be tipped up a bit for easier access. 

![Brew Thermostat Replaced with TC](https://user-images.githubusercontent.com/117388662/239386114-4c98cdc0-8ad6-459f-921d-61014fc1cf9c.png ':size=500')

There should already be high-temp thermal paste in place. If there is not, or if the paste is dried out, replace with a paste that has at least a 180°C working temperature. Here are some possible options:
* Thermal Grizzly Kryonaut (350°C max)
* Noctua NT-H2 (200°C max)
* SYY-157 (200°C max)
* GELID GC-Extreme (180°C max)

## Pump Area

The 3-way solenoid valve, Pump, and Neutral connections are all integrated into the wire harness around the pump. Read through the instructions, then cut extra wire length (if desired) and add crimped spade connectors.

* **3-Way valve:** Male spade. Disconnect original pump wire (labeled Pb) from the pump and connect the 3-way valve control wire to it.  
* **Pump:** Female spade. Connect the pump control wire where the original pump wire was.  
* **Neutral:** Piggyback spade. Piggyback the Neutral connection. 

## SSR

Mount the SSR to the back wall of the machine using an M4 screw and nut (you will need to mount sideways in a GCP) Remove the wires from the steam thermostat (Sa, Sb) and connect to the AC ports on the SSR (order doesn't matter). Remove disconnected thermostat if desired.

![SSR Thermostat Connections](https://user-images.githubusercontent.com/117388662/239403962-c0ef2429-ec12-4d81-b56b-02c91cd702d3.png ':size=500')

## Switch

**High Voltage**

Disconnect wires from the switch(es) and connect your last 3PLN connection (Line) with a male spade to the brew switch source wire. **Follow the [schematic](#schematics) for your machine**, a GC example is shown here:

![L Connection](https://user-images.githubusercontent.com/117388662/239404551-97d6f3e4-f62e-45c4-93d7-52d8ae373526.png ':size=500')

**Low Voltage**

> [!Tip]
> Keep LV (DC) and sensors separated from HV (AC) wires to reduce interference. I like to run AC wires near the top of the machine enclosure, mostly left of the boiler. DC wires are run near the bottom of the enclosure, mostly on the right side.

Connect GND, brewPin, and steamPin wires to the switches, making use of some of the space you've freed up by removing the HV wires. **Follow the [schematic](#schematics) for your machine**, a GC example is shown here:

![Switch LV Connections](https://user-images.githubusercontent.com/117388662/239406277-7bdd8852-5fcb-454e-9521-cd9537543144.png ':size=500')

## Pressure Transducer

The pressure transducer comes with a base O-ring, however, the threaded length of the fittings vary and many aren't long enough to seal against the base. Insert the small O-ring into the fitting, adjust flush, then screw on the transducer until it seals on an O-ring.

![Transducer and fittings](https://user-images.githubusercontent.com/117388662/239452187-429dafd7-6844-4256-ae76-b9982dcce86c.png ':size=500')

Cut the tubing in between the pump and boiler, nearer to the boiler but high enough the T is mostly vertical, not horizontal. Attach the appropriate T fitting for your machine. 

> [!Tip]
> Make sure the tubing is fully engaged on the fittings. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. For barbed fittings you may even need to use some water-based lubricant to get it all the way on.

Cut a 200-250 mm length of your tubing from the BOM and attach it to the pressure transducer fitting. Then, fill that length of tubing with water so there are no air bubbles. This can be difficult due to surface tension if you don't use a simple trick: insert a small wire down the center of the tubing and inject water with a syringe. The wire allows the water to flow down and the air to vent up because it doesn't let surface tension seal the tube.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239455051-c8fe0d0a-270e-4685-9478-d751eb746d49.png ':size=250')

Plug the filled tube into the T fitting and arrange the pressure transducer so that it is at the base of the machine, lower than the T fitting. 

![pressure transducer placement](https://user-images.githubusercontent.com/117388662/239457706-7ee5d101-d209-41b4-a3d3-ce159e98032f.png ':size=500')

> [!Tip]
> While some sensors/setups seem to have no issues with the pump vibration, others are affected by vibration and even the sensor coming in contact with the housing. In those cases it can be beneficial to wrap the sensor in foam.  
![Foam-wrapped sensor](https://user-images.githubusercontent.com/117388662/239457402-b58dfe55-6572-45b7-8960-2a4d1f9d5753.png ':size=250')

## Internal Finishing Touches

Remove the pins from the screen connector, add a length of heat shrink tubing around the cable bundle so the sharp vent doesn't cut through the soft silicone wire jacket (don't shrink it), and pass the screen wires and ST-Link wires through the back vents. Mount the ST-Link with some double-sided tape.

![Wire pass-through](https://user-images.githubusercontent.com/117388662/239461641-e4f1d5f0-e83c-458c-94ca-61b25a6c7fa0.png ':size=500')

Make sure HV AC wiring and LV DC wiring/sensors are separated. Zip-tie wire bundle, ensuring disconnected wires and connectors are constrained so they cannot make accidental contact. In a Gaggia Classic it looks like this:

![Finished Internals](https://user-images.githubusercontent.com/117388662/239461982-54c2c808-9597-4fe2-8bee-3a759064d065.png ':size=500')

When you're happy with everything, put the cover back on (don't forget to connect the ground wire).

## Screen

There's extra wire length so the screen can remain connected while the cover is removed. Snake the screen wires through the housing components and replace the pins in the connector. Make sure the wire order matches what you successfully tested in the bench test. I also like to put the nuts in the screen housing cover, use screws to draw them tight, and put a drop of super-glue on the nuts (**not the screws**) to hold them to the housing. When it's dry remove the screws.

![Screen wiring](https://user-images.githubusercontent.com/117388662/239463397-25c3e82c-07e3-4b10-b056-59cbf8d36efc.png ':size=500')

Put the screen housing together and you're ready for espresso! 

![Finished!](https://user-images.githubusercontent.com/117388662/239463949-0e90b52f-a5fa-4aed-8ea7-9047154cc213.png ':size=500')