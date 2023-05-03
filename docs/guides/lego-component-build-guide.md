This is a quick guide on how to best piece together the Gaggiuino mod into the 3D printed housing.
Lots of images are provided to give you a sense of what a completed STM32 component (Lego) build should look like in the box.

[comment]: # (needs new pics and updates to better align with the independent relay and dimmer guide, but is OK-ish for now)

# Preparation 
It is recommended to remove pins on the dimmer and thermocouple interface boards for the smallest, best connection. If you’d prefer to not do this in later steps you can solder wires to the pins and heat shrink over them.
An easy way to remove header pins is to cut the plastic linkage between each pin with snips, then de-solder the pins individually. Solder wick or a solder sucker can help get the through holes nice and clean.

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652146-fc29d237-0d93-42c4-861e-bc928f1411e9.png">

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652214-fc0e0670-4cf7-4ad2-9bcc-ea8c3f1cf3a4.png">

<img height="150" alt="image" src="https://user-images.githubusercontent.com/53577819/211652260-bdcd3e94-a3c6-4831-bf13-34b99d6514b2.png">

# Soldering
## Expansion Board Soldering 
If necessary, solder female headers and screw terminals to the nano expansion board. Make sure the headers and terminals are flush to the board. 

**Bad:**

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652382-dff7fc6f-ac02-494a-a506-9d4a22fbb792.png">

**Acceptable:**

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652433-0c49b699-9370-4639-8b9a-b78eb15b1948.png">

## Arduino Soldering
Solder header pins to the Blackpill. Make sure the plastic linkage is flush with the board when soldering, and make sure all solder joints are properly reflowed. 

**Bad:**

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652496-980a3551-d6f9-44b4-91f7-3b5944996c51.png">

**Acceptable:**

<img width="600" alt="image" src="https://user-images.githubusercontent.com/53577819/211652544-adf88443-8a51-4836-80ee-97c130007bf3.png">

# Crimping 
Crimps are not required, but are recommended for non-soldered component connections such as to the screw terminals on the expansion board, dimmer, and snubber. Make sure they are small enough to go into the screw terminals – 22AWG is possible, but 26AWG is much easier to crimp and fit in the terminals. Do NOT tin (solder) wires that will be crimped or clamped into screw terminals.
## No Crimp Examples
**Bad (exposed wire):**

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653168-26f72fb8-7998-4cea-bebf-a13f37bd55a1.png">

**Bad (stray wire):**

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653201-b4c2b2fb-56f5-4a80-b5f3-3e0ab329d52f.png">

**Acceptable:**

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653247-1101c113-21f4-4796-8fd0-8e62d65841a8.png">

## Crimp Examples
**Acceptable (shielded):**

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653300-d95006c8-3f17-4a3a-8f0d-b682ec9a5066.png">

**Acceptable (unshielded):**

<img width="275" alt="image" src="https://user-images.githubusercontent.com/53577819/211653338-3e47c284-f51a-4ff8-b2f5-3f9db7a5b45a.png">

Make sure unshielded crimped wires are inserted into the terminal such that no bare metal is outside of the terminal housing (red wire: good, black wire: barely acceptable):

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211653388-3bf48014-8de2-40b0-898a-e57918ff4925.png">

# Fit Check
Perform a fit check in the housing of all your components. Make sure the lid closes with no interference.
Note: you can use strip board for power distribution (cut for 6x5 usable points), Wago connectors or soldering wires to each other (provided heat shrink is applied for cover) are also acceptable options.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/53577819/211652610-4b63d97b-90fd-43b1-b37f-a71ad0523008.png">

# Component Wiring 
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

## Screen and SSR

?> Wire lengths were added by request and are the length for a typical install plus a small margin. Verifying wire length in your machine is recommended. 

Measure and cut 400 mm each of 26 gauge Black, Yellow, Blue, and White wires for the screen connection. Cut the DuPont connectors off the screen wires, solder like colors, and cover with heat shrink so you end up with a 600 mm long screen cable. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235807077-38f3fe70-f784-47da-aab0-3d9dbfc4114c.png">

Make sure that the wire colors connecting to the screen line up with the schematic. If necesary, swap connector positions (a small screwdriver can be used to pry up the JST housing tabs holding the crimped connectors in place. They can then be easily removed and swapped).

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235808221-fdfc62a2-9d1f-44fa-b62b-ec041f7fc74f.png">

Solder the power wires to the stripboard and connect the communication wires to the expansion board.

Measure and cut 530 mm of Black wire and 450 mm of Yellow wire for the SSR. Solder to the stripboard and connect to the expansion board per the schematic.  
Once you're done the assembly should look like this.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/235809222-788d1771-ca1f-4924-b9bf-274fd2b487f2.png">

## Snubber
The snubber is not required for operation but should extend the life of the 5v relay and will reduce EMI, allowing you to route wires closer together.

To wire you’ll need to make a pair of jumpers from snubber to relay, with the main wire going out to the solenoid. Reference schematic for wire gauge.

<img width="444" alt="image" src="https://user-images.githubusercontent.com/53577819/211653512-822f7705-2acd-4210-b50f-f497e9b402bc.png">

<img width="488" alt="image" src="https://user-images.githubusercontent.com/53577819/211653613-aeaf786c-b208-4651-a211-cdc3b8263372.png">

The jumper wires get routed under the AC-DC power supply like above. 

# Finish
The assembled housing should look like this (You can chose whether or not to use header pins on the Blackpill for connecting to an ST-Link, but you could also solder wires directly to those connection points). 

<img width="544" alt="image" src="https://user-images.githubusercontent.com/53577819/211653656-a98de6f7-a900-425c-a847-361ea2e19153.png">

Close the housing with 4 screws to complete. 

Things that are not pictured – connections to solid state relay (SSR), touchscreen, scales, thermocouple, steam/brew switches. Please continue the install by referencing the machine-specific schematic and/or install instructions as they may vary.
Here are the labeled component connections to wiring that should be referenced by the machine-specific schematic(s). 

<img width="629" alt="image" src="https://user-images.githubusercontent.com/53577819/211653789-00be52a2-e019-43f2-94af-1c9425beb54b.png">
