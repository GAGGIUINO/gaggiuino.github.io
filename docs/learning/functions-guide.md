
> [!NOTE]
> This page is a work in progress.

# Functions and usage

 - **BOILER**: Sets the desired temperature at the boiler level
 - **OFFSET**: Sets the offset value used to calculate the real water temperature
 - **HPWR**: Sets the relay max pulse width
 - **M.C.DIV**: Sets the main cycle divider (aka non brew heating behaviour), used in conjunction with HPWR
 - **B.C.DIV**: Sets the brew cycle divider
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
 - **DESCALE**: Enables the descaling program.

    1. Descaling takes around 45-50mins.
    2. Fill up water tank fully loaded with water mixed with descale solution (possible 4-6tbsp citric acid per one tank of water).
    3. Should be done with a blind basket and porta-filter locked in the grouphead.
    4. Open the steam valve one full turn to allow the water to flow in a separate reservoir.
    5. About 30 minutes since starting the procedure the water tank should be nearly empty, once the descaling solution water mix runs out the pump pitch will change fill the reservoir with clean fresh water, the pump should prime itself in a few seconds and continue the cleaning procedure.
    6. A **FINISHED** message will popup when descaling finishes.

