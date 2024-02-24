# Example tools
## Introduction
This article is not aimed at seasoned DIY enthusiasts who already possess a comprehensive set of tools. Instead, it's designed for primarily kit installers, offering beginner-friendly and budget-aware advice for those without extensive prior experience.

## Insulated Cable Crimper

An insulated cable crimper is crucial for fitting insulated ends, like Quick Connects (QCs) or Spades, onto cables. The insulation color on these connectors corresponds to the hole size, aiding in selecting the right connector for a given cable. For single cables, a red-insulated connector should be used, matching the crimper's red slot. For two cables going into a connector, use a connection with blue insulation.

Follow this step-by-step guide to utilize an insulated crimper effectively, with an example model: [Example Crimper](https://pl.aliexpress.com/item/1005005812085022.html).

1. **Cable Preparation**: Start by stripping about 6mm off the cable's insulation.
2. **Crimper Slot Selection**: Choose the crimper slot that matches the color of your connector (e.g., red for standard single cables).
3. **Securing the Connector**: Insert the connector into the appropriate slot of the crimper and lightly squeeze to keep it in place.
4. **Inserting the Cable and Crimping**: Place the stripped cable end into the connector. Ensure it's fully inserted before squeezing the crimper handles together to attach the connector firmly.
5. **Verify the connection**: Pull gently on a cable. If it's not held secure, cut the connector with pliers and redo the process.

Below is an example image demonstratration:

![insulated_crimper](https://github.com/kozikow/gaggiuino.github.io/assets/722866/5e3d69f1-0079-4ed0-954c-e3c70947c44a)

> [!Tip]
> The technique previously outlined is suitable for larger wires, such as 18 AWG wires mentioned in the bill of materials. For connecting smaller cables, such as those for the JST connector, if your kit isn't supplied with pre-crimped ends, you'll need to follow a few extra steps. An example scenario is when you need to attach spade (sometimes refered to as fork) connectors to the JST cables for the SSR. You can either splice (connect) these smaller cables with a larger 18 AWG wire and then crimp as previously described, or if you choose to crimp directly onto the smaller wire, you must strip four times the normal amount of insulation and fold the wire over itself to thicken it for the crimping process, given its original diameter is too small for conventional crimping methods.

## Uninsulated cable crimper

You'll use an uninsulated cable crimper mainly for BN connectors, also known as butt connectors, to join two high-voltage cables. Utilize BN 1.25 connectors for joining single cables and BN 2 for connecting pairs of cables into one connector. The essential tools for working with these uninsulated terminals are a punch and block, commonly used alongside electrician pliers. Remember to put insulation on top of those connections. Refer to the images below for guidance:

![uninsulated1](https://github.com/kozikow/gaggiuino.github.io/assets/722866/31e53688-562a-4ccd-818d-5727f698bb05)
![uninsulated2](https://github.com/kozikow/gaggiuino.github.io/assets/722866/05b41975-adb5-4f51-8b1c-234508a188eb)

## Long and thin screwdriver

The standard screwdriver in your toolkit may not suffice for all tasks in this project. A long, thin screwdriver with the capability to magnetize and demagnetize its tip is required.

There are specific scenarios where a regular screwdriver falls short:

1. **Pump and Eco Board Screws**: For removing screws that secure the pump and eco board to the machine's lower rear housing, a thin, long screwdriver with a magnetized tip.
2. **Thermocouple Attachment**: A tiny flat screw used to connect the thermocouple to the board demands precision (refer to the second photo below).

Here’s an example of a screwdriver kit suitable for these tasks, and all screwdriving needs you will need for completing the project:

![thin_screwdriver](https://github.com/kozikow/gaggiuino.github.io/assets/722866/4ace1768-8dd4-426b-b047-9b9075a0f5eb)

Additionally, PCB screws requiring a unique tip are shown here:

![thermo_screw](https://github.com/kozikow/gaggiuino.github.io/assets/722866/08081bcf-ebce-4a72-b67e-ffdd9d421872)

## Spanner and allen key 

To remove the brew and steam thermostats, a 17mm spanner key is essential. Reference the attached photo for clarification:

![steam_key](https://github.com/kozikow/gaggiuino.github.io/assets/722866/fac7c457-555b-4926-97bd-a386ed5b43f3)

Additionally, a 4mm Allen key is required for boiler removal. You can watch [this YouTube video](https://www.youtube.com/watch?v=JTTLYj1l0KI&t=204s) to see how removing Gaggia boiler works. It's strongly advised to detach the boiler when removing the thermostat and installing the thermocouple. Attempts to perform this task without removing the boiler have led to damaged thermocouples. The thermocouple is identified by the blue cable in the photo below (your thermocouple may have a different color):

![thermocouple](https://github.com/kozikow/gaggiuino.github.io/assets/722866/8b57b0af-07ee-483f-ba44-52cd729c7034)


## Lighter or heat gun

For tasks such as heating heat-shrink tubing and assisting with the stripping of tiny JST wires, you'll require a method to apply heat. A heat gun is excessive for the Gaggiuino project. A regular lighter can suffice, but a "flame-less" lighter, as shown in the photo below, is a better choice. It offers a more controlled application of heat, significantly reducing the risk of burning beyond the intended area. Flame-less lighters should not be more costly than traditional lighters, but consider this when selecting one for your toolkit.

![lighter](https://github.com/kozikow/gaggiuino.github.io/assets/722866/11421a4c-282d-4bd0-8aff-38294498809c)

## Pliers - Optional

When cutting cables, especially in hard-to-reach areas, having dedicated pliers can be invaluable, as regular scissors may not suffice. Various models are available; here is an example: [Cable Cutting Pliers](https://pl.aliexpress.com/item/4001146365274.html).

## Cable stripper - Optional

While an automated wire stripper is a convenient tool, it's not essential. You can accomplish all necessary stripping tasks with tools like pliers. Automated strippers offer useful features, such as the ability to adjust automatically to the cable's width for stripping and pulling, and pre-configured stripping lengths. For instance, when inserting two cables into the same connector, an automated stripper can ensure they are stripped to the exact same length, like 6mm, which is highly convenient.

![stripper](https://github.com/kozikow/gaggiuino.github.io/assets/722866/1950fd54-5f0d-4bfd-86a4-880c2beb114d)

However, for kits that include low-voltage work, such as tiny JST cables, an automated stripper might not be suitable as it could pull the cables apart. If stripping ever results in any metal strands coming off with the insulation, trim the end and strip again. For low-voltage cable stripping, gently heating the insulation and then pulling it off with pliers or even fingers, without cutting, can be effective. This method, as demonstrated in [this YouTube video](https://www.youtube.com/watch?v=n5o2drU65UM), can be used.

## Solder - Optional

Soldering in your Gaggiuino project can either be a necessity or an option, depending on the approach you choose.

For those assembling without a pre-made kit, soldering is essential. Additionally, some kits may not include pre-assembled low-voltage cabling, making soldering a recommended step for securing low-voltage connections. While handling the cables, avoid pulling them, but tight space inside Gaggia machine may make it hard and soldered connections will be much more secure.

Soldering cables together is simpler and more cost-effective than many assume, particularly when only soldering wires. For guidance, this instructional video offers excellent tips on cable soldering: [How to Connect Cables with a Soldering Iron](https://www.youtube.com/watch?v=Zu3TYBs65FM). Additionally, consult the [Solder Recommendations](learning-sources.md) for best practices and always employ the "Western Union" splice technique. "Splicing cables" refers to connecting two cables together.

When it comes to soldering low-voltage wires, even the most affordable soldering iron is sufficient. Ensure good ventilation or use a fan to avoid inhaling harmful fumes. The soldering process involves melting the solder (the wire in the middle above) by touching it with a hot iron (on the left), which then fuses the cables together more robustly.

![cheap_low_voltage](https://github.com/kozikow/gaggiuino.github.io/assets/722866/0631dcd4-7a85-4fe4-90af-71caa739cdf6)

## Multimeter - Optional

While a multimeter is not strictly required, it is immensely beneficial. Conducting multimeter tests is the first recommended step for troubleshooting should any component fail to function as expected. It's ideal for all components to be tested with a multimeter before the initial power-up. Before activating the device for the first time, it's crucial to check the continuity of both high-voltage (HV) and low-voltage (LV) lines to prevent short circuits where they shouldn't be and ensure continuity where it's needed (e.g., between pins on different components). Neglecting these preventive measures and powering on the device without prior testing could not only damage your board, necessitating a costly replacement but also pose a serious safety risk.

> [!Warning|style:callout]
> Bypassing these preliminary tests and immediately turning on the machine can lead to severe consequences beyond just damaging the board. For instance, a short circuit in the HV lines through the metal case of the Gaggia machine could lead to the case becoming electrified. This situation could quickly escalate, potentially tripping a breaker in your home. However, the more immediate danger is the risk of electric shock to anyone or anything that comes into contact with the live case, leading to a perilous situation. Always prioritize safety by conducting thorough pre-use checks to mitigate any risks of injury or damage.

Below is an example of multimeter test to detect a failed SSR connection:

![multimeter_test](https://github.com/kozikow/gaggiuino.github.io/assets/722866/14193f4a-9691-4942-909b-f6fe2d8b094c)
