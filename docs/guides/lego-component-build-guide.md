This is a quick guide on how to best piece together the Gaggiuino mod into the 3D printed housing.
Lots of images are provided to give you a sense of what a completed STM32 component (Lego) build should look like in the box.

## General Install Principles

<details>
<summary><b>Component prep</b> <i>(Click to expand)</i></summary>

It is recommended to remove pins on the dimmer and thermocouple interface boards for the smallest, best connection. If you’d prefer to not do this in later steps you can solder wires to the pins and heat shrink over them.
An easy way to remove header pins is to cut the plastic linkage between each pin with snips, then de-solder the pins individually. Solder wick or a solder sucker can help get the through holes nice and clean.

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652146-fc29d237-0d93-42c4-861e-bc928f1411e9.png">

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652214-fc0e0670-4cf7-4ad2-9bcc-ea8c3f1cf3a4.png">

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652260-bdcd3e94-a3c6-4831-bf13-34b99d6514b2.png">

</details>

<details>
<summary><b>Soldering</b> <i>(Click to expand)</i></summary>

?> Additional information can be found in [Soldering Recommendations](/docs/learning/learning-sources.md/#soldering)

**Expansion Board Soldering** 

If necessary, solder female headers and screw terminals to the nano expansion board. Make sure the headers and terminals are flush to the board. 

Bad:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652382-dff7fc6f-ac02-494a-a506-9d4a22fbb792.png">

Acceptable:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652433-0c49b699-9370-4639-8b9a-b78eb15b1948.png">

**STM32 Soldering**
Solder header pins to the Blackpill. Make sure the plastic linkage is flush with the board when soldering, and make sure all solder joints are properly reflowed. 

Bad:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652496-980a3551-d6f9-44b4-91f7-3b5944996c51.png">

Acceptable:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652544-adf88443-8a51-4836-80ee-97c130007bf3.png">

</details>

<details>
<summary><b>Crimping</b> <i>(Click to expand)</i></summary>

Crimps are not required within the housing, but are a good idea for non-soldered component connections such as to the screw terminals on the expansion board, dimmer, and snubber to avoid stray wires. Make sure they are small enough to go into the screw terminals – 22AWG is possible, but 24-26AWG is much easier to crimp and fit in the terminals. 

!>Do **not** tin (solder) wires that will be crimped or clamped into screw terminals.

**No Crimp Examples**
Bad (exposed wire):

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653168-26f72fb8-7998-4cea-bebf-a13f37bd55a1.png">

Bad (stray wire):

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653201-b4c2b2fb-56f5-4a80-b5f3-3e0ab329d52f.png">

Acceptable:

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653247-1101c113-21f4-4796-8fd0-8e62d65841a8.png">

**Crimp Examples**
Acceptable (shielded):

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653300-d95006c8-3f17-4a3a-8f0d-b682ec9a5066.png">

Acceptable (unshielded):

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653338-3e47c284-f51a-4ff8-b2f5-3f9db7a5b45a.png">

Make sure unshielded crimped wires are inserted into the terminal such that no bare metal is outside of the terminal housing (red wire: good, black wire: barely acceptable):

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653388-3bf48014-8de2-40b0-898a-e57918ff4925.png">

**Crimping Outside of the Housing**

6.3 mm spade connectors are used for integration (connecting the assembled housing to the espresso machine). Molex's [TBO-Quality Crimp Handbook](https://github.com/Loogl3/gaggiuino.github.io/files/11400156/tbo.quality.crimp.handbook.pdf) is an excellent resource. Sections 6 and 7 contain information that applies to most crimped connections.

</details>

>

# Fit Check
Perform a fit check in the housing of all your components. Make sure the lid closes with no interference.
Note: you can use strip board for power distribution (cut for 6x5 usable points), Wago connectors or soldering wires to each other (provided heat shrink is applied for cover) are also acceptable options.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211652610-4b63d97b-90fd-43b1-b37f-a71ad0523008.png">

>

# Wire lengths

!> Wire cut lengths to connect the housing components to the espresso machine were added by request and are the length for a typical install in a GC or GCP plus a small margin.  
**Verifying wire length in your machine is recommended.** 

Component                                      |Colors                  |Gauge|Length                        
-----------------------------------------------|------------------------|:---:|------------------------------
[Screen](#screen)                              |Black, Yellow, Blue, Red|26   |400 mm *(600 mm if crimping JST)*
[SSR](#ssr)                                    |Black                   |22   |530 mm
[SSR](#ssr)                                    |Yellow                  |22   |450 mm
[Switches](#switches)                          |Black, Yellow, Blue     |22   |600 mm
*Switch Jumper*                                |*Black*                 |*22* |*50 mm (used during machine install)*
[PSU](#psu)                                    |Black, White            |22   |600 mm
[Snubber-Relay](#snubber-relay-and-dimmer)     |Black, Red              |22   |100 mm
[Relay-Dimmer](#snubber-relay-and-dimmer)      |Black                   |22   |50 mm
[Relay (NO)](#snubber-relay-and-dimmer)        |Red                     |22   |600 mm
[Dimmer (Out, N-In)](#snubber-relay-and-dimmer)|Red, White              |22   |250 mm
[Dimmer (L-In)](#snubber-relay-and-dimmer)     |Black                   |22   |600 mm

>

# LV Wiring 
The next steps describe the process of wiring the components together. You can do the power wiring first, then follow it up with the component signal wiring, but it can be done in whatever order you like. Trust the schematic if you’re confused on a step or there appears to be a difference between an image and the schematic. You can use 22-26AWG wires for LV wiring unless otherwise noted; see the schematic for permissible wire gauges.

<img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235083835-fa2b6721-598c-4fca-9ac7-eb23a2aa596b.png">

[STM32 Internal Comp Housing Schematic](https://user-images.githubusercontent.com/117388662/235083835-fa2b6721-598c-4fca-9ac7-eb23a2aa596b.png)

## Power wiring 
If using a strip board it is recommended to use an arrangement like this with two rows of 5V and two rows of 5V GND (0 VDC). 
Have the wires from the PSU go in through from the top, then fold over underneath and solder to connect the 2 rails.

<img width="250" alt="image" src="https://user-images.githubusercontent.com/53577819/211652856-028d0570-1736-4715-b6be-a3efb7325813.png">

<img width="250" alt="image" src="https://user-images.githubusercontent.com/53577819/211652920-b17579ce-f9d9-4be0-991a-668df15f95a4.png">

Measure distance to components in the housing, cut wires to length plus ~1 cm, then solder. 

!> Do not solder in the housing, it will melt. A “helping hand tool” or soldering vice is very helpful.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653005-8bffe9c8-1967-461d-a163-9a130534e0d0.png">

Now that power wires have been added we’ll begin adding signal wires per the schematic. Just like with the power wires, measure length in the housing, then remove from housing to solder. A few notes:
1. Make sure to route the wires before measuring. There is not enough clearance for wires to go over the Blackpill, they must go around. 
2. Up to you whether you cut the pressure transducer cable shorter. Option to cut it down to about 12 in / 30 cm for my GC, but you may want it longer depending on your specific machine. 

Here’s a pic partway through the wiring process:

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653439-4aa95ae9-e234-406e-a38d-0b3cdf2a377a.png">

## ADS Board
Here are a few details on wiring the ADS:
Connect G to ADDR like this (there’s clearance in the housing for this):

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653056-184db336-120e-49d9-95d9-84c5103c3227.png">

Wiring the pull-up 5V to A1, A2, and A3 is optional, but easy. Just make sure that you have extra wire length to push through, bend over, and solder as shown (upper left):

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653104-486b571e-866d-4e5a-95c6-88f0271e25e3.png">

## Screen

[Measure and cut](#wire-lengths) wires for the screen connection. Cut the DuPont connectors off the JST-XH pigtail included with the screen, solder like colors, and cover with heat shrink so you end up with a 600 mm long screen cable. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235807077-38f3fe70-f784-47da-aab0-3d9dbfc4114c.png">

Make sure that the wire colors connecting to the screen line up with the schematic. If necesary, swap connector positions to correct. A small screwdriver can be used to release the tabs holding the pins in place. They can then be easily removed and swapped.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235808221-fdfc62a2-9d1f-44fa-b62b-ec041f7fc74f.png">

?> The pins will need to be removed from the connector to pass the wires through the back vent slot - ensuring the wire colors line up before testing makes that process much simpler.

Solder the power wires to the stripboard and connect the communication wires to the expansion board per the schematic.

## SSR

[Measure and cut](#wire-lengths) the wires for the SSR. Solder to the stripboard and connect to the expansion board per the schematic.  
Once you're done the assembly should look like this.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236147555-e463242b-1aa4-4639-8efb-f789e5074b9b.png">

## Switches

[Measure and cut](#wire-lengths) the wires for the switch connections. Solder to the stripboard and connect to the expansion board per the schematic.  
Once you're done the assembly should look like this.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236129109-bfbb6880-8942-4009-a386-3d2be94ca1c1.png">

## Programming/Flashing

!> Do not flash the Blackpill while powering the system over USB-C.  

Flash the Blackpill using the ST-Link (connect SWDIO, GND, SWCLK, and 3.3V* - see [Prerequisites](prereq/prerequisites.md) for details). 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235833233-5d8d99d3-665a-40d2-b215-489295c49480.png">

Flash the Nextion with the applicable nextion-*-lcd.tft on an otherwise-empty ≤32 GB FAT32 microSD card.  

Power for flashing the Nextion may be provided through the USB-C port on the Blackpill so long as you are using a USB power adapter that will supply 4.6-5.2 VDC (don't use a battery bank or your PC USB ports for power).  

?> More stable voltage can be provided by using the 120 VAC PSU and piggybacking off of the Gaggia power switch ([example here](https://user-images.githubusercontent.com/117388662/235836724-71394491-c47a-46ed-920b-79ced184cc16.png)), however this is unnecessary for flashing and testing at this point so long as the voltage provided through the USB-C port is in range.  
*If you wish to power the system through the 120 VAC PSU to flash the Blackpill then do **not** connect 3.3V to the ST-Link.

Wait for the Nextion to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236127637-fb83e05e-06d0-4a2f-b6e8-cdf48a36a077.png">

## Component test

Connect the thermocouple to the terminals and power on the system once again. If all is successful you should:
- see a build number during boot (good Blackpill-Nextion communication)
- hear the relay click for boiler fill
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target (if you do then there's a short to ground, likely through the expansion board)

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236076956-36ab8d35-6b5d-476e-84d2-d2e5097fafb1.png">

>

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236077124-e318b230-908e-4715-8810-a819f260c04f.png">

Recommendation: zip-tie the cable strain relief at this point so the risk of stressing the connections in the housing is reduced. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236130002-977f47b6-c742-4f66-b240-15cbd5664a7d.png">

>

# HV Wiring

?>The images in this section have the LV wire connections moved out of the shot and the thermocouple disconnected for a cleaner view of the HV wiring.

## PSU

[Measure and cut](#wire-lengths) the wires for the PSU and solder to the AC in landings. Note that "polarity" does not matter. This is the last bit of soldering for the housing!

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/236347733-2f0f105d-1157-420e-84b4-ec7f2b0efe0a.png">

## Snubber, Relay, and Dimmer

[Measure and cut](#wire-lengths) the wires for the snubber-relay, relay-dimmer, relay, and dimmer connections. 

The snubber wires get routed in the channel under the PSU

<img width="488" alt="image" src="https://user-images.githubusercontent.com/117388662/236350069-ad339311-676a-4514-84a8-7bc9b3dcb4bd.png">

And here is the full set of housing HV wires for interfacing with the power switch, 3-way solenoid valve, and pump.

<img width="488" alt="image" src="https://user-images.githubusercontent.com/117388662/236350229-e6ad120d-48e7-45de-b25b-249352784fca.png">

# Final Steps

To connect the ST-Link to the Blackpill (for flashing without opening the housing or machine) this is one of the few times in the project where DuPont connectors may be used. Another option is to solder the wires directly to the Blackpill. 

?> If you wish to power the system through the 120 VAC PSU (powering on the espresso machine) to flash the Blackpill then do **not** connect 3.3V to the ST-Link.

Close the housing with 4 screws to complete. 

Optional wiring that is not pictured:
- HW Scales
- ToFnLED

!>Please continue the install by referencing the machine-specific schematics and/or install instructions as they may vary.