# Example tools
## Introduction
This article is not aimed at seasoned DIY enthusiasts who already possess a comprehensive set of tools. Instead, it's designed for primarily kit installers, offering beginner-friendly and budget-aware advice for those without extensive prior experience.

## Insulated Cable Crimper

An insulated cable crimper is crucial for fitting insulated ends, like Quick Connects (QCs) or Spades, onto cables. The insulation color on these connectors corresponds to the hole size, aiding in selecting the right connector for a given cable. For single cables, a red-insulated connector should be used, matching the crimper's red slot. For two cables going into a connector, use a connection with blue insulation. [An Example Crimper](https://pl.aliexpress.com/item/1005005812085022.html) that would work.

For begginer-focused overview on how to use it see [Crimping insulated connectors](wiring-basics.md#crimping-insulated-connectors).

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

It is advisable to get an adjustable spanner due to the varying sizes of components requiring adjustment or removal - thermostats, steam wand, pressure transducer. Thermostats necessitate a 17mm spanner, as illustrated in the photo below. Pressure transducers, in particular, feature screws of different sizes in different kits. Connecting pressure transducer may need two spanners.

![steam_key](https://github.com/kozikow/gaggiuino.github.io/assets/722866/fac7c457-555b-4926-97bd-a386ed5b43f3)

Additionally, a 4mm Allen key is required for boiler removal. You can watch [this YouTube video](https://www.youtube.com/watch?v=JTTLYj1l0KI&t=204s) to see how removing Gaggia boiler works. It's advised to detach the boiler when removing the thermostat and installing the thermocouple. Attempts to perform this task without removing the boiler have led to damaged thermocouples.

## Lighter or heat gun

For tasks such as heating heat-shrink tubing and assisting with the stripping of tiny JST wires, you'll require a method to apply heat. A heat gun is excessive for the Gaggiuino project. A regular lighter can suffice, but a "flame-less" lighter, as shown in the photo below, is a better choice. It offers a more controlled application of heat, significantly reducing the risk of burning beyond the intended area. Flame-less lighters should not be more costly than traditional lighters, but consider this when selecting one for your toolkit.

![lighter](https://github.com/kozikow/gaggiuino.github.io/assets/722866/11421a4c-282d-4bd0-8aff-38294498809c)

## Pliers - Optional

When cutting cables, especially in hard-to-reach areas, having dedicated pliers can be invaluable, as regular scissors may not suffice. Various models are available; here is an example: [Cable Cutting Pliers](https://pl.aliexpress.com/item/4001146365274.html).

## Cable stripper - Optional

While an automated wire stripper is a convenient tool, it's not essential. You can accomplish all necessary stripping tasks with tools like pliers. 

For begginer-focused overview on cable stripping [Cable stripping](wiring-basics.md#cable-stripping).

## Solder - Optional

Soldering in your Gaggiuino project can either be a necessity or an option, depending on the approach you choose.

For those assembling without a pre-made kit, soldering is essential. Additionally, some kits may not include pre-assembled low-voltage cabling, making soldering a recommended step for securing low-voltage connections. While handling the cables, avoid pulling them, but tight space inside Gaggia machine may make it hard and soldered connections will be much more secure.

Soldering cables together is simpler and more cost-effective than many assume, particularly when only soldering wires. For guidance, this instructional video offers excellent tips on cable soldering: [How to Connect Cables with a Soldering Iron](https://www.youtube.com/watch?v=Zu3TYBs65FM). Additionally, consult the [Solder Recommendations](learning-sources.md) for best practices and always employ the "Western Union" splice technique. "Splicing cables" refers to connecting two cables together. When it comes to soldering low-voltage wires, even the most affordable soldering iron is sufficient. 

## Multimeter - Optional

While a multimeter is not strictly required, it is immensely beneficial. Conducting multimeter tests is the first recommended step for troubleshooting should any component fail to function as expected. It's ideal for all components to be tested with a multimeter before the initial power-up. Before activating the device for the first time, it's crucial to check the continuity of both high-voltage (HV) and low-voltage (LV) lines to prevent short circuits where they shouldn't be and ensure continuity where it's needed (e.g., between pins on different components). Neglecting these preventive measures and powering on the device without prior testing could not only damage your board, necessitating a costly replacement but also pose a serious safety risk.

**Important Safety Warning**: Bypassing these preliminary tests and immediately turning on the machine can lead to severe consequences beyond just damaging the board. For instance, a short circuit in the HV lines through the metal case of the Gaggia machine could lead to the case becoming electrified. This situation could quickly escalate, potentially tripping a breaker in your home. However, the more immediate danger is the risk of electric shock to anyone or anything that comes into contact with the live case, leading to a perilous situation. Always prioritize safety by conducting thorough pre-use checks to mitigate any risks of injury or damage.
