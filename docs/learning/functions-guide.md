> [!NOTE]
> This page is a work in progress.
# Startup
<img height="300" alt="Startup" src="manual/00_000_startup.png">

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

# Home -> Dose
<img height="300" alt="Dose" src="manual/01_001_dose.png">

- **Stop On Weight**: Stop on espress shot weight. Affects both Hardware and Predictive Scales. 
- **Coffee Dose**: Input weight of coffee grounds.
- **Brew Ratio**: Input weight of coffee grounds compared to the output weight of the espresso shot.
- **Shot Weight Override**: Manual override of the output weight.

# Home -> Scales
<img height="300" alt="Scales" src="manual/01_002_scales.png">

Hardware Scales Required
- **Weight**: Current scale weight.
- **Tare**: Tares the scales. Scales auto tare on brew.

# Brew
 - **Brew(Auto)**: All pressure settings are following the below:
   - **PREINFUSION**: Enables pre-infusion
     - **Time**: Sets the length of the PI phase
     - **Bar**: Sets the max reachable pressure for the PI phase
     - **Soak**: Sets the length of the soaking (blooming) phase
     - **Ramp**: Sets the length of the pressure ramping phase, PI to PP windup time.
   - **P-PROFILING**: Enables AUTO pressure profiling mode
     - **Start**: Sets the desired starting point of the PP phase, can be High->Low or Low->High.
     - **Finish**: Sets the desired finish point of the PP phase, same as above can be from High->Low or Low->High.
     - **Hold**: Sets the length of the PP hold period, if it's desired to maintain the "Start" pressure for a period of time before the pressure drop/raise is applied this is where it's done.
     - **Length/Slope**: Sets the length (aka curve speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.

**Here is a classic pre-example of how a declining pressure profile can be used once the mod is installed.**

![PressureGraph](https://user-images.githubusercontent.com/109426580/204081504-90cd4961-5a0f-4911-b4db-00411437ff2f.png)
 - **Brew(Manual)**: Allows for manual pressure control at brew time.

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
  5. Wait about 30 minutes, checking for an empty water tank.
  6. Once the descaling solution and water mix runs out fill the reservoir with clean fresh water. 
  7. The pump should auto prime and continue the cleaning procedure.
  8. A **FINISHED** message will popup when descaling finishes.

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
