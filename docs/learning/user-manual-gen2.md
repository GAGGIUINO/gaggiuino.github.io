# User Manual

> [!NOTE]
> This page is a work in progress.

Special Thanks to:
- wundersnooch
- np_x
- EuphoricCatastrophe

# Startup
<img alt="Startup" src="manual/gen2/00_000_startup.png">

- **Build Number**: A missing number indicates no communication between the Nextion and the micro controller.

# Home
<img alt="Home" src="manual/gen2/01_000_home.png">

- **Menu**: The main menu.
- **Profiles**: Tap to select, hold to enter **Custom Profile Override**. Last renamed profile is set as default profile.
  - *IUIUIU Classic* : A mixed style profile with a flow driven preinfussion for an even puck, free falling pressure driven soak to provide balanced extraction and a complex pressure driven but flow limited  profilling phase. A good all-rounder profile that should suit most beans with some tweaking.
  - *Londinium* : Simulates the extraction style and profile of a Londinium R lever machine. Described as pulling shots that are smooth with great body and an appealing syrupiness. Similar to the previous default profile, for those that are missing it. A flexible style suited for all bean and roast types, with usual consideration given to properly dialing in.
  - *Adaptive* : Designed to adapt to a given grind size by making the extraction phase decide the steady state flow relative to flow at peak pressure, as well as a pressurized bloom stage to maintain puck integrity resulting in a more consistent puck resistance. This allows it to be relatively forgiving to a range of grind settings. Best for light roasts, if using with darker roasts consider reducing temps and a shorter bloom. Use with a ratio between 1:2 and 1:25 with total shot times ranging from 25 to 45 seconds.
  - *Filter 2.1* : Used to make filter-style coffee with nothing but your espresso machine, some paper filters and a puck screen. Use a 58mm paper filter (or cut one to size) in the bottom of your portafilter basket, rise with hot water and fill with ground coffee (coarser than typical espresso but much finer than you would usually use for filter). WDT and optional(!) tamp. Place the metal puck screen on top and pull the shot to a 5:1 ratio. Dilute shot with 225-250g of water.
  - *Blooming Espresso* : Designed to maximize extraction quality and quantity with a flow-controlled pre-infusion and a long "blooming" phase, which allows the puck to become fully saturated before extraction. Best for light roasts, complex beans to draw out flavours the way a pour over would, while preventing sourness and sharpness.
- **Target Temp**: Target water temperature. Normally set to brew temp ( ~ 93&deg;C ), but will display steam temp when switched on ( ~ 155&deg;C ). This is set under -> Settings -> Temp.
- **Water Temp**: Current water temperature.
- **Pressure**: Current system pressure in bars.
- **Brew Ratio**: Adjust dose. Affects both Hardware and Predictive Scales.
- **Scales**: Hardware Scales required. View and tare scales. 
- **Tanks Water Level**: ToFnLED required. 0 to 100%.
- **System Uptime**: Machine uptime, counts from 0. 10 to 15 minute warm-up is recommended.
- **Dropping Beats**: Automatic pressure release through the group head, it is a system pressure and group water equalizing measure that triggers when pressure is above 0.7bar. This is done to improve shot consistency.

# Home -> Brew Ratio
<img alt="Dose" src="manual/gen2/01_001_dose.png">

- **Stop On Weight**: Stop on espresso shot weight. Affects both Hardware and Predictive Scales. 
- **Coffee Dose**: Input weight of coffee grounds.
- **Brew Ratio**: Input weight of coffee grounds compared to the output weight of the espresso shot.
- **Shot Weight Override**: Manual override of the output weight, completely ignores **Coffee Dose** and **Brew Ratio**, set 0 to disable.

# Home -> Scales
<img alt="Scales" src="manual/gen2/01_002_scales.png">

Hardware Scales Required
- **Weight**: Current scale weight.
- **Tare**: Tares the scales. Scales auto tare on brew.

# Home -> Custom Profile Override
<img alt="Profile" src="manual/gen2/01_003_rename.png">

To access the **Custom Profile Override** screen long press on a profile from the **Home** screen. When building out a new brew profile select the profile slot from the home screen, make changes in the **Pre-Infusion**, **Soak**, **Profiling**, and **Advanced** pages. Return to the **Home** screen, long press on the profile, give it a custom name, press ok to save and set it as default start-up profile.
- **Profile**: Change a profile’s name.
- **Load Default**: Return profile slot to Gaggiuino preloaded settings. Exits to **Home** screen without setting profile as start-up default.
- **Okay**: Renames the selected profile and sets it to the default profile that will load at start-up. Renaming is not required to set to default.

# Brew
<img alt="Brew" src="manual/gen2/02_000_brew.png">

- **Reset Weight**: Resets the weight, when on predictive scales press this when the first drips hit the cup.

# Brew -> Pre-Infusion
<img alt="PI" src="manual/gen2/02_001_pi.png">

Pre-infusion phase fills the basket until a threshold is reached. The idea of pre-infusion is to saturate the puck of coffee, with the aim of increasing evenness of extraction and reducing channeling. It also helps when extracting lighter roasts, which are harder to extract.
- **PI On / Off**: Turns pre-infusion on or off.
- **Flow / Bar**: Determines if flow or pressure is the PI target.
- **Fill**: Target for the pre-infusion phase.
  - **Time**: Target length of the pre-infusion phase in seconds.
  - **Flow**: Target flow rate for the pre-infusion phase.
  - **Pressure**: Target pressure for the pre-infusion phase.
- **Switch On**: When one of the following trigger, move on to the **Soak** phase.
  - **Filled**: Exit when amount water pumped is set value in mL.
  - **Pressure Above**: Pressure as an exit criteria if true or as a restriction if false.
  - **Weight Above**: Exit when weight is above set value in grams.
- **Preview**: Preview the current profile.

Example: if you set a flow target of 8 ml/s, you set a time of 20, pressure of 4.5, filled of 100 and weight above of 5g, and you tick pressure above off. The system will try to hit 8ml/s but only if the pressure is at or under 4.5bars. so if you grind finely, then that high of a flow rate can't be achieved so it'll do the best it can, maybe it will settle at 4ml/s. This will continue until either one of these things happen: you pumped more than a 100ml of water, you got 5g in the cup, or you hit 20s of time.

# Brew -> Soak
<img alt="Soak" src="manual/gen2/02_002_soak.png">

Soak phase turns pump off completely allowing the built pressure during the pre-infusion phase to penetrate the puck naturally. This helps because it theoretically allows some of the trapped C02 from roasting coffee to escape, allowing easier extractions. If you have a darker roast, you might or might not want to do this phase, since darker roasts are easier to extract.
- **Soak On / Off**: Turns soak on or off.
- **Target**: Target for the Soak phase.  If you keep only one above 0, then the system will aim to maintain that target during the soak phase. If more than one are above zero, the system interprets that as a pressure target with a flow restriction. if you say don't pump any water in (i.e. both are 0) then pressure will gradually fall as the puck resistance falls, resulting in a decline in pressure and/or increase in weight.
  - **Time**: Sets the length of the soaking (blooming) phase.
  - **Maintain Pressure**: Machine will attempt to maintain pressure at set value in bars.
  - **Maintain Flow**: Machine will attempt to maintain flow at set value in mL/s.
- **Switch On**: When one of the following trigger, move on to the **Pressure Profile** phase.
  - **Weight Above**: Exit when weight is above set value in grams.
  - **Pressure Above**: Exit when pressure is above set value in bars.
  - **Pressure Below**: Exit when Pressure is below set value in bars.
- **Slope Time**: Number of seconds it should take to get to the target.
- **Slope Type**: Curve type, which corresponds to how the machine will get to its target. See **Easing** section.

# Brew -> Profiling
<img alt="PP" src="manual/gen2/02_003_profile.png">

Profiling phase.
- **Profile On / Off**: Turns profiling on or off.
- **Flow / Bar**: Determines if flow or pressure is the profile target.
- **Start**: Sets the desired starting point of the profile phase, can be high to low or low to high. In bars or mL/s depending on **Flow/Bar** switch.
- **End**: Sets the desired finish point of the profile phase, same as above can be high to low or low to high. In bars or mL/s depending on **Flow/Bar** switch.
- **Slope Time**: Number of seconds it should take to get to the target.
- **Slope Type**: Curve type, which corresponds to how the machine will get to its target. See **Easing** section.
- **Limit**: Machine will attempt to maintain set value. In bars or mL/s depending on **Flow/Bar** switch.
- **Transition**: See **Advanced** section.
- **Preview**: Preview the current profile.


# Brew -> Advanced
<img alt="Advanced" src="manual/gen2/02_004_advanced.png">

Transition phase in between soak and profiling. Use this if you want to hold a target for a specified amount before profiling.
- **Profile On / Off**: Turns transition on or off.
- **Flow / Bar**: Determines if flow or pressure is the transition target.
- **Start**: Sets the desired starting point of the transition phase, can be high to low or low to high. In bars or mL/s depending on **Flow/Bar** switch.
- **End**: Sets the desired finish point of the transition phase, same as above can be high to low or low to high. In bars or mL/s depending on **Flow/Bar** switch.
- **Hold**: Sets the length of the transition hold period in seconds, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
- **Slope Time**: Number of seconds it should take to get to the target.
- **Slope Type**: Curve type, which corresponds to how the machine will get to its target. See **Easing** section.
- **Limit**: In bars or mL/s depending on **Flow/Bar** switch.
- **Hold Limit**: In bars or mL/s depending on **Flow/Bar** switch.
- **Preview**: Preview the current profile.

# Brew -> Preview
<img alt="Preview" src="manual/gen2/02_005_preview.png">

Sample profile preview.

<img alt="Classic" src="manual/gen2/declining_pp_classic.png">

Here is a classic pre-example of a declining pressure profile.

# Brew -> Manual
<img alt="Manual" src="manual/gen2/02_006_manual.png">

Manual flow control. Adjust flow traget flow rate with sider, flipe the brew switch to start.
  - **Control**: Manual control slider.
  - **Target Flow**: Target flow rate in mL per second.
  - **Shot Timer**: Shot timer in seconds.
  - **Status**
    - *Temp &deg;C* : Current water temperature.
    - *Flow(g/s)* : Current flow rate in grams per second.
    - *Pressure* : Current pressure in bars.
    - *Weight(g)* : Current weight of shot.
  

# Brew -> More
<img alt="More" src="manual/gen2/02_007_more.png">

- **Home On Finish**: Automatically return to the **Home Screen** after 10 seconds have passed since the brew has been stopped.
- **Brew Delta**: Boiler will increase temperature based on flow rate and be allowed to go over 100 C during the shot to more quickly transfer heat to the incoming cool water.
- **Basket Prefill**: Fills the basket until pressure stabilizes at greater than or equal 0.1 bar.

# Steam
<img alt="Steam" src="manual/gen2/02_008_steam.png">

Ready to steam. Open steam wand valve to release pressure if temperature stops increasing.
# Clean -> Flush
<img alt="Flush" src="manual/gen2/03_001_flush.png">

Flushing can be used in one of two ways. Cleaning grounds out of the group head after a shot and back flushing through the three wave valve.
- After shot flush
  1. Remove portafilter and puck.
  2. Turn on **Brew** switch.
  3. Wait a couple seconds.
  4. Turn off **Brew** switch.
- Back flushing
  1. Insert blind basket into portafilter.
  2. *OPTIONAL* Remove shower screen and add Cafiza to blind basket.
  3. Lock portafilter into the group head.
  4. Turn on **Brew** switch.
  5. Let machine cycle several times
  6. Turn off **Brew** switch.

# Clean -> Descale
<img alt="Descale" src="manual/gen2/03_002_descale.png">

The descaling process takes around 45-50 minutes.
  1. Fill water tank to "MAX" with water and descale solution (possible 4-6tbsp citric acid per one tank of water).
  2. Insert blind basket into portafilter.
  3. Lock portafilter into the group head.
  4. Place a 2+ L reservoir under the steam wand and open the steam valve one full turn.
  5. Turn on **Brew** switch.
  6. Wait about 30 minutes, checking for an empty water tank.
  7. Once the descaling solution and water mix runs out, empty and replace the reservoir if needed and then fill the water tank with clean fresh water. 
  8. The pump should auto prime and continue the cleaning procedure.
  9. A **FINISHED** message will popup when descaling finishes.
  10. Turn off **Brew** switch.
  11. Return to **Home** Screen and select any profile to re-enable brew mode.

# Settings -> Temp
<img alt="Temp" src="manual/gen2/04_001_temp.png">

- **Water Target Temp**: Water target temperature, set per profile.
- **Steam Target Temp**: Steam target temperature, set system wide.
- **HPWR**: Relay max pulse width.
- **M. DIV**: Main cycle divider (aka non brew heating behavior), used in conjunction with HPWR.
- **B. DIV**: Brew cycle divider.
- **Offset**: Offset value to calculate the real water temperature.

# Settings -> System
<img alt="System" src="manual/gen2/04_002_system.png">

- **Load Cells**: Hardware scales load cell values.
- **Pump Zero**: Amount of expected water pumped per cycle in mL.
- **Warm Up**: Flashes **Warming Up** message for 15 minutes on machine power on.
- **LCD Sleep**: LCD sleep timer in minutes, set 0 to disable.
- **LCD Brightness**: 0 - 100%.
- **LED Control**: Settings for ToFnLED.
- **Reset**: Reset machine to default settings and profiles.

# Settings -> System -> LED
<img alt="LED" src="manual/gen2/04_003_led.png">

ToFnLED Required.

- **LED On/Off**: Turn water tank led on or off. 
- **LED Color**: Red, Green, Blue, color control
- **Disco Mode**: Brew in style.

# Easing
- *Ease-In* : Slow start to rapid end.
<img alt="In" src="manual/gen2/ease_in.png">

- *Ease-Out* : Rapid start to slow end.
<img  alt="Out" src="manual/gen2/ease_out.png">

- *Ease-In-Out* : Slow start to slow end.
<img  alt="In Out" src="manual/gen2/ease_in_out.png">

- *Linear* : Consistent rate of change.
<img  alt="Linear" src="manual/gen2/ease_linear.png">

- *Instant* : Instant change.
<img  alt="Instant" src="manual/gen2/ease_instant.png">
