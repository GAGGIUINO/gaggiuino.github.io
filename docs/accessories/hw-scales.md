This assembly is for adding hardware scales to your Gaggia Classic or Gaggia Classic Pro.  

> [!Tip] The STM32 build has software emulated **predictive scales** that try to offer accurate sensing of the first drops into the cup as well as realtime shot weight tracking and stop-on-weight across a variety of settings and shot profiles. Predictive scales are sufficient for most users with performed calibration and standard dialed-in shots but they're not fool proof or able to cater for the more advanced minds out there.  
If extreme experimentation with beans, grinds, or shot profiles is your fetish it's advised to use HW scales instead.

> [!WARNING] This is an advanced installation step that requires accurate 3D-printed parts and good installation practices to achieve optimal results.

# Bill of Materials

## Components

There are two options for HX711 boards - buying two HX711 boards from AliExpress or using the dualScaleBoard

* M3 Flat head screws
    * [**2** M3x5 mm nickel plated steel](https://www.aliexpress.com/item/3256803315929210.html) *(must be magnetic)*  
    * [**6** M3x5 mm and **4** M3x4 mm stainless steel](https://www.aliexpress.com/item/2251832760640149.html)
* **2** thread-rolling/self-tapping screws for plastic *(pick one)*
    * [M3x6mm self-tapping screws for plastic](https://www.aliexpress.com/item/3256802230982244.html)
    * #4-20x1/4" thread rolling screws *(local USA option)*
    * M2.9x6.5mm self-tapping screws for plastic *(local EU option)*
* **20** [disc magnets, 5 mm dia. x 2 mm ht.](https://www.aliexpress.com/item/3256803930463196.html)  
    *Most machine housings are magnetic - subtract 12 magnets if yours is not. The scales will still work but won't be held as securely.*
* Gap-filling cyanoacrylate (super glue)
* [**2+** 750 g load cells](https://www.aliexpress.com/item/2251832483911236.html)  
    *Buying 3-4 load cells is recommended as QC isn't great and they may need modifications that can result in damage if done improperly*
* [**1 row** 2.54 mm right angle (reverse bending) header pins](https://www.aliexpress.com/item/2255800474074961.html) (only need 5 pins)
* [**1** 5P JST XH or DuPont connector](https://www.aliexpress.com/item/2255799940249067.html)
* [**1** Stripboard/protoboard](https://www.aliexpress.com/item/3256801470993306.html) (only need a small piece)
* [Heat-resistant Silicone Wire](https://www.aliexpress.com/item/2255800441309579.html)
    * **26AWG - 5m**: Black, Red, Yellow, Blue

<!-- tabs:start -->
<!-- tab:2 HX711 -->
* [**2** HX711 interface board](https://www.aliexpress.com/item/2251832855509243.html)
* [**1** 1KΩ resistor](https://www.aliexpress.com/item/3256802484566250.html)
<!-- tab:dualScaleBoard -->
* [**1** dualScaleBoard](https://www.pcbway.com/project/shareproject/Dula_HX711_scales_board_17abe179.html)
<!-- tabs:end -->

## 3D-Printed Parts

Print files are available on [Printables](https://www.printables.com/model/285370) or can be ordered from official print providers

* **1** Scales base assembly 
* **1** Drip tray or adapter combo *(choose based on your system)*
    * GC Drip Tray: GC Drip Tray Adapter and 4 Drip Tray Spacers
    * Low-Profile Drip Tray: LP Drip Tray Adapter and 4 Drip Tray Spacers  
        *Note: designed for BaristaGadgets and Shades of Coffee low profile trays*
    * GCP Drip Tray: GCP Drip Tray Adapter (L and R)
    * 3D Print DripTray (no other adapters needed)

# Assembly

1. The load cells are often covered with adhesive in places it shouldn't be. Use a sharp razor blade and cut the adhesive away from the screw holes, being careful to not cut a wire or cut into the load sensing area.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964354-bca6c07c-4a85-4b3a-b499-7e2b3032d524.png">

2. Fit-up the load cells into the load cell housings, re-trimming adhesive if necessary. Use the 5 mm screws on the top to attach to the load cell to the housing and the 4 mm screws on the bottom to attach the flex limiter to the load cell. Attach the load plate using one magnetic screw and one nonmagnetic screw as noted and make sure there's a gap all the way around it.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964444-025e6320-b85b-433e-99ba-829ea5907b91.png">

3. Cut the stripboard to size and cut off a group of 5 right angle pins

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964557-82f40003-01e6-4ca1-90a1-17889fbb587d.png">

4. Do a quick fit-check with the base assembly. Note that the load cell housings are designed to be slightly loose so that parallelism issues in the sheet metal don't affect them. Slide the PCB retainer to check that the boards lock in.

    <!-- tabs:start -->
    <!-- tab:2 HX711 -->
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964641-3acbc0d1-9491-4017-852f-5f5b65086ada.png">
    <!-- tab:dualScaleBoard -->
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964653-13ea4859-a5e9-4153-9c0a-796def530f7f.png">
    <!-- tabs:end -->

5. Cut the load cell wires as shown (this provides extra for strain relief) and **save what you cut off**

    <!-- tabs:start -->
    <!-- tab:2 HX711 -->
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964791-0b282d78-d4fb-4158-b2d2-5aa005f3e443.png">
    <!-- tab:dualScaleBoard -->
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964801-62946762-2394-4d70-b601-50f07f1cff0c.png">

    Also cut the dualScaleBoard JP11 jumper
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256964853-8b8c8c03-a83c-412a-989c-739abae6975f.png">
    <!-- tabs:end -->

6. Solder the stripboard

    <!-- tabs:start -->
    <!-- tab:2 HX711 -->
    Solder the leftover wires, 1kOhm resistor (SCK pull-up), and header pins to the stripboard as shown. Fit the stripboard back into the housing after soldering, measure wire lengths to the HX711 boards (with extra strain relief) and cut to length. If necessary, trim backside wire tails so that the board fits in the housing.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256965255-349887f1-3a25-4361-afe1-ce5cc0e097ed.png">
    <!-- tab:dualScaleBoard -->
    Solder the leftover wires and header pins to the stripboard as shown. Fit the stripboard back into the housing after soldering, measure wire lengths to the dualScaleBoard (with extra strain relief) and cut to length. If necessary, trim backside wire tails so that the board fits in the housing.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256965268-d3bca727-c90e-4faa-89db-13a807ecbcbb.png">  

    > [!Note] It's fine to make the stripboard wire order line up with the DualScaleBoard. I chose not to do so because I wanted my scale builds to be interchangeable. 
    <!-- tabs:end -->

7. Now that wires are all cut to length, remove the boards from the housing and solder (don't solder in the housing, it will melt). It should look like this when complete: 

    <!-- tabs:start -->
    <!-- tab:2 HX711 -->
    <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/256965397-bbc54472-f866-404d-9053-0e4850e43377.png">
    <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/256965387-c217fc32-4cf8-4c89-8a9e-5b96efc188a2.png">

    > [!Note] The green HX711 boards have been replaced by the purple ones. The housing is compatible with both, however, the green boards are missing a ground plane tie between E- and GND. Soldering a 30 gauge jumper wire from E- to GND will improve stability of the green boards. 
    <!-- tab:dualScaleBoard -->
    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/256965408-cd9db3f8-4bd6-4746-b915-601de9a9ec4a.png">
    <!-- tabs:end -->

    At this point you can attach the center housing cover (slides on from the front) and screw it down with the 2 thread-rolling/self-tapping screws.

8. Install magnets in load plates, load cell housings, and drip tray or drip tray adapter parts using the gap-filling cyanoacrylate. Make sure to match the polarity of magnets on the drip tray or drip tray adapter to those on the load plate so that it snaps in place. Holes are sized to only have 0.25 mm extra depth, so if a hole looks like it could fit another magnet put another one in.  

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257019766-5bf71df5-d363-4e2c-8d49-f4f217209356.png">  

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/267487785-489c145c-5008-4d74-95f0-762e8f978df6.png">

    If your magnet holes are too tight, brush over the edge with a hobby knife to slightly widen the hole, then partially insert the magnet manually. Press down on a flat surface to seat flush.

    If your magnet holes are loose and you want the magnets perfectly flush use a metal ruler with a parchment paper barrier to hold the magnets flush while the glue sets. 

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/267475094-bec78ce0-a85b-4c68-b675-d05f1388fabc.png">  
    
    <details>
    <summary><b>Old GCP Drip Tray Adapter tip</b> <i>(Click to expand)</i></summary>

    If you're using the old GCP Drip Tray Adapters and Clamps it's easier if you install magnets in the order shown below. Otherwise, the bottom magnets can spin the internal side-facing magnets as you try to install.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257087212-fe5873c9-405e-4221-abfb-d696fab30ff1.png">

    </details>

9. Prep drip tray and/or adapters

    <!-- tabs:start -->
    <!-- tab:GCP Drip Tray Adapter -->
    Cut the sides of the drip tray as seen below (thick red line) and remove scrap (red X area). This provides clearance to the load cell housings. 

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257088268-c1ab40c7-4c69-4b48-a10c-3b890e8cc97b.png">

    A good way to cleanly cut the profile is to sketch on masking tape, make a pilot hole, use a step drill bit for a 5 mm radius (10 mm diameter), cut with a blade or saw, and then finish with a hobby knife and file.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257088426-229b8358-d270-4efa-bc71-25f75c4685e1.png">

    Slide the drip tray adapters onto the drip tray side fins. The adapters are labeled F (front) and L (left) or R (right), left/right orientation as if facing the espresso machine. Make sure the adapters are fully seated on the underside of the tray's top surface.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/267475732-14dbea6c-ff72-45ff-959c-9a5ef89ce215.png">
    <!-- tab:GC/LP Drip Tray Adapter -->
    Fully insert the drip tray spacers into the Gaggia Classic or Low Profile drip tray adapter with the flat surface down. If the fit is not snug use a drop of cyanoacrylate to hold each spacer in place. 

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257087801-911f627f-ac5b-4011-802c-8ee73655e872.png">
    <!-- tabs:end -->

10. Wire a 5P JST XH or DuPont connector (I used JST XH with the latching features cut off because it'll only fit one way with enough clearance to install under the machine) and route through the housing back to wherever your controller is. Protect the areas where it goes through the housing with heat shrink tubing and ensure the wires don't affect placement of the water tank so much that it rubs the drip tray.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257089366-23a5f80e-7147-4194-ba84-740927286400.png">

11. Place the assembly into the machine and check fit. Things to verify:
    * Load cell housings are parallel to each other and the Gaggia housing sides

        <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257089574-2004216e-7231-4c33-b8eb-ff90b93f4dfa.png">
    
    * Drip tray or drip tray adapter snaps into place magnetically and fits with even gaps around it, not touching Gaggia housing sides or water tank

        <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257089656-57ecccf3-1225-4ff7-a387-01ace2999414.png">

    * Drip tray has at least 0.5 mm clearance under the front lip and on the sides

        <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257089747-74fd447d-a299-4d65-a408-b325f09ec326.png">

# Flashing/Calibration

1. Build and flash the scales calibration task

<!-- tabs:start -->
<!-- tab:2 HX711 -->
Use the appropriate scales-calibration task to upload to the STM32 and copy scales-calibrate TFT onto a microSD card to flash the Nextion. You should see this show up on the screen (with numbers). If there are no numbers your Screen-Blackpill connection is likely bad.

<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257109779-2888a68b-7131-4243-824b-c43cc3ac4b8c.png">

<!-- tab:dualScaleBoard -->
Before building in Platformio, create an “extra_defines.ini” file (if one doesn't already exist) with these contents in the project root:

```
[extra]
build_flags =
    -DSINGLE_HX711_BOARD
```

Use the appropriate scales-calibration task to upload to the STM32 and copy scales-calibrate TFT onto a microSD card to flash the Nextion. You should see this show up on the screen (with numbers). If there are no numbers your screen-STM32 connection is likely bad.

<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257109779-2888a68b-7131-4243-824b-c43cc3ac4b8c.png">

<!-- tabs:end -->

2. Remove the load plates and insert the calibration load plate to space the load away from the load cell housing (otherwise the housing will take some of the load). I prefer to detach the load cell housing from the center housing as shown to get more room to fit the calibration weight (in this case a 318.5 g tamper). Ideal calibration weight is in the 200-400g range.

    <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257110291-ae8bf438-a692-4b89-b511-8ef8073f1065.png">

    To calibrate, use the adjustment value and +/- buttons to adjust the scale factors until the weight output in grams matches the real weight. One scale factor will likely be negative to make the output in grams positive. Take a pic or copy down the scale factors.

3. Once calibrated, flash the regular build back onto the screen and STM32. Copy the scale factors into the LC1 and LC2 Factors and click Save.

    <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257110664-fd0f6aa1-aefe-4a6d-b167-12183f9d1b87.png">

4. Add the drip tray / drip tray adapter. Congrats, your machine has a scale!

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257110758-a6eae8c8-c12e-41eb-bfa3-586ae03dd88a.png">

> [!TIP] If using the stock GC or GCP drip trays you may want to file or cut 2 mm off of the pressure outlet tube (solenoid vent) to bring it to 130 mm and make drip tray removal easier.  
You'll find that you might not be able to easily reach under the stock drip tray to remove it - I find holding it like this to lift over the retaining lip and pull it forward slightly works well. 
<img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/257110983-c41210d7-dbb4-4666-bb82-2f0b789a50ad.png">

# Troubleshooting

If you have “jumpy” scales or are struggling to calibrate, check that
* magnets are installed flush or sub-flush
* the bottom surface of all parts resting on the machine sheet metal is flat and free of dirt, dried adhesive, print artifacts, etc. 
* the load cell adhesive is not clamped by the load cell housings or flex limiters (see step 1). Adhesive on the side of the load cell before the cutout area is fine.
* the load plates have clearance to the load cell housings all the way around
* wires are not routed by high voltage
