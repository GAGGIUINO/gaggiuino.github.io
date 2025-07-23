# Wiring B: Custom Wiring

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

<img height="300" alt="Custom Wiring - Leon McKee" src="media/custom_wiring.png">

# Alternate Components

The BOM is compiled for the standard install path where all components are taken from the stock wiring harness and crimped onto new wires, following the schematics and wiring diagrams. **This is not part of the BOM**, however, stock components may be broken, unavailable, or a completely new wiring harness desired. Alternate components may be substituted for stock components as needed. Note that this list of components is still a work in progress. 

<details>
<summary><b>Alternate Component List </b> <i>(Click to expand)</i></summary>

| Description | Link(s)     | Notes       |
| :---------- | :---------- | :---------- |
| 22-16 Gauge Wire Connector | [BN1.25 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html) <br /> [4 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) | Use for splicing in components (stock or alternate) |
| 16-14 Gauge Wire Connector | [BN2 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html) <br /> [5 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) | Can crimp 2x 18 gauge wires per side. Useful for splicing 1:2 boiler connector wires on 120V machines |
| High-temp Insulation | [Silicone Heat Shrink Tube \| 4, 5, 6 mm](https://www.aliexpress.com/item/3256801522005095.html) or <br /> [Self-Fusing Silicone Tape](https://www.aliexpress.com/item/3256805094022385.html)    | Self-fusing silicone tape is more work to use, but is one-size-fits-all heat shrink when applied correctly      |
| 6.3 mm Open Barrel Spade Connectors | [6.3mm Female Spade Connectors](https://www.aliexpress.com/item/3256801761334075.html)     | Requires open barrel terminal crimper. Good up to 200° C when covered with silicone high temp insulation       |
| Nylon Spade Connectors | [Nylon Fully Insulated M/F Spade connectors](https://www.aliexpress.com/item/3256803187210898.html)     | Max temp 105° C. For connecting things away from boiler that may want to be swapped later, e.g. pump thermal fuse       |
| Nylon Flag Spade Connectors | [Nylon Flag Female Terminals](https://www.aliexpress.com/item/3256803184573157.html)     | Requires flag connector crimper. Max temp 105° C. Power plug on GCP. Red: 1x 18 gauge wire, Blue: 2x 18 gauge wires      |
| Boiler Thermal Fuse | [Resettable Thermal Fuse, NC, 185°C, 16 A, M4](https://www.aliexpress.com/item/3256805886376281.html) | Substitute for stock thermal fuse across boiler. Install location is the steam thermostat boiler boss |
| Pump Thermal Fuse | [KSD9700 Thermal Switch, 120°C, NC](https://www.aliexpress.com/item/2251832685942790.html) | Retain with hot glue (same method as stock)|
| Boiler Terminal Connectors | [TE 160783-7 (DigiKey)](https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/160783-7/5157254) or [TE 160783-7 (Mouser)](https://www.mouser.com/ProductDetail/TE-Connectivity-AMP/160783-7?qs=%252BeETdXPI8nLQYJsNGAnPEA%3D%3D) | Stock part, a bit tricky to crimp properly |
| Boiler Terminal Connector Housing | [Boiler Terminal Shroud](https://www.printables.com/model/380256) | Can be purchased from print providers, used if stock covers are unavailable |
| Boiler Terminal Crimpers | [IWISS IWS-1424A](https://www.aliexpress.com/item/3256805916886076.html) **+ Pliers** or <br /> [TE 160783-7 Crimper HS Jaws](https://www.printables.com/model/673240)| Listed only because manufacturer crimpers don't exist. Open barrel crimpers can crimp the wire connection, but the insulation needs to be done with pliers or the TE 160783-7 Crimper HS Jaws|
| Indicator Lamp | [Red 6x13 mm Neon Bulb](https://www.aliexpress.com/item/2261799834780054.html) - pick the voltage range for your machine <br /> [7.9 mm Clear Heat Shrink Tubing](https://www.aliexpress.com/item/3256804355023361.html) - 2 layers over bulb <br /> [4 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) - insulate resistor and leads | Using the stock indicators is easier. Only do this if you really don't want to cut the stock harness.
| Indicator Lamp Clips | [Gaggia Classic Pro Neon Lamp Clip](https://www.printables.com/model/647745)     | For Pro/Eco/Evo. There is a version for stock lamps as well as a tighter clip for 6 mm dia neon bulbs (adding thickness with heat shrink tubing not needed)       |
</details>

>

# Custom Wire Harness Schematics

> [!Warning|style:callout]
> * Make sure your control system has been flashed and passed the pre-install test checklist ([PCB](guides-stm32/pcb-guide.md#pre-install-test), [Component (Lego) build](guides-stm32/lego-component-build-guide.md#component-test)). It's much easier to resolve issues prior to integration.
> * If you have a US Gaggia Classic with a 2 pole power cord and plug then please see the [Grounding](guides/machine-specific-guide.md#Grounding) section of the machine-specific instructions before continuing.
> * As this wiring completely replaces the stock wiring harness it is expected that the reader can complete the wiring using only the schematics.  
> * Component builds can use the AC wiring on the schematics after completing the [Lego Component Build Guide](guides-stm32/lego-component-build-guide.md).

<!-- tabs:start -->
<!-- tab:Gaggia Classic Pro 100-120v -->

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_1_120v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_120v.png">
<!-- tabs:end -->

* Example of the AC portion of the wiring harness:  

    <img width="600" alt="GCP 120v" src="schematics/custom-3pln-examples/GCP_120v.jpg">

<!-- tab:Gaggia Classic Pro 220-240v -->

*Remember to do the [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) to make it bistable.*  

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GCP 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_1_220v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GCP 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_220v.png">
<!-- tabs:end -->

* Example of the AC portion of the wiring harness:  

    <img width="600" alt="GCP 220v" src="schematics/custom-3pln-examples/GCP_220v.jpg">

<!-- tab:Gaggia Classic 100-120v -->

*Remember to check and add [Grounding](guides/machine-specific-guide.md#grounding) if needed.*  

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GC 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_1_120v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GC 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_120v.png">
<!-- tabs:end -->

* Example of the AC portion of the wiring harness:  

    <img width="600" alt="GC 120v" src="schematics/custom-3pln-examples/GC_120v.jpg">

<!-- tab:Gaggia Classic 220-240v -->

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_1_220v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_220v.png">
<!-- tabs:end -->

* Example of the AC portion of the wiring harness:  

    <img width="600" alt="GC 220v" src="schematics/custom-3pln-examples/GC_220v.jpg">

<!-- tabs:end -->

>

# Hardware Install Notes

## Thermocouple

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

## SSR

Mount the SSR to the back wall of the machine using an M4 (or 8-32) screw, washer, and nut thru a vent slot. Make sure the SSR has space above it for the funnel piece and its screw while not touching the pump or pump housing.

![SSR Install Detail](https://github.com/user-attachments/assets/94bcb6c1-6e65-4ced-957c-9c00551140b3 ':size=300')

## Pressure Transducer
There are two methods of attaching the pressure transducer to the system: 
* T-Fitting - Tubing between Pump and boiler is cut, a T-fitting is inserted with a pressure transducer on the new branch line.
* Pressure Tap Block (PTB) - the PTB is fastened between the boiler and inlet fitting, with the pressure transducer attached to the PTB via fittings and PTFE tubing. 

Select the method that matches your components.

<!-- tabs:start -->
<!-- tab:T-Fitting -->

The pressure transducer may have a base O-ring (green in pictures), however, the threaded length of the fittings vary and many aren't long enough to seal against the base. Insert the small white O-ring into the fitting, adjust flush, then screw in the transducer until hand-tight. You can add 1/4 wrench turn after hand-tight if desired, but **do not overtighten** or you may damage the O-ring and/or not get a pressure reading.

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->

![Transducer and fittings](https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/78d801f3-9c4f-4c17-8105-74e32711af09 ':size=500')

Cut the tubing in between the pump and boiler, nearer to the boiler but high enough so the T is mostly vertical, not horizontal. Attach the push-to-connect T fitting. 

> [!Tip]
> Make sure the tubing is cut straight and fully engaged on the fittings, or it may not seal. The push-to-connect fitting has a ring of teeth and then an o-ring - the tubing must be fully inserted through both. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. 

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

Arrange the connected pressure transducer so that it is at the base of the machine, lower than the T fitting. Ignore wiring in the images as they're from a machine following the stock wiring integration. 

> [!Tip]
> It's not common, but some pressure transducers are affected by vibration and even the sensor coming in contact with the housing. In those cases it can be beneficial to wrap the sensor in foam or use adhesive to securely attach it to the machine frame.  
> <details>
> <summary><b>Foam-wrapped sensor</b> <i>(Click to expand)</i></summary>
    <img width="300" alt="GC 120v" src="https://user-images.githubusercontent.com/117388662/239457402-b58dfe55-6572-45b7-8960-2a4d1f9d5753.png">
> </details>

Before pulling shots you'll need to fill the tubing with water so there are no air bubbles. After the screen has been connected and the remainder of the install completed:

<!-- tabs:start -->
<!-- tab:Gen 3 -->
Download and run the utility profile **[UT] Tube Fill** from Community profiles in WebUI. 
<!-- tab:Gen 2 -->
Go to the Brew menu, select the Manual tab, set flow to 1 ml/s and run for ~2 minutes (with open group head) to gently fill the line.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239618595-844609d1-7b59-456e-afba-2d2b1bf73374.png ':size=250')
<!-- tabs:end -->

<!-- tab:Pressure Tap Block -->

>[!Note|style:callout|label:2 PTB Versions|iconVisibility:visible]
> There are 2 different versions of the PTB, designed for compatibility with different manufacturing methods. The LM version is shown; both follow the same assembly process and are compatible with all Gaggia Classic, Pro, Eco, Evo, and E24 models.

The pressure transducer may have a base O-ring (green in pictures), however, the threaded length of the fittings vary and many aren't long enough to seal against the base. Insert the small white O-ring into the fitting, adjust flush, then screw in the transducer until hand-tight. You can add 1/4 wrench turn after hand-tight if desired, but **do not overtighten** or you may damage the O-ring and/or not get a pressure reading.

![Transducer and fittings](https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/78d801f3-9c4f-4c17-8105-74e32711af09 ':size=500')

Screw the fitting into the PTB hand-tight, fully insert the tube into the fitting, and place the O-ring. The fitting thread should not protrude more than 1/4 of the hole diameter. 

![PTB Assembly](https://github.com/user-attachments/assets/bd6a1e31-b43d-4b4d-abfe-4204d290cf39 ':size=500')

Remove the inlet connector (metal OPV on a GC) by unscrewing the two M5 screws.

![Remove inlet](https://github.com/user-attachments/assets/12e2f8d8-5313-4f5d-b932-4b213ebf22e8 ':size=500')

Clamp the pressure tap block assembly between the group head and the inlet connector (or OPV). O-rings both face toward the group head.

![Clamped PTB Assembly](https://github.com/user-attachments/assets/8cf1157b-b990-41c1-9770-24d7ac5af067 ':size=500')

Plug the pressure transducer assembly onto the PTFE tubing; make sure the tube is fully inserted into the fitting, and the pressure transducer isn't touching any metal components.

![Finished PTB Assembly](https://github.com/user-attachments/assets/53026edc-2026-4144-9714-200cdb2ebf51 ':size=500')

After the install is complete, run flush for 10 seconds (with open group head) to fill the system, then run flush with a blank basket to test pressure.

<!-- tabs:end -->

## Internal Finishing Touches

Remove the pins from the screen connector, add a length of heat shrink tubing around the cable bundle so the sharp vent doesn't cut through the soft silicone wire jacket (don't shrink it), and pass the screen wires and ST-Link wires through the back vents. Mount the ST-Link with some double-sided tape.

![Wire pass-through](https://user-images.githubusercontent.com/117388662/239461641-e4f1d5f0-e83c-458c-94ca-61b25a6c7fa0.png ':size=250')

Make sure HV AC wiring and LV DC wiring/sensors are separated. Check that nothing (other than silicone-jacketed wires rated to 200C) can touch the boiler or steam wand. Zip-tie the wire bundle as needed. 

**Continue the installation by referencing the interface instructions.**  

* [Interface: Screen](guides/interface-screen.md) page.
<!-- tabs:end -->