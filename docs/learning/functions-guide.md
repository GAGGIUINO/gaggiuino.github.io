> [!NOTE]
> This page is a work in progress.
# Startup
<img alt="Startup" src="manual/00_000_startup.png">

- **Build Number**: 35b2d4d is the last Nextion Release, missing number indicates no communitaion between the Nextion and the microcontroller.

# Home
<img height="300" alt="Home" src="manual/01_000_home.png">

- **Menu**: The main menu.
- **Pofiles**: Tap to select, hold to rename. Last renamed profile is set as default profile. The following described by wundersnooch. (Thanks for your effort!)
  - *IUIUIU Classic* : A lower pressure profile with average length preinfusion and soak stages. A good all-rounder profile that should suit most beans with some tweaking.
  - *Londonium* : Simulates the extraction style and profile of a Londonium R lever machine. Described as pulling shots that are smooth with great body and an appealing syrupiness. Similar to the previous default profile, for those that are missing it. A flexible style suited for all bean and roast types, with usual consideration given to properly dialing in.
  - *Adaptive* : Designed to adapt to a given grind size by making the extraction phase decide the steady state flow relative to flow at peak pressure, as well as a pressurised bloom stage to maintain puck integrity resulting in a more consitent puck resistence. This allows it to be relatively forgiving to a range of grind settings. Best for light roasts, if using with darker roasts consider reducing temps and a shorter bloom. Use with a ratio between 1:2 and 1:25 with total shot times ranging from 25 to 45 seconds.
  - *Filter 2.1* : Used to make filter-style coffee with nothing but your espresso machine, some paper filters and a puck screen. Use a 58mm paper filter (or cut one to size) in the bottom of your portafilter basket, rise with hot water and fill with ground coffee (coarser than typical espresso but much finer than you would usually use for filter). WDT and optional(!) tamp. Place the metal puck screen on top and pull the shot to a 5:1 ratio. Dilute shot with 225-250g of water.
  - *Blooming Espresso* : Designed to maximise extraction quality and quanity with a flow-controlled pre-infusion and a long "blooming" phase, which allows the puck to become fully saturated before extraction. Best for light roasts, complex beans to draw out flavours the way a pourover would, while preventing sourness and sharpness.
- **Target Temp**: Target temperature of the boiler. Normally set to brew temp ( ~ 93&deg;C ), but will display steam temp when switched on ( ~ 155&deg;C ). This is set under -> Settings -> Temp.
- **Boiler Temp**: Current boiler temperature.
- **Pressure**: Current system pressure in bars.
- **Dose**: Adjust dose. Affects both Hardware and Predictive Scales.
- **Scales**: Hardware Scales required. View and tare scales. 
- **Tanks Water Level**: ToFnLED required. 0 to 100%.
- **Timer**: Machine uptime, counts from 0.
- **Dropping Beats**: Pressure release that happens about every minute if needed.

# Home -> Dose
<img height="300" alt="Dose" src="manual/01_001_dose.png">

- **Stop On Weight**: Stop on espress shot weight. Affects both Hardware and Predictive Scales. 
- **Coffee Dose**: Input weight of coffee grounds.
- **Brew Ratio**: Input weight of coffee grounds compared to the output weight of the espresso shot.
- **Shot Weight Override**: Manual override of the output weight, completely ignores **Coffee Dose** and **Brew Ratio**, set 0 to disable.

# Home -> Scales
<img height="300" alt="Scales" src="manual/01_002_scales.png">

Hardware Scales Required
- **Weight**: Current scale weight.
- **Tare**: Tares the scales. Scales auto tare on brew.

# Brew
<img height="300" alt="Brew" src="manual/02_000_brew.png">

- **Reset Weight**: Resets the weight, when on predictive scales press this when the first drips hit the cup.

# Brew -> Preinfusion
<img height="300" alt="PI" src="manual/02_001_pi.png">

Preinfusion (PI) fills the basket until a threshold pressure or time is reached at specified ml/s. The idea of preinfusion is to saturate the puck of coffee, with the aim of increasing evenness of extraction and reducing channeling. It also helps when extracting lighter roasts, which are harder to extract.
- **PI On / Off**: Turns PI on or off.
- **Flow / Bar**: Determines if flow or pressure is the PI target.
- **Fill**: Target for the PI phase.
  - **Time**: Target length of the PI phase in seconds.
  - **Flow**: Target flow rate for the PI phase.
  - **Pressure**: Target pressure for the PI phase.
- **Switch On**: When one of the folowing trigger move on to the Soak phase.
  - **Filled**: Amount of water pumped as an exit criteria.
  - **Pressure Above**: Pressure as an exit criteria if true or as a restriction if false.
  - **Weight Above**: Shot weight as an exit PI criteria.
- **Preview**: Preview the current profile.

Example: if you set a flow target of 8 ml/s, you set a time of 20, pressure of 4.5, filled of 100 and weight above of 5g, and you tick pressure above off. The system will try to hit 8ml/s but only if the pressure is at or under 4.5bars. so if you grind finely, then that high of a flow rate can't be achieved so it'll do the best it can, maybe it will settle at 4ml/s. This will continue until either one of these things happen: you pumped more than a 100ml of water, you got 5g in the cup, or you hit 20s of time. (Thanks np_x!)

# Brew -> Soak
<img height="300" alt="Soak" src="manual/02_002_soak.png">

Soak turns pump off completely allowing the built pressure during the fill phase to penetrate the puck naturally.
- **Soat On / Off**: Turns soak on or off.
- **Time**:  Sets the length of the soaking (blooming) phase
- **Maintain Pressure**:
- **Maintain Flow**:
- **Weight Above**:
- **Pressure Above**:
- **Pressure Below**:
- **Ramp/Slope**:
- **Ramp/Slope Type**: See easing section.

# Brew -> Pressure Profile
<img height="300" alt="PP" src="manual/02_003_profile.png">

- **Profile On / Off**: Turns profiling on or off.
- **Flow / Bar**: Determines if flow or pressure is the PP target.
- **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
- **End**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
- **Ramp/Slope**: Sets the length (aka curve speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.
- **Ramp/Slope Type**: See easing section.
- **Pressure Limit**:
- **Transition**: Advanced
- **Preview**: Preview the current profile.


# Brew -> Advanced
<img height="300" alt="Advanced" src="manual/02_004_advanced.png">

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
<img height="300" alt="Preview" src="manual/02_005_preview.png">

Sample profile preview.

<img height="380" alt="Classic" src="manual/declining_pp_classic.png">

Here is a classic pre-example of a declining pressure profile.

# Brew -> Manual
<img height="300" alt="Manual" src="manual/02_006_manual.png">

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
<img height="300" alt="More" src="manual/02_007_more.png">

- **Home On Finish**: Automatically return to the **Home Screen** after 10 seconds have passed since the brew has been stopped.
- **Brew Delta**: Boiler will increase temperature based on flow rate and be allowed to go over 100 C during the shot to more quickly transfer heat to the incoming cool water.
- **Basket Prefill**: Fills the basket until pressure stabilises at greater than or equal 0.1 bar.

# Steam
<img height="300" alt="Steam" src="manual/02_008_steam.png">

Ready to steam. Open wand valve to release pressure if temperature stops building.

# Clean -> Flush
<img height="300" alt="Flush" src="manual/03_001_flush.png">

Flushing can be used in one of two ways. Cleaning grounds out of the grouphead after a shot and back flushing through the three wave valve. **Never flush between back to back shots.**
- After shot flush
  1. Remove porta-filter and puck.
  2. Turn on **Brew** switch.
  3. Wait a couple seconds.
  4. Turn off **Brew** switch.
- Back flushing
  1. Insert blind basket into porta-filter.
  2. *OPTIONAL* Add Cafiza to blind basket.
  3. Lock porta-filter into the grouphead.
  4. Turn on **Brew** switch.
  5. Let machine cycle several times
  6. Turn off **Brew** switch.

# Clean -> Descale
<img height="300" alt="Descale" src="manual/03_002_descale.png">

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
  11. Retrun to **Home Screen** and select any profile to re-enable brew mode.

# Settings -> Temp
<img height="300" alt="Temp" src="manual/04_001_temp.png">

- **Water Target Temp**: Water target temperature, set per profile.
- **Steam Target Temp**: Steam target temperature, set system wide.
- **HPWR**: Relay max pulse width.
- **M. DIV**: Main cycle divider (aka non brew heating behaviour), used in conjunction with HPWR.
- **B. DIV**: Brew cycle divider.
- **Offset**: Offset value to calculate the real water temperature.

# Settings -> System
<img height="300" alt="System" src="manual/04_002_system.png">

- **Load Cells**: Hardware scales load cell values.
- **Pump Zero**: Amount of expeced water pumped per cycle in mL.
- **Warm Up**: Flashes **Warming Up** message for 15 minutes on machine power on.
- **LCD Sleep**: LCD sleep timer in minutes, set 0 to disable.
- **LCD Brightness**: 0 - 100%.
- **LED Control**: Settings for ToFnLED.
- **Reset**: Reset machine to default settings and profiles.

# Settings -> System -> LED
<img height="300" alt="LED" src="manual/04_003_led.png">

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
