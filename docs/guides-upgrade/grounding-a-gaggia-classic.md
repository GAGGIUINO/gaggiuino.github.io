!> If you have a US Gaggia Classic it likely has a 2P socket and is **ungrounded**. It is recommended that espresso machines be grounded and powered through a GFCI/AFCI/RCD device.

Grounding (also known as Earthing) provides an alternate path for current to flow into the ground in the event of an issue with the wiring system or introduction of a conductive medium (such as ionized water).  
Without a grounded housing, if the 120 V line came loose at some point and contacted the housing the machine may still work, but touching the metal housing would be the same as touching a live power socket. With a grounded housing, breaker, and ideally a GFCI/AFCI/RCD device, an AC wiring fault will trip the breaker or circuit interrupter before becoming a danger to people or the system.

!>Earth Ground is **not the same** as 5V GND (aka 0 V, " - ", or 5V COM). LV uses a "floating ground" for thermocouple compatibility. Do not connect the two.

## Bill of Materials

?> As these are US-specific components, many cannot be found on AliExpress or may be no cheaper there than purchasing from Amazon, Digi-Key, Mouser, etc.  
Links are provided, but feel free to shop around.

* C14 3P Panel-Mount Socket for 1.2-1.5 mm panel thickness *(choose **one** that's in-stock)*
    * Schurter [6100.4312](https://www.digikey.com/en/products/detail/schurter-inc/6100-4312/640562) (Digi-Key)
    * Schurter [6100.4315](https://www.digikey.com/en/products/detail/schurter-inc./6100.4315/569906) (Digi-Key)
* 5-15P to C13 Right-Angle Power Cord, 14-16 gauge *(choose **one** that's in-stock)*
    * Qualtek [313010-01](https://www.digikey.com/en/products/detail/qualtek/313010-01/183386)
    * Assmann [A-PC2304-020027-1](https://www.digikey.com/en/products/detail/assmann-wsw-components/A-PC2304-020027-1/3135012)
* 0.4+ m Heat-Resistant Silicone Wire, 16-18 gauge
    * [Green, 18AWG 1m](https://www.aliexpress.com/item/2255800441309579.html)
* *4x 6.3 mm female spade connectors (use spares from main BOM)*

>

# Instructions

## Replace Socket

Remove wires. Make a note of where they started, but also check the schematic. On a number of machines L and N are switched. This doesn't make a difference for stock operation, but it might for Gaggiuino depending on if/how you integrate into the stock wiring harness.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/236963585-40bd561b-2375-4878-adfa-3e8ca4631554.png">

Use wide-jaw or channellock type pliers to squeeze the retaining tabs (shown below) and push on the plug. Alternate between top and bottom pair of retaining tabs with a bit of a wiggle and it should pop out fairly easily.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/236964221-30e21582-5bd8-422b-88eb-d9cb27d7ee52.png">

Install the new socket by pushing into place and making sure all locking tabs are seated

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/236964636-bf53e5ef-53aa-4f0c-ba69-a9c23222c644.png">

>

## Add Grounding Wires

Cut two lengths of ~200 mm wire to go from socket to boiler fuse clip / ground connector and from there to the warming plate connector. Crimp on spade connectors

!> Insulation on pre-insulated spade connectors attached to the boiler will melt. Use un-insulated spade connectors or remove insulation.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/236979713-6508871f-8405-4e0c-b4ed-e7ab59904ad6.png">

Attach the Line, Neutral, and Ground (noted) wires. 

?>Per the Gaggia Classic 120V 2009 schematic, Neutral (Blue) goes to the thermal fuse on top of the boiler and turns to Brown after passing thru the fuse. Line (Gray) goes to the top of the power switch. Colors may change depending on model and time of manufacture.

<img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/237005812-6b360577-e91f-4ba1-a1ca-83480e9c50cf.png">

Grounding is complete!