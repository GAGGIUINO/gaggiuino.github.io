# Wiring A: Stock Wiring Integration

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

<img height="300" alt="Stock Wiring (lego build)" src="media/stock_wiring.jpg">

These instructions detail how to integrate a 3PLN + SSR Gaggiuino control system (such as the [component build](guides-stm32/lego-component-build-guide.md), PCBv2, or PCBv3) into a Gaggia Classic | Pro | Eco espresso machine. They assume that you already have an assembled control system that has successfully completed a bench test.

# What is 3PLN + SSR?

3PLN + SSR (often noted as "3PLN") describes the AC integration points of a Gaggiuino control system into an espresso machine. Through these points the Gaggiuino control device can control the espresso machine AC components either by connecting into the stock wire harness or by replacing the stock wire harness with a custom one. 


Abbr. |Name               |Description 
------|-------------------|-----------
3     | 3-Way Valve       | 3-Way Solenoid Valve that controls flow between the group head, boiler, and vent tube
P     | Pump              | Vibratory pump that pumps the water
L     | Line              | AC Line voltage
N     | Neutral           | AC Neutral voltage
SSR   | Solid-State Relay | Relay placed in-line with the boiler heaters for control

The PCB and component installs have been synchronized to both utilize 3PLN, harmonizing the install process. Although the images shown in this guide may use the component build the install principles and machine connection points are the same for the PCB when using the stock wire harness.

# Schematics
These schematics show the connection points for integrating into the stock wiring harness with 3PLN + SSR. Study both HV and LV pages for your specific machine, as well as the notes on the schematic. In general, HV wiring changes must be made before LV.

Save the images or right-click and open in a new tab to view at full resolution.

<details>
<summary><b>Control system schematics/diagrams for connection reference  </b> <i>(Click to expand)</i></summary>
<!-- tabs:start -->
<!-- tab:Comp Build -->
<img height="400" alt="image" src="schematics/stm32-comp-build.png">
<!-- tab:PCBv3.1/v4 -->
<img height="400" alt="image" src="schematics/stm32_pcbv3_1_board_labels.png">
<!-- tab:PCBv3 -->
<img height="400" alt="image" src="schematics/stm32_pcbv3_board_labels.png">
<!-- tabs:end -->
</details>

>

> [!Warning|style:callout]
> * Stock integration of the 220-240v Gaggia Classic Pro variants with Eco PCB is not recommended. Please use [Custom Wiring](guides-stm32/3pln-custom-wiring.md).
> * Component builds can use the AC wiring on the schematics after completing the [Lego Component Build Guide](guides-stm32/lego-component-build-guide.md). 
> * The old stock integration diagrams (drawn on manufacturer schematics) have been [archived](archive/archive.md#stock-wiring-integration-schematics)

<!-- tabs:start -->
<!-- tab:Gaggia Classic Pro 120v -->
![GCP SI PCB](../schematics/install-stock-3pln/GCP_SI_wiring_PCBv3_1_120v.png ':size=80%')

<!-- tab:Gaggia Classic 100-120v -->
![GC SI PCB](../schematics/install-stock-3pln/GC_SI_wiring_PCBv3_1_120v.png ':size=80%')

<!-- tab:Gaggia Classic 220-240v -->
![GC SI PCB](../schematics/install-stock-3pln/GC_SI_wiring_PCBv3_1_220v.png ':size=80%')

<!-- tabs:end -->

# Integration Wires

The following wires are used to integrate the stock wiring with the Gaggiuino control system:

<img height="300" alt="image" src="https://github.com/user-attachments/assets/09a876da-2380-4a97-9aad-7fbbed6007fa">

CBL   | Connections                    | Description                                  |Length (mm)
:----:|--------------------------------|----------------------------------------------|:----------:
J     | Male Spade - Male Spade        | Jumper in place of Brew Thermostat           | 70
Sa    | Fork Spade - Male Spade        | SSR AC1 in place of Steam Thermostat Spade 1 | 100
Sb    | Fork Spade - Male Spade        | SSR AC2 in place of Steam Thermostat Spade 2 | 100
3     | Female Spade - Male Spade      | PCB 3 to Pb                                  | 350
P     | Female Spade - Female Spade    | PCB P to Pump                                | 300
L     | Female Spade - Male Spade      | PCB L to B4                                  | 350
N     | Female Spade - Piggyback Spade | PCB N to Pump and Pa (into fuse)             | 300

> [!Note|style:callout]
> The listed length is generous to fit a wide variety of machines and routing paths; feel free to route and then cut to optimize for a specific build if making your own.

>

# Integration

> [!Warning|style:callout]
> * Make sure your control system has been flashed and passed the pre-install test checklist ([PCB](guides-stm32/pcb-guide.md#pre-install-test), [Component (Lego) build](guides-stm32/lego-component-build-guide.md#component-test)). It's much easier to resolve issues prior to integration.
> * If you have a US Gaggia Classic with a 2 pole power cord and plug then please see the [Grounding](guides/machine-specific-guide.md#Grounding) section of the machine-specific instructions before continuing.

## Open machine

Take off the top cover by unscrewing the 2 top screws. You should be able to see something similar to the below image. 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Opened Machine](https://user-images.githubusercontent.com/117388662/239368163-aa737736-51b5-43ed-86f9-cb834e031d2a.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Opened Machine](https://user-images.githubusercontent.com/117388662/243791638-b16cac88-6802-49a7-b1d8-13c04be99b96.png ':size=500')
<!-- tabs:end -->

I recommend labeling the stock connectors with a permanent marker for ease of troubleshooting and reversal. Here are the labels I used:

Component             |Prefix |Labels <br />_see images and schematic for detail_
----------------------|:-----:|:-------:
Switch Assem. (GC)    |-      |1   3      7 <br />P(1-2) P(3-4) P(5-6) P(7-8)<br />2      6   8
Switches (GCP/Eco)    |P - Power <br />B - Brew/Coffee <br />S - Steam |1    4<br /> 2    5<br /> 3    6
Heaters               |H      |3    4 <br />1    2
Steam Temp Switch (TS)|S      |a    b
Brew Temp Switch (TS) |B      |a    b
Valve                 |V      |a    b
Pump                  |P      |a    b <br /> _a is from fuse, GC unlabeled_ <br />_b is the single 18 gauge wire in most machines_
Pump Fuse (GC)        |F      |_there should be 2 wires_ <br />_in the connector to the fuse_

> [!Warning|style:callout]
> Misidentifying connections may result in a damaged control system! Please [ask for help](readme.md#build-process) in your Discord install-help thread if unsure.
> 
> Stock wiring colors and connector positions (especially at the pump) may not match the schematics and pictures. Please make sure the wiring matches the stock [schematic](#schematics) for your machine before continuing.

Here are the stock pump connections for clarity. 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Stock pump connections](https://user-images.githubusercontent.com/117388662/239372268-1605be4b-5a0c-414d-bdc2-3524ef26b11e.png ':size=250')
<!-- tab:Gaggia Classic Pro -->
![Stock pump connections](https://user-images.githubusercontent.com/117388662/243792655-6a186fde-062c-4f2d-b3ed-cba5d3b0c6c8.png ':size=250')
<!-- tabs:end -->

## Brew Thermostat Replacement
Make a short jumper wire with male spades on both ends. Remove the wires attached to the brew thermostat (Ba and Bb) and jumper them together. Heat shrink the connections as required to prevent electrical faults. 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Brew Thermostat Jumper Wire](https://user-images.githubusercontent.com/117388662/239383435-9a3407bc-7455-4a2d-86db-e12ea441fcfc.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Brew Thermostat Jumper Wire](https://user-images.githubusercontent.com/117388662/243794746-39d788cb-2b08-45ae-a08e-f1bb0907129d.png ':size=500')
<!-- tabs:end -->

Unscrew the brew thermostat, transfer or add thermal paste, then ***Gently** screw in the thermocouple barely finger-tight (**do not over-tighten**).  
This can be done in-place, but it's easier to remove the boiler (4 SHCS up from below the sheet metal), steam knob, and steam wand so that the boiler can be tipped up a bit for easier access. Make sure the thermocouple wire is free to rotate during the install. 

![Thermocouple Install Detail](https://github.com/user-attachments/assets/7eef096a-bcce-4d98-8a7d-ae898c3afec3 ':size=500')

After screwing in the thermocouple (and reinstalling the boiler, if necessary), run the thermocouple wire to the front of the Gaggia, around the boiler, and back to the control enclosure (avoid going back behind the pump area). 

> [!Note|style:callout]
>There should already be high-temp thermal paste in place. If there is not, or if the paste is dried out, replace with a paste that has at least a 180°C working temperature. 
><details>
><summary><b>Thermal Paste Options</b> <i>(Click to expand)</i></summary>
>
>* Thermal Grizzly Kryonaut (350°C max)  
>* Noctua NT-H2 (200°C max)  
>* SYY-157 (200°C max)  
>* GELID GC-Extreme (180°C max)
></details>

## Pump Area

The 3-way solenoid valve, Pump, and Neutral connections are all integrated into the wire harness around the pump. Read through the instructions, then cut extra wire length (if desired) and add crimped spade connectors.

* **3-Way valve:** Male spade. Disconnect original pump wire (labeled Pb) from the pump and connect the 3-way valve control wire to it.  
* **Pump:** Female spade. Connect the pump control wire where the original pump wire was.  
* **Neutral:** Piggyback spade. Piggyback the Neutral connection. 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Pump Area Connections](https://github.com/user-attachments/assets/08201c41-7c72-4839-b85b-654710d979d0 ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Pump Area Connections](https://github.com/user-attachments/assets/b8b0da1a-111e-4a19-8c0f-7b933b973026 ':size=500')
<!-- tabs:end -->

## SSR

Mount the SSR to the back wall of the machine using an M4 (or 8-32) screw, washer, and nut. Remove the wires from the steam thermostat (Sa, Sb) and connect to the AC ports on the SSR (order doesn't matter). To ensure a good connection, loop the bare wire around the clamping screw under the clamping plate, or crimp wire to forked spade connectors and clamp those. Remove disconnected thermostat if desired.

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![SSR Thermostat Connections](https://user-images.githubusercontent.com/117388662/239403962-c0ef2429-ec12-4d81-b56b-02c91cd702d3.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
Make sure the SSR has space above it for the funnel piece and its screw.

![SSR Thermostat Connections](https://user-images.githubusercontent.com/117388662/246569790-dfc78317-caef-4bba-a528-466affb516b1.png ':size=500')
<!-- tabs:end -->

## Switch

**High Voltage**

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
Disconnect wires from the switch and connect your last 3PLN connection (Line) with a male spade to the brew switch source wire. **Follow the [schematic](#schematics) for your machine**

![L Connection](https://user-images.githubusercontent.com/117388662/239404551-97d6f3e4-f62e-45c4-93d7-52d8ae373526.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
Disconnect and move wires from the switches and connect your last 3PLN connection (Line) with a male spade to the brew switch source wire. **Follow the [schematic](#schematics) for your machine**. When you're done you should have one empty column of spades on both the brew and steam switches.

![L Connection](https://user-images.githubusercontent.com/117388662/243890489-77c730e4-20e3-4e6f-9cb5-6295780194fc.png ':size=500')
<!-- tabs:end -->
**Low Voltage**

> [!Tip]
> Keep LV (DC) and sensors separated from HV (AC) wires to reduce interference. I like to run AC wires near the top of the machine enclosure, mostly left of the boiler. DC wires are run near the bottom of the enclosure, mostly on the right side.

Connect GND, brewPin, and steamPin wires to the switches, making use of some of the space you've freed up by removing the HV wires. **Follow the [schematic](#schematics) for your machine**.
<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Switch LV Connections](https://user-images.githubusercontent.com/117388662/239406277-7bdd8852-5fcb-454e-9521-cd9537543144.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Switch LV Connections](https://user-images.githubusercontent.com/117388662/246567190-77c4ca27-fb2d-4105-bb41-cc5875a4cc50.png ':size=500')
<!-- tabs:end -->

## Pressure Transducer

The pressure transducer comes with a base O-ring (green in pictures), however, the threaded length of the fittings vary and many aren't long enough to seal against the base. Insert the small white O-ring into the fitting, adjust flush, then screw in the transducer until hand-tight. You can add 1/4 wrench turn after hand-tight if desired, but **do not overtighten** or you may damage the O-ring and/or not get a pressure reading.

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->

![Transducer and fittings](https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/78d801f3-9c4f-4c17-8105-74e32711af09 ':size=500')

Cut the tubing in between the pump and boiler, nearer to the boiler but high enough the T is mostly vertical, not horizontal. Attach the push-to-connect T fitting. 

> [!Tip]
> Make sure the tubing is cut straight and fully engaged on the fittings or it may not seal. The push-to-connect fitting has a ring of teeth and then an o-ring - the tubing must be fully inserted through both. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. 

Cut a 200-250 mm length of your tubing from the BOM and attach it to the pressure transducer fitting.

![pressure transducer placement](https://user-images.githubusercontent.com/117388662/239457706-7ee5d101-d209-41b4-a3d3-ce159e98032f.png ':size=500')
<!-- tab:Gaggia Classic Pro -->

![Transducer and fittings](https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/f294cdb2-000b-4583-b258-8dd53854a2ec ':size=500')

Cut the tubing in between the pump and boiler, roughly 65 mm above the boiler connection. Slide a loose hose clamp onto each tube, attach the barbed T fitting, and secure the hose clamps over the middle of the barbed area. 

> [!Tip]
> Make sure the tubing is cut straight and fully engaged on the fittings. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. You may even need to use some water-based lubricant to get it all the way on.

Cut a 200-250 mm length of your tubing from the BOM and attach it to the pressure transducer fitting, securing each end with a hose clamp as before.

![pressure transducer placement](https://user-images.githubusercontent.com/117388662/246573952-ca092066-d107-46e6-85f1-e2a7b19865e0.png ':size=500')
<!-- tabs:end -->

Arrange the connected pressure transducer so that it is at the base of the machine, lower than the T fitting. 

> [!Tip]
> It's not common, but some pressure transducers are affected by vibration and even the sensor coming in contact with the housing. In those cases it can be beneficial to wrap the sensor in foam or use adhesive to securely attach it to the machine frame.  
> <details>
> <summary><b>Foam-wrapped sensor</b> <i>(Click to expand)</i></summary>
    <img width="300" alt="GC 120v" src="https://user-images.githubusercontent.com/117388662/239457402-b58dfe55-6572-45b7-8960-2a4d1f9d5753.png">
> </details>

 Before pulling shots you'll need to fill the tubing with water so there are no air bubbles. There are 2 options:

<details>
<summary><b>Machine fill - recommended</b> <i>(Click to expand)</i></summary>

After the screen has been connected and the remainder of the install completed, go to the Brew menu, select the Manual tab, set flow to 1 ml/s and run for ~2 minutes (with open group head) to gently fill the line.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239618595-844609d1-7b59-456e-afba-2d2b1bf73374.png ':size=250')

</details>

<details>
<summary><b>Hand fill</b> <i>(Click to expand)</i></summary>

This should be done before finishing the install and is easiest before connecting the T fitting. Surface tension can make hand filling the tube difficult if you don't use a simple trick: insert a small wire down the center of the tubing and inject water with a syringe. The wire allows the water to flow down and the air to vent up because it doesn't let surface tension seal the tube.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239455051-c8fe0d0a-270e-4685-9478-d751eb746d49.png ':size=250')
</details>

## Internal Finishing Touches

Remove the pins from the screen connector, add a length of heat shrink tubing around the cable bundle so the sharp vent doesn't cut through the soft silicone wire jacket (don't shrink it), and pass the screen wires and ST-Link wires through the back vents. Mount the ST-Link with some double-sided tape.

![Wire pass-through](https://user-images.githubusercontent.com/117388662/239461641-e4f1d5f0-e83c-458c-94ca-61b25a6c7fa0.png ':size=250')

Make sure HV AC wiring and LV DC wiring/sensors are separated. Check that nothing (other than silicone-jacketed wires rated to 200C) can touch the boiler or steam wand. Zip-tie the wire bundle as needed, ensuring disconnected wires and connectors are constrained so they cannot make accidental contact. Here are examples with a component build enclosure:

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Finished Internals](https://user-images.githubusercontent.com/117388662/239461982-54c2c808-9597-4fe2-8bee-3a759064d065.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Finished Internals](https://user-images.githubusercontent.com/117388662/246574886-6a137c93-dc74-4d76-9eff-661204bd7571.png ':size=500')
<!-- tabs:end -->

**Continue the installation by referencing the interface instructions.**  

* [Interface: Screen](guides/interface-screen.md) page.
