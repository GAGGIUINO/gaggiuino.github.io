This assembly is for adding hardware scales to your Gaggia Classic or Gaggia Classic Pro. 

## Bill of Materials

## Components

There are two options for HX711 boards - buying two HX711 boards from AliExpress or using the dualScaleBoard

* M3 Flat head screws
    * [**2** M3x5 mm nickel plated steel](https://www.aliexpress.com/item/3256803315929210.html) *(must be magnetic)*  
    * [**6** M3x5 mm and **4** M3x4 mm stainless steel](https://www.aliexpress.com/item/2251832760640149.html)
* **2** thread-rolling/self-tapping screws for plastic *(pick one)*
    * [M3x6mm self-tapping screws for plastic](https://www.aliexpress.com/item/3256802230982244.html)
    * #4-20x1/4" thread rolling screws *(local USA option)*
    * M2.9x6.5mm self-tapping screws for plastic *(local EU option)*
* **20** (GC) or **36** (GCP) [disc magnets, 5 mm dia. x 2 mm ht.](https://www.aliexpress.com/item/3256803930463196.html)  
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
* [**1** dualScaleBoard](https://github.com/banoz/dualScaleBoard_HX711)
<!-- tabs:end -->

## 3D-Printed Parts

Print files are available on [Printables](https://www.printables.com/model/285370) or can be ordered from official print providers

* **1** Scales base assembly 
* **1** Drip tray or adapter combo *(choose based on your system)*
    * GC Drip Tray: GC Drip Tray Adapter and 4 Drip Tray Spacers
    * Low-Profile Drip Tray: LP Drip Tray Adapter and 4 Drip Tray Spacers  
        *Note: designed for BaristaGadgets and Shades of Coffee low profile trays*
    * GCP Drip Tray: GCP Drip Tray Adapter (L and R) and 2 GCP Drip Tray Adapter Clamps
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

    If your magnet holes are undersized, brush over the edge with a hobby knife to slightly widen the hole, then partially insert the magnet manually. Press down on a flat surface to seat flush.

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257019766-5bf71df5-d363-4e2c-8d49-f4f217209356.png">  

    <img width="600" alt="image" src="https://user-images.githubusercontent.com/117388662/257019800-ee2aac69-5ea5-421d-86a6-8499613f4875.png">

