The Time of Flight and LED (ToFnLED) board provides a sensor for determining tank water level and and LED for tank lighting. 

<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/256652023-fb3ead35-419b-4859-96b7-1cfbb1b0e9b8.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/256652465-c6fe4def-9d61-43f8-9b23-339bb7d53b8b.png">

## Bill of Materials

> [!Note] Understanding of the PCB ordering/manufacturing process is needed to order the ToFnLED. For housing compatibility do **not** add the backside connector.  
Conformal coating the PCB is highly recommended for longevity. This can be done as part of the PCB assembly process or manually post-assembly.

<!-- tabs:start -->
<!-- tab:PCB -->
* ToFnLED (two options due to LED controller availability - choose one)
    * [NCP5623](https://www.pcbway.com/project/shareproject/ToFnLED_v1_214578da.html)
    * [PCA9632](https://www.pcbway.com/project/shareproject/ToFnLED_RGBW_1a918f23.html)
* I2C Qwiic cable, 250+ mm (choose one)
    * [(Digi-Key) JST JUMPER 04SR-3S - 04SR-3S 10 A04SR04SR30K254A](https://www.digikey.com/en/products/detail/jst-sales-america-inc/A04SR04SR30K254A/9922185)
    * [(AliExpress) 10 PCS 30CM JST SH 1.0 Female Double Connector, 4P, Same Direction](https://www.aliexpress.com/item/3256804651494821.html)
* 3D-Printed Housing, available on [Printables](https://www.printables.com/model/502813) or can be ordered from official print providers
    * [(2 disc magnets, 5 mm dia. x 1 mm ht. (for magnetic espresso machine)](https://www.aliexpress.com/item/3256801641477250.html)
    * Cyanoacrylate / super glue (for magnetic espresso machine)
    * Double-sided tape, long-term temp rating of at least 80° C  (for non-magnetic espresso machine)
        * VHB 4611/5952/4910, Gorilla Tape, Alien Tape are options

<!-- tab:LEGO -->
* ToFnLED (two options due to LED controller availability - choose one)
    * [NCP5623](https://www.pcbway.com/project/shareproject/ToFnLED_v1_214578da.html)
    * [PCA9632](https://www.pcbway.com/project/shareproject/ToFnLED_RGBW_1a918f23.html)
* I2C Qwiic cable, 250+ mm (choose one)
    * [(Digi-Key) JST JUMPER 04SR-3S - 04SR-3S 10 A04SR04SR30K254A](https://www.digikey.com/en/products/detail/jst-sales-america-inc/A04SR04SR30K254A/9922185)
    * [(AliExpress) 10 PCS 30CM JST SH 1.0 Female Double Connector, 4P, Same Direction](https://www.aliexpress.com/item/3256804651494821.html)
* [2 Channel IIC I2C Logic Level Converter](https://www.aliexpress.com/item/2251832426051878.html)
* [12 mm diameter heat shrink tubing](https://www.aliexpress.com/item/3256804353582834.html)
* 3D-Printed Housing, available on [Printables](https://www.printables.com/model/502813) or can be ordered from official print providers
    * [2 disc magnets, 5 mm dia. x 1 mm ht. (for magnetic espresso machine)](https://www.aliexpress.com/item/3256801641477250.html)
    * Double-sided tape, long-term temp rating of at least 80° C  (for non-magnetic espresso machine)
    * Cyanoacrylate (super glue)
<!-- tabs:end -->

For tubing consolidation (optional):

* [6 mm barb T-type fitting](https://www.aliexpress.com/item/3256805112468750.html)

>

# Housing Assembly

Scratch up the housing magnet indentations a bit with a craft blade to improve adhesion before adding a drop of cyanoacrylate and placing a magnet on top. Make sure the magnets seat flat!

<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/256454738-f7717135-2389-451c-b2c9-9439c2159eee.png">


# Connections
<!-- tabs:start -->
<!-- tab:PCB -->
Plug the Qwiic cable into the J2 Qwiic I2C socket on the PCB

<!-- tab:LEGO -->
Cut off one Qwiic connector from the cable and solder it and the wires back to the component enclosure to the level shifter and LDO board, following the schematic. 

<img width="600" alt="image" src="schematics/stm32-comp-build.png">

Once soldered cover with heat shrink tubing. 

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256456847-fcb44efb-4e87-4b8b-b4f2-4a47d036ccf5.png">
<!-- tabs:end -->

Run the Qwiic cable down through the gap on the right side of the machine sheet metal, plug it into the ToFnLED board, insert the board into the housing, and mount above the water tank. 

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256464601-0d54fd7a-0f65-495e-8169-83fe9bd14a53.png">

# Extra Defines

The ToF and LED elements need to be enabled in the code. To do so, create a file in the project folder called "extra_defines.ini"  
The exact contents of the file depend on your system build, but it will look something like this (green lines are commented out and inactive). 

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256468372-14e57794-6ded-4bc1-a641-921cd4c6ca58.png">

> 

> [!WARNING] Adding build flags that do not apply to your system hardware configuration may cause it to not work or behave unexpectedly.

Here is an example of an extra_defines file for a system with the NCP5623 version of the ToFnLED board with no other defines.

```
[extra]
build_flags =
    ; -DLED_PCA9632
    -DLED_NCP5623
    -DTOF_VL53L0X
```

# Tubing Consolidation (Optional)

The intake and OPV tubes can be combined above the water tank using a T fitting. This reduces water agitation in the tank during pumping and hides the OPV tube.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256653622-6f84ea94-ee0c-4dbe-aae4-88dc015f8d03.png">

The intake tube should be ~175 mm long. Cut to ~190 mm, then trim as needed. Make sure to cut the end into a very shallow "V" shape so that it can't get suctioned to the bottom of the tank.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256655744-be96feb6-40d0-4f12-91cb-79502fb5027e.png">

After completing installation:
* Flush water with an open group head to prime the pump.  
* With a blank portafilter basket in, Flush and let it run through the backflush/pressure release cycle a few times to cycle water through the OPV tubing.  
* Remove blank portafilter and run Flush one more time with open group head to make sure any air from the OPV line is pushed through.
