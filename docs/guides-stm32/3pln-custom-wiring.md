# Wiring B: Custom Wiring

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

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

> [!Note|style:callout]
> * As this wiring completely replaces the stock wiring harness it is expected that the reader can complete the wiring using only the schematics.  
> * Component builds can use the HV wiring on the [PCBv3 (3PLN)](#pcb-v3-3pln) schematics after completing the [Lego Component Build Guide](guides-stm32/lego-component-build-guide.md).

### PCB v3 (3PLN)
<!-- tabs:start -->
<!-- tab:Gaggia Classic 100-120v -->

*Remember to check and add [Grounding](guides/machine-specific-guide.md#grounding) if needed.*  

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GC 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_1_120v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GC 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_120v.png">
<!-- tabs:end -->

<!-- tab:Gaggia Classic 220-240v -->

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_1_220v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_220v.png">
<!-- tabs:end -->

<!-- tab:Gaggia Classic Pro 100-120v -->

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_1_120v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_120v.png">
<!-- tabs:end -->

<!-- tab:Gaggia Classic Pro 220-240v -->

*Remember to do the [Power switch mod](guides/machine-specific-guide.md#power-switch-mod) to make it bistable.*  

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
<img width="600" alt="GCP 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_1_220v.png">
<!-- tab:PCBv3 -->
<img width="600" alt="GCP 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_220v.png">
<!-- tabs:end -->

<!-- tabs:end -->

**Examples of the high voltage 3PLN custom wiring harness:**

<!-- tabs:start -->
<!-- tab:Gaggia Classic 100-120v -->
<img width="600" alt="GC 120v" src="schematics/custom-3pln-examples/GC_120v.jpg">
<!-- tab:Gaggia Classic 220-240v -->
<img width="600" alt="GC 220v" src="schematics/custom-3pln-examples/GC_220v.jpg">
<!-- tab:Gaggia Classic Pro 100-120v -->
<img width="600" alt="GCP 120v" src="schematics/custom-3pln-examples/GCP_120v.jpg">
<!-- tab:Gaggia Classic Pro 220-240v -->
<img width="600" alt="GCP 220v" src="schematics/custom-3pln-examples/GCP_220v.jpg">
<!-- tabs:end -->

>

# Hardware Install Notes

## Thermocouple

Unscrew the brew thermostat, transfer or add thermal paste, then ***Gently** screw in the thermocouple finger-tight (**do not over-tighten**). This can be done in-place, but it's easier to remove the boiler (4 SHCS up from below the sheet metal), steam knob, and steam wand so that the boiler can be tipped up a bit for easier access. You'll want to have the thermocouple wire free to rotate during the install. 

>[!Tip]
>Depending on your machine type and location of your Gaggiuino control system it may be easier to run the thermocouple wire to the front of the machine and around the boiler to the back instead of going back behind the pump area. Pick the path with the fewest AC wires in the area.

>[!Note]
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

Mount the SSR to the back wall of the machine using an M4 (or 8-32) screw, washer, and nut. Make sure the SSR has space above it for the funnel piece and its screw while not touching the pump or pump housing.

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

Cut the tubing in between the pump and boiler, roughly 65 mm above the boiler connection. Attach the barbed T fitting. 

> [!Tip]
> Make sure the tubing is cut straight and fully engaged on the fittings. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. You may even need to use some water-based lubricant to get it all the way on.

Cut a 200-250 mm length of your tubing from the BOM and attach it to the pressure transducer fitting.

![pressure transducer placement](https://user-images.githubusercontent.com/117388662/246573952-ca092066-d107-46e6-85f1-e2a7b19865e0.png ':size=500')
<!-- tabs:end -->

Arrange the connected pressure transducer so that it is at the base of the machine, lower than the T fitting. Ignore wiring in the images as they're from a machine following the stock wiring integration. 

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

Make sure HV AC wiring and LV DC wiring/sensors are separated. Check that nothing (other than silicone-jacketed wires rated to 200C) can touch the boiler or steam wand. Zip-tie the wire bundle as needed. 

When you're happy with everything, put the cover back on (don't forget to connect the ground wire).

## Screen

There should be extra wire length so the screen can remain connected while the cover is removed. If that is not the case, solder wire extensions. Snake the screen wires through the housing components and replace the pins in the connector. Make sure the wire order matches what you successfully tested in the bench test. I also like to put the nuts in the screen housing cover, use screws to draw them tight, and put a drop of super-glue on the nuts (**not the screws**) to hold them to the housing. When it's dry remove the screws.

![Screen wiring](https://user-images.githubusercontent.com/117388662/239463397-25c3e82c-07e3-4b10-b056-59cbf8d36efc.png ':size=500')

Put the screen housing together, push the spare screen wire (and heat shrink tubing) back through the vent hole and you're ready for espresso! 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![Finished!](https://user-images.githubusercontent.com/117388662/239463949-0e90b52f-a5fa-4aed-8ea7-9047154cc213.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![Finished!](https://user-images.githubusercontent.com/117388662/246686394-b0ab3256-57cb-4869-b2dd-51c7778dfa68.png ':size=500')
<!-- tabs:end -->