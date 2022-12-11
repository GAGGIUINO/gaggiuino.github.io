## Community Speaks

<!-- panels:start -->
<!-- div:left-panel -->
?> Nano install overview
<iframe width="560" height="315" src="https://www.youtube.com/embed/EJFadpL9aOE" title="GAGGIUINO BUILD LOG" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<!-- div:right-panel -->

?> Follow up review.
<iframe width="560" height="315" src="https://www.youtube.com/embed/Dm1uVyiZOOE" title="GAGGIUINO BUILD LOG" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<!-- panels:end -->

?> STM32 install overview.
<iframe width="560" height="315" src="https://www.youtube.com/embed/5-PWW3dbh1c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<details>

<summary><b>MORE FROM THE COMMUNITY</b> <i>(Click to expand)</i></summary>

<iframe width="560" height="315" src="https://www.youtube.com/embed/MxPNQRCxQZc" title="GAGGIUINO Upgrade Show" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</details>

<!-- panels:start -->
<!-- div:title-panel -->
## Functions and usage

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
     - **Length**: Sets the length (aka curve speed) of the PP drop/raise behaviour, so one can change the pressure slow or fast if desired.

**Here is a classic prexample of how a declining pressure profile can be used once the mod is installed.**

![PressureGraph](https://user-images.githubusercontent.com/109426580/204081504-90cd4961-5a0f-4911-b4db-00411437ff2f.png)


 - **Brew(Manual)**: Allows for manual pressure control at brew time.
 - **DESCALE**: Enables the descaling program.

  >Descaling should be done with a blind basket portafilter locked in the group, steam valve slightly open for the water to flow in a separate reservoir and water tank fully loaded with water mixed with descale solution.
  <!-- div:title-panel -->