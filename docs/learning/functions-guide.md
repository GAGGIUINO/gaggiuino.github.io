> [!NOTE]
> This page is a work in progress.

Special Thanks to:
wundersnooch
np_x
EuphoricCatastrophe

# Startup
<img alt="Startup" src="manual/00_000_startup.png">

- **Build Number**: 35b2d4d is the last Nextion Release, missing number indicates no communication between the Nextion and the micro controller.

# Home
<img alt="Home" src="manual/01_000_home.png">

- **Menu**: The main menu.
- **Profiles**: Tap to select, hold to rename. Last renamed profile is set as default profile.
  - *IUIUIU Classic* : A lower pressure profile with average length pre-infusion and soak stages. A good all-rounder profile that should suit most beans with some tweaking.
  - *Londonium* : Simulates the extraction style and profile of a Londonium R lever machine. Described as pulling shots that are smooth with great body and an appealing syrupiness. Similar to the previous default profile, for those that are missing it. A flexible style suited for all bean and roast types, with usual consideration given to properly dialing in.
  - *Adaptive* : Designed to adapt to a given grind size by making the extraction phase decide the steady state flow relative to flow at peak pressure, as well as a pressurized bloom stage to maintain puck integrity resulting in a more consistent puck resistance. This allows it to be relatively forgiving to a range of grind settings. Best for light roasts, if using with darker roasts consider reducing temps and a shorter bloom. Use with a ratio between 1:2 and 1:25 with total shot times ranging from 25 to 45 seconds.
  - *Filter 2.1* : Used to make filter-style coffee with nothing but your espresso machine, some paper filters and a puck screen. Use a 58mm paper filter (or cut one to size) in the bottom of your portafilter basket, rise with hot water and fill with ground coffee (coarser than typical espresso but much finer than you would usually use for filter). WDT and optional(!) tamp. Place the metal puck screen on top and pull the shot to a 5:1 ratio. Dilute shot with 225-250g of water.
  - *Blooming Espresso* : Designed to maximize extraction quality and quantity with a flow-controlled pre-infusion and a long "blooming" phase, which allows the puck to become fully saturated before extraction. Best for light roasts, complex beans to draw out flavours the way a pour over would, while preventing sourness and sharpness.
- **Target Temp**: Target temperature of the boiler. Normally set to brew temp ( ~ 93&deg;C ), but will display steam temp when switched on ( ~ 155&deg;C ). This is set under -> Settings -> Temp.
- **Water Temp**: Current boiler temperature.
- **Pressure**: Current system pressure in bars.
- **Dose**: Adjust dose. Affects both Hardware and Predictive Scales.
- **Scales**: Hardware Scales required. View and tare scales. 
- **Tanks Water Level**: ToFnLED required. 0 to 100%.
- **System Uptime**: Machine uptime, counts from 0. 10 to 15 minute warm-up is recommended.
- **Dropping Beats**: Pressure release through the group head, system pressure and group water equalizing measure triggers when pressure is above 0.7bar.

# Home -> Brew Ratio
<img alt="Dose" src="manual/01_001_dose.png">

- **Stop On Weight**: Stop on espresso shot weight. Affects both Hardware and Predictive Scales. 
- **Coffee Dose**: Input weight of coffee grounds.
- **Brew Ratio**: Input weight of coffee grounds compared to the output weight of the espresso shot.
- **Shot Weight Override**: Manual override of the output weight, completely ignores **Coffee Dose** and **Brew Ratio**, set 0 to disable.

# Home -> Scales
<img alt="Scales" src="manual/01_002_scales.png">

Hardware Scales Required
- **Weight**: Current scale weight.
- **Tare**: Tares the scales. Scales auto tare on brew.

# Home -> Profile Rename
<img alt="Profile" src="manual/01_003_rename.png">

To access the **Profile Rename** screen long press on a profile from the **Home** screen. 
- **Profile**: Change a profile’s name.
- **Load Default**: Reload the settings and values for that profile slot back to default.
- **Okay**: Renames the selected profile and sets it to the default profile that will load at start-up. Renaming is not required to set to default.

# Brew
<img alt="Brew" src="manual/02_000_brew.png">

- **Reset Weight**: Resets the weight, when on predictive scales press this when the first drips hit the cup.

# Brew -> Pre-Infusion
<img alt="PI" src="manual/02_001_pi.png">

Pre-infusion (PI) fills the basket until a threshold is reached. The idea of pre-infusion is to saturate the puck of coffee, with the aim of increasing evenness of extraction and reducing channeling. It also helps when extracting lighter roasts, which are harder to extract.
- **PI On / Off**: Turns PI on or off.
- **Flow / Bar**: Determines if flow or pressure is the PI target.
- **Fill**: Target for the PI phase.
  - **Time**: Target length of the PI phase in seconds.
  - **Flow**: Target flow rate for the PI phase.
  - **Pressure**: Target pressure for the PI phase.
- **Switch On**: When one of the following trigger, move on to the **Soak** phase.
  - **Filled**: Exit when amount water pumped is set value in mL.
  - **Pressure Above**: Pressure as an exit criteria if true or as a restriction if false.
  - **Weight Above**: Exit when weight is above set value in grams.
- **Preview**: Preview the current profile.

Example: if you set a flow target of 8 ml/s, you set a time of 20, pressure of 4.5, filled of 100 and weight above of 5g, and you tick pressure above off. The system will try to hit 8ml/s but only if the pressure is at or under 4.5bars. so if you grind finely, then that high of a flow rate can't be achieved so it'll do the best it can, maybe it will settle at 4ml/s. This will continue until either one of these things happen: you pumped more than a 100ml of water, you got 5g in the cup, or you hit 20s of time. (Thanks np_x!)

# Brew -> Soak
<img alt="Soak" src="manual/02_002_soak.png">

Soak turns pump off completely allowing the built pressure during the pre-infusion phase to penetrate the puck naturally. This helps because it theoretically allows some of the trapped C02 from roasting coffee to escape, allowing easier extractions. If you have a darker roast, you might or might not want to do this phase, since darker roasts are easier to extract.
- **Soak On / Off**: Turns soak on or off.
- **Target**: Target for the Soak phase.  If you keep only one above 0, then the system will aim to maintain that target during the soak phase. If more than one are above zero, the system interprets that as a pressure target with a flow restriction. if you say don't pump any water in (i.e. both are 0) then pressure will gradually fall as the puck resistance falls, resulting in a decline in pressure and/or increase in weight.
  - **Time**: Sets the length of the soaking (blooming) phase.
  - **Maintain Pressure**: Machine will attempt to maintain pressure at set value in bars.
  - **Maintain Flow**: Machine will attempt to maintain flow at set value in mL/s.
- **Switch On**: When one of the following trigger, move on to the **Pressure Profile** phase.
  - **Weight Above**: Exit when weight is above set value in grams.
  - **Pressure Above**: Exit when pressure is above set value in bars.
  - **Pressure Below**: Exit when Pressure is below set value in bars.
- **Ramp/Slope**: Number of seconds it should take to get to the resulting target.
- **Ramp/Slope Type**: Transition curve type, which corresponds to how the machine will get to its target. See easing section.

# Brew -> Pressure Profile
<img alt="PP" src="manual/02_003_profile.png">

- **Profile On / Off**: Turns profiling on or off.
- **Flow / Bar**: Determines if flow or pressure is the PP target.
- **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
- **End**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
- **Ramp/Slope**: Sets the length (aka curve speed) of the PP drop/raise behavior, so one can change the pressure slow or fast if desired.
- **Ramp/Slope Type**: See easing section.
- **Pressure Limit**:
- **Transition**: Advanced
- **Preview**: Preview the current profile.


# Brew -> Advanced
<img alt="Advanced" src="manual/02_004_advanced.png">

- **Profile On / Off**: Turns profiling on or off.
- **Flow / Bar**: Determines if flow or pressure is the PP target.
- **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
- **End**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
- **Hold**: Sets the length of the PP hold period, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
- **Ramp/Slope**: Sets the length (aka curve speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.
- **Ramp/Slope Type**: See easing section.
- **Flow Limit**:
- **Hold Limit**:
- **Preview**: Preview the current profile.

# Brew -> Preview
<img alt="Preview" src="manual/02_005_preview.png">

Sample profile preview.

<img alt="Classic" src="manual/declining_pp_classic.png">

Here is a classic pre-example of a declining pressure profile.

# Brew -> Manual
<img alt="Manual" src="manual/02_006_manual.png">

Manual pressure control at brew time.
  - **Status**
    - *Temp &deg;C* : Target temperature.
    - *Flow(g/s)* : Current flow rate in grams per second.
    - *Pressure* : Current pressure in bars.
    - *Weight(g)* : Current weight of shot.
  - **Control**: Manual control slider.
  - **Boiler Temp**: Current boiler temperature.
  - **Flow**: Current flow rate in mililiter per second.

# Brew -> More
<img alt="More" src="manual/02_007_more.png">

- **Home On Finish**: Automatically return to the **Home Screen** after 10 seconds have passed since the brew has been stopped.
- **Brew Delta**: Boiler will increase temperature based on flow rate and be allowed to go over 100 C during the shot to more quickly transfer heat to the incoming cool water.
- **Basket Prefill**: Fills the basket until pressure stabilises at greater than or equal 0.1 bar.

# Steam
<img alt="Steam" src="manual/02_008_steam.png">

Ready to steam. Open wand valve to release pressure if temperature sto
# Clean -> Flush
<img alt="Flush" src="manual/03_001_flush.png">

Flushing can be used in one of two ways. Cleaning grounds out of the grouphead after a shot and back flushing through the three wave valve. **Never flush between back to back shots.**
- After shot flush
  1. Remove porta-filter and puck.
  2. Turn on **Brew** switch.
  3. Wait a couple seconds.
  4. Turn off **Brew** switch.
- Back flushing
  1. Insert blind basket into porta-filter.
  2. *OPTIONAL* Remove shower screen and add Cafiza to blind basket.
  3. Lock porta-filter into the grouphead.
  4. Turn on **Brew** switch.
  5. Let machine cycle several times
  6. Turn off **Brew** switch.

# Clean -> Descale
<img alt="Descale" src="manual/03_002_descale.png">

The descaling process takes around 45-50 minutes.
  1. Fill water tank to "MAX" with water and descale solution (possible 4-6tbsp citric acid per one tank of water).
  2. Insert blind basket into porta-filter.
  3. Lock porta-filter into the grouphead.
  4. Place a reservoir under the steam wand and open the steam valve one full turn.
  5. Turn on **Brew** switch.
  6. Wait about 30 minutes, checking for an empty water tank.
  7. Once the descaling solution and water mix runs out fill the reservoir with clean fresh water. 
  8. The pump should auto prime and continue the cleaning procedure.
  9. A **FINISHED** message will popup when descaling finishes.
  10. Turn off **Brew** switch.
  11. Retrun to **Home** Screen and select any profile to re-enable brew mode.

# Settings -> Temp
<img alt="Temp" src="manual/04_001_temp.png">

- **Water Target Temp**: Water target temperature, set per profile.
- **Steam Target Temp**: Steam target temperature, set system wide.
- **HPWR**: Relay max pulse width.
- **M. DIV**: Main cycle divider (aka non brew heating behaviour), used in conjunction with HPWR.
- **B. DIV**: Brew cycle divider.
- **Offset**: Offset value to calculate the real water temperature.

# Settings -> System
<img alt="System" src="manual/04_002_system.png">

- **Load Cells**: Hardware scales load cell values.
- **Pump Zero**: Amount of expeced water pumped per cycle in mL.
- **Warm Up**: Flashes **Warming Up** message for 15 minutes on machine power on.
- **LCD Sleep**: LCD sleep timer in minutes, set 0 to disable.
- **LCD Brightness**: 0 - 100%.
- **LED Control**: Settings for ToFnLED.
- **Reset**: Reset machine to default settings and profiles.

# Settings -> System -> LED
<img alt="LED" src="manual/04_003_led.png">

ToFnLED Required.

- **LED On/Off**: Turn water tank led on or off. 
- **LED Color**: Red, Green, Blue, color control
- **Disco Mode**: Brew in style.

# Easing
- *Ease-In* : Slow start to rapid end.
<img alt="In" src="manual/ease_in.png">

- *Ease-Out* : Rapid start to slow end.
<img  alt="Out" src="manual/ease_out.png">

- *Ease-In-Out* : Slow start to slow end.
<img  alt="In Out" src="manual/ease_in_out.png">

- *Linear* : Consistnat rate of change.
<img  alt="Linear" src="manual/ease_linear.png">

- *Instant* : Instant change.
<img  alt="Instant" src="manual/ease_instant.png">
