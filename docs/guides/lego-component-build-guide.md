# Gaggiuino Component Housing Build Guide

I recommend removing pins on the dimmer and thermocouple interface boards for the smallest, best connection. If you’d prefer to not do this in later steps you can solder wires to the pins and heat shrink over them.
An easy way to remove header pins is to cut the plastic linkage between each pin with snips, then de-solder the pins individually. Solder wick or a solder sucker can help get the thru holes nice and clean.



If necessary, solder female headers and screw terminals to the nano expansion board. Make sure the headers and terminals are flush to the board. 
Bad

Acceptable

Solder header pins to the Blackpill. Make sure the plastic linkage is flush with the board when soldering, and make sure all solder joints are properly reflowed. 
Bad

Acceptable

Perform a fit-check in the housing of all your components. Make sure the lid closes with no interference.
Note: I’m using a stripboard for power distribution (cut for 6x5 usable points). Wago connectors or soldering wires to each other are also acceptable options.

The next steps describe the process of wiring the components together. I chose to do the power wiring first, then follow it up with the component signal wiring, but it can be done in whatever order you like. Trust the schematic if you’re confused on a step or there appears to be a difference between an image and the schematic. I used 22 gauge wires unless otherwise noted; see the schematic for permissible wire gauges.

Power wiring. If using a stripboard I recommend an arrangement like this with two rows of 5V and two rows of 5V GND (0 VDC). 
Have the wires from the PSU go in thru from the top, then fold over underneath and solder to connect the 2 rails.

Measure distance to components in the housing, cut wires to length plus ~1 cm, then solder. Do not solder in the housing, it will melt. A “helping hand tool” or soldering vice is very helpful.

Here are a few details on wiring the ADS:
I connected G to ADDR like this (there’s clearance in the housing for this)

Wiring the pull-up 5V to A1, A2, and A3 is optional, but easy. Just make sure that you have extra wire length to push through, bend over, and solder as shown (upper left)

Crimps are not required, but are recommended for non-soldered component connections such as to the screw terminals on the expansion board, dimmer, and snubber. Make sure they are small enough to go into the screw terminals – 22 gauge is possible, but 24 gauge is much easier to crimp and fit in the terminals. Do NOT tin (solder) wires that will be crimped or clamped into screw terminals.
No crimp examples
Bad (exposed wire)

Bad (stray wire) 

Acceptable

Crimp examples
Acceptable (shielded)

Acceptable (unshielded)

Make sure unshielded crimped wires are inserted into the terminal such that no bare metal is outside of the terminal housing (red wire: good, black wire: barely acceptable)

Now that power wires have been added I’ll begin adding signal wires per the schematic. Just like with the power wires, measure length in the housing, then remove from housing to solder. A few notes:
Make sure to route the wires before measuring. There is not enough clearance for wires to go over the Blackpill, they must go around. 
Up to you whether you cut the pressure transducer cable shorter. I chose to cut it down to about 12 in / 30 cm for my GC, but you may want it longer depending on your specific machine. 
Here’s a pic partway through the wiring process

The snubber is not required for operation but should extend the life of the relay and will reduce EMI, allowing you to route wires closer together. 
To wire you’ll need to make a pair of jumpers from snubber to relay, with the main wire going out to the solenoid. The wires don’t need to be large, I used 26 gauge for the jumper.
 
Those wires get routed under the AC-DC power supply like this

The assembled housing should look like this (I’ve chosen to use header pins on the Blackpill for connecting to an ST-Link, but you could also solder wires directly to those connection points). 
Close the housing with 4 screws to complete. 

Things that are not pictured – connections to solid state relay (SSR), touchscreen, scales, thermocouple, steam/brew switches. Please continue the install by referencing the machine-specific schematic and/or install instructions as they may vary.
Here are the labeled component connections to wiring that should be referenced by the machine-specific schematic(s). 