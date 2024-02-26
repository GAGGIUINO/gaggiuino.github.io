# Introduction

This article is primarily aimed at kit installers without significant prior electrical experience. If you are already familiar with the basics of doing electronics projects information here may be redundant for you.

# Connectors overview

There are different types of connections used in the build. Based on the following picture:

![connectors](https://github.com/kozikow/gaggiuino.github.io/assets/722866/cba29dc6-3a60-4bd5-a2c1-92f5cc4c08e2)

From the left:
1. White plastic, first from the left – **JST**, those will just plug into the board. Those should come in the kit, but you may need to connect the cables (splice to another cable and add a connector – e.g. fork for SSR). It’s OK to splice those tiny cables to thicker cables.
2. Second from the left – **QC connector**, sometimes refered to as spade. Those will plug into various parts of the machine like switches and into 4 big connectors (3PLN) at the board. You will primarily use female connectors as seen in the picture, but some setups may use male connectors.
3. **Spade connector**, Third from the left. Sometimes referred to as fork connector (yes, spade semantics are confusing). Those will connect to SSR with screw-on.
4. **BN connector**, sometimes referred to as butt connector, first from the right – those will connect two high voltage cables together, as those shouldn’t be soldered due to added resistance. After connecting remember to add the insulation on top of this connector.
5. **Low voltage cable splicing** – connecting two low voltage cables together, that may be optional depending on your route. Western Union Splice and soldering – see [recommendations page](learning-sources.md).
6. Boiler attachments on the top and lights connections can be re-used from what already exists in the machine both in Stock and Custom integrations. 

# Crimping insulated connectors

This is an introduction to the usage of an insulated crimper.

1. **Cable Preparation**: Start by stripping about 6mm off the cable's insulation.
2. **Crimper Slot Selection**: Choose the crimper slot that matches the color of your connector (e.g., red for standard single cables).
3. **Securing the Connector**: Insert the connector into the appropriate slot of the crimper and lightly squeeze to keep it in place.
4. **Inserting the Cable and Crimping**: Place the stripped cable end into the connector. Ensure it's fully inserted before squeezing the crimper handles together to attach the connector firmly.
5. **Verify the connection**: Pull gently on a cable. If it's not held secure, cut the connector with pliers and redo the process.

Below is an example image demonstration:

![insulated_crimper](https://github.com/kozikow/gaggiuino.github.io/assets/722866/5e3d69f1-0079-4ed0-954c-e3c70947c44a)

> [!Tip]
> The technique previously outlined is suitable for larger wires, such as 18 AWG wires mentioned in the bill of materials. For connecting smaller cables, such as those for the JST connector, if your kit isn't supplied with pre-crimped ends, you'll need to follow a few extra steps. An example scenario is when you need to attach spade (sometimes referred to as fork) connectors to the JST cables for the SSR. You can either splice (connect) these smaller cables with a larger 18 AWG wire and then crimp as previously described or if you choose to crimp directly onto the smaller wire, you must strip four times the normal amount of insulation and fold the wire over itself to thicken it for the crimping process, given its original diameter is too small for conventional crimping methods.

# Cable stripping

Cable stripping refers to taking the insulation off the cable, so metal is exposed for connections. Any previously stripped exposed metal area should be insulated after connecting. Any cable stripping can be achieved with pliers, scisors or a dedicated tool.  Automated strippers offer useful features, such as the ability to adjust automatically to the cable's width for stripping and pulling, and pre-configured stripping lengths. For instance, when inserting two cables into the same connector, an automated stripper can ensure they are stripped to the exact same length, like 6mm, which is highly convenient.

![stripper](https://github.com/kozikow/gaggiuino.github.io/assets/722866/1950fd54-5f0d-4bfd-86a4-880c2beb114d)

If stripping ever results in any metal strands coming off with the insulation, trim the end and strip again. 

However, for kits that include low-voltage work, such as tiny JST cables, an automated stripper might not be suitable as it could pull the cables apart. For low-voltage cable stripping, gently heating the insulation and then pulling it off with pliers or even fingers, without cutting, can be effective. This method, as demonstrated in [this YouTube video](https://www.youtube.com/watch?v=n5o2drU65UM), can be used.

# Thermal fuse

Some installers have been confused by the thermal fuse setup. Refer to the following picture: 

![fuse_new](https://github.com/kozikow/gaggiuino.github.io/assets/722866/37c18fea-959b-4788-abbe-896db287d696)


In all installations, the steam and brew thermostats are removed and discarded. Kits may offer a resettable thermal fuse that will go into the steam thermostat slot as a replacement; if not included, this space remains vacant. Original thermal fuse is used instead and kept as it is. This component is crucial for safety, disconnecting the circuit if the boiler overheats.

There is another thermal fuse in Gaggia machines - pump thermal fuse, seen in the following picture. Most of setups - either stock integrations or custom wirings would leave this pump thermal fuse as it is, just connecting cables to it.


![pump_thermal_fuse](https://github.com/kozikow/gaggiuino.github.io/assets/722866/9f71d390-a802-4d49-851b-3ccfa03b4536)

