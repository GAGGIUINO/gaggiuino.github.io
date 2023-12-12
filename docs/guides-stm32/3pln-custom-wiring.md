> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!


# Custom Wiring Considerations

* Consider buying a XH and PH JST kit to make up your own LV connectors instead of using pigtails.
* Know and study difference between HV and LV lines in the schematics.
* PCB v3 can fit into the pump tower where the eco board would be on the 2019+ models (Gaggia Classic Pro, Eco, Evo). 

# Alternate Components

Many stock components are difficult to source so component substitutions have been found and are being tested. Options range from using only stock components (by cutting the original wire harness and splicing them in) to creating a completely new HV wiring harness with alternate components. The list of components is still a work in progress. 

<details>
<summary><b>Alternate Component List </b> <i>(Click to expand)</i></summary>

| Description | Link(s)     | Notes       |
| :---------- | :---------- | :---------- |
| 22-16 Gauge Wire Connector | [BN1.25 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html) <br /> [4 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) | Use for splicing in components (stock or alternate) |
| 16-14 Gauge Wire Connector | [BN2 Bare Crimp](https://www.aliexpress.com/item/3256801144001097.html) <br /> [5 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) | Useful for splicing 1:2 boiler connector wires on 120V machines |
| Boiler Thermal Fuse | [Resettable Thermal Fuse, NC, 185°C, 16 A, M4](https://www.aliexpress.com/item/3256805886376281.html) | Install in the boiler boss where the steam thermostat was|
| Pump Thermal Fuse | [KSD9700 Thermal Switch, 120°C, NC](https://www.aliexpress.com/item/2251832685942790.html) | Retain with hot glue (same method as stock)|
| Boiler Terminal Connectors | [TE 160783-7 (DigiKey)](https://www.digikey.com/en/products/detail/te-connectivity-amp-connectors/160783-7/5157254) or [TE 160783-7 (Mouser)](https://www.mouser.com/ProductDetail/TE-Connectivity-AMP/160783-7?qs=%252BeETdXPI8nLQYJsNGAnPEA%3D%3D) | Stock part, a bit tricky to crimp properly |
| Boiler Terminal Connector Housing | [Boiler Terminal Shroud](https://www.printables.com/model/380256) | Can be purchased from print providers, used if stock covers can't be |
| Boiler Terminal Crimpers | [IWISS IWS-1424A](https://www.aliexpress.com/item/3256805916886076.html) **+ Pliers** or <br /> [TE 160783-7 Crimper HS Jaws](https://www.printables.com/model/673240)| Manufacturer crimpers do not exist. Open barrel crimpers can crimp the wire connection, but the insulation needs to be done with pliers or the TE 160783-7 Crimper HS Jaws|
| Indicator Lamp | [Red 6x13 mm Neon Bulb](https://www.aliexpress.com/item/2261799834780054.html) - pick the voltage range for your machine <br /> [7.9 mm Clear Heat Shrink Tubing](https://www.aliexpress.com/item/3256804355023361.html) - 2 layers over bulb <br /> [4 mm Silicone Heat Shrink Tube](https://www.aliexpress.com/item/3256801522005095.html) - insulate resistor and leads | Using the stock indicators is easier. Only do this if you really don't want to cut the stock harness.
| Indicator Lamp Clips | [Gaggia Classic Pro Neon Lamp Clip](https://www.printables.com/model/647745)     | For Pro/Eco/Evo. There is a version for stock lamps as well as a tighter clip for 6 mm dia neon bulbs (adding thickness with heat shrink tubing not needed)       |
</details>

>

# Custom Wire Harness Schematics

!> As this wiring completely replaces the stock wiring harness it is expected that the reader can complete the wiring using only the schematics. Component builds can use the PCBv3 or HV Only schematics after completing the [Lego Component Build Guide](guides-stm32/lego-component-build-guide.md).

### PCB v3
> #### Gaggia Classic
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GC PCBv3 120v" src="schematics/custom-3pln/GC_wiring_PCBv3_120v.png"> | <img height="300" alt="GC PCBv3 220v" src="schematics/custom-3pln/GC_wiring_PCBv3_220v.png"> |
>
> #### Gaggia Classic Pro
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GCP PCBv3 120v" src="schematics/custom-3pln/GCP_wiring_PCBv3_120v.png"> | <img height="300" alt="GCP PCBv3 220v" src="schematics/custom-3pln/GCP_wiring_PCBv3_220v.png"> |
### PCB v2
> #### Gaggia Classic
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> | <img height="300" alt="GC PCBv2 120v" src="schematics/custom-3pln/GC_wiring_PCBv2_120v.png"> | <img height="300" alt="GC PCBv2 220v" src="schematics/custom-3pln/GC_wiring_PCBv2_220v.png"> |
>
> #### Gaggia Classic Pro
> | 100v - 120v | 220v - 240v |
> | :---------- | :---------- |
> |<img height="300" alt="GCP PCBv2 120v" src="schematics/custom-3pln/GCP_wiring_PCBv2_120v.png"> | <img height="300" alt="GCP PCBv2 220v" src="schematics/custom-3pln/GCP_wiring_PCBv2_220v.png"> |

### HV Only
* [3PLN 120v, GC-specific](https://user-images.githubusercontent.com/53577819/220784232-1b254cd4-d3d7-4fe9-97e5-283fa1fb2659.png)
* [3PLN 120v](https://user-images.githubusercontent.com/53577819/220784237-e2b841e0-4754-4657-98bd-6adb96255aa1.png)
* [3PLN 240v](https://user-images.githubusercontent.com/53577819/220784234-0b370f5b-fd5e-4d0d-9b9d-109ff25d2cbf.png)

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

The pressure transducer comes with a base O-ring, however, the threaded length of the fittings vary and many aren't long enough to seal against the base. Insert the small O-ring into the fitting, adjust flush, then screw on the transducer until it seals on an O-ring.

![Transducer and fittings](https://user-images.githubusercontent.com/117388662/239452187-429dafd7-6844-4256-ae76-b9982dcce86c.png ':size=250')
![Transducer and fittings](https://user-images.githubusercontent.com/117388662/246572048-75f314cb-6585-4351-8c5e-085362841301.png ':size=250')

Cut the tubing in between the pump and boiler, nearer to the boiler but high enough the T is mostly vertical, not horizontal. Attach the appropriate T fitting for your machine. 

> [!Tip]
> Make sure the tubing is fully engaged on the fittings. It can be helpful to use a grip aid such as silicone tape or a rubber glove to grip the tubing and push it in. For barbed fittings you may even need to use some water-based lubricant to get it all the way on.

Cut a 200-250 mm length of your tubing from the BOM and attach it to the pressure transducer fitting. You'll need to fill that length of tubing with water so there are no air bubbles. There are 2 options:

<details>
<summary><b>Hand fill</b> <i>(Click to expand)</i></summary>

Surface tension can make hand filling the tube difficult if you don't use a simple trick: insert a small wire down the center of the tubing and inject water with a syringe. The wire allows the water to flow down and the air to vent up because it doesn't let surface tension seal the tube.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239455051-c8fe0d0a-270e-4685-9478-d751eb746d49.png ':size=250')
</details>

<details>
<summary><b>Machine fill</b> <i>(Click to expand)</i></summary>

Plug the tube into the T fitting. After the screen has been connected and the remainder of the install completed, go to the Brew menu, select the Manual tab, set flow to 1 ml/s and run for ~2 minutes (with open group head) to gently fill the line.

![Filling the transducer tubing](https://user-images.githubusercontent.com/117388662/239618595-844609d1-7b59-456e-afba-2d2b1bf73374.png ':size=250')

</details>

Arrange the connected pressure transducer so that it is at the base of the machine, lower than the T fitting. Ignore wiring in the images as they're from a machine following the stock wiring integration. 

<!-- tabs:start -->
<!-- tab:Gaggia Classic -->
![pressure transducer placement](https://user-images.githubusercontent.com/117388662/239457706-7ee5d101-d209-41b4-a3d3-ce159e98032f.png ':size=500')
<!-- tab:Gaggia Classic Pro -->
![pressure transducer placement](https://user-images.githubusercontent.com/117388662/246573952-ca092066-d107-46e6-85f1-e2a7b19865e0.png ':size=500')
<!-- tabs:end -->

> [!Tip]
> While some sensors/setups seem to have no issues with the pump vibration, others are affected by vibration and even the sensor coming in contact with the housing. In those cases it can be beneficial to wrap the sensor in foam.  
![Foam-wrapped sensor](https://user-images.githubusercontent.com/117388662/239457402-b58dfe55-6572-45b7-8960-2a4d1f9d5753.png ':size=250')

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