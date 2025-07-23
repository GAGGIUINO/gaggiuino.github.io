# User Manual - Gen 3

> [!Warning|style:callout|label:Work in Progress|iconVisibility:visible]
> This manual (and Gaggiuino Gen 3) are a work in progress. Expect the manual to naturally lag feature releases.
> 
> The [Gen 2 User Manual](learning/user-manual-gen2.md) is linked in the [Archive](archive/archive.md).

# Getting Started

## Connecting to WebUI

The ESP32 can be connected to your local network, and will generate its own access point if it is not connected to a network. WebUI is located at [gaggiuino.local](http://gaggiuino.local/).

* **Access point<sup>1</sup>:**  
  Select Gaggiuino AP<sup>2</sup> on a WiFi-capable device. The password is the network name with a zero substituted for the "o" and the space removed.  
  <img width="300" alt="image" src="https://github.com/user-attachments/assets/af24bb4e-1608-4b45-b78d-ccb7d15bec18">  

* **Network:**  
  Go to "Settings" tab (WebUI) or gear icon (screen), select "System" and click "Connect" to select a 2.4 GHz Wi-Fi network and enter the password<sup>3</sup>. 

> [!Note|style:callout|label:Notes|iconVisibility:visible]
> 1 - Gaggiuino can be used in access point mode, but shot history times will be inaccurate because it won't have access to a time server.  
> 2 - The network name may initially be ESP_xxxxxx instead of Gaggiuino AP. The password is based on Gaggiuino AP, and the access point name should become Gaggiuino AP after connecting and disconnecting from a network.  
> 3- if a special character is unavailable on the on-screen keyboard, connect to the access point and enter the password through WebUI.

## Initial Startup

* Fill the boiler by enabling Flush and running the system until water comes out of the group head for 5+ seconds.  
* If your pressure transducer is connected via a T-Fitting, run the utility profile **[UT] Tube Fill**.
* Test pressure by inserting a portafilter with a blank basket and running **[UT] Test OPV**. Confirm:
  * Max pressure is 10.5-13 bar
  * Water is moving through the OPV tubing
  * No leaks are present

> [!Note|style:callout|label:Community Profiles|iconVisibility:visible]
> Utility profiles can be downloaded from Community Profiles in WebUI or [Github](https://github.com/Zer0-bit/gaggiuino/tree/community/profiles).  

## Gaggiuino Tips

* If Brew Delta is enabled, the boiler will be used like a thermoblock, adding heat based on flow rate to maintain the target water temperature at the puck. As the thermocouple is attached to the boiler it will not match the output temperature, so the plot is capped at the target temperature. When returning to the home page you may see the high boiler temperature; wait for it to settle before pulling another shot. 
* Do not expect Gaggiuino shot settings to behave the same as the stock machine. 
  * Temperature with Brew Delta will be much more stable during the shot than the stock machine (or even PID mods), so the resulting average temperature will be higher.  
  * Pre-infusion and soak increase flow significantly during the extraction phase(s). Dialing-in should be done per-profile, and grind will typically be finer than with a stock machine.
* If stop-on-weight is enabled, the shot will predictively stop ahead of the target weight to account for what hasn't hit the cup yet - the espresso in the air and the last bit that comes out of the puck as the shot is stopped and pressure equalizes.

> 

# UI Descriptions

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Home embedded" src="manual/gen3/mbed/001_000_home.png">
<!-- tab:Web UI -->
<img alt="Home web" src="manual/gen3/web/001_000_home.png">
<!-- tabs:end -->

- **Home**: Navigate to the [Home](/learning/user-manual-gen3.md#Home) screen.

- **Settings**: Navigate to the [Settings](/learning/user-manual-gen3.md#Settings) screen.

- **Shot History**: Navigate to the [Shot History](/learning/user-manual-gen3.md#ShotHistory) screen. Shot History can also be accessed by swiping up on the screen. 

- **Profile Preview**: Shows a preview of the selected profile.

- **Profile Selection**: Shows the available profiles. The active profile is highlighted in color (e.g. 'IUIUIU Classic'). The field can be swiped horizontally, to access additional profiles.

- **Edit Profile**: Edit and create new profiles.

- **Save Profile**: Save the current profile (e.g. after changing the brew temperature, shot weight). This also saves the currently selected profile, as the startup profile.

- **Temperature**: Current boiler temperature in Celsius. 

- **Target Temperature**: Water temperature from the current profile or the Steam Temperature from Boiler Settings if the Steam switch is active.

    > [!Note|style:callout|label:Changing and Saving|iconVisibility:visible]
    > On the Embedded UI, the Target Temperature can be temporarily changed by pressing and holding the temperature and swiping up or down.  Pressing Save will update the current profile's Water Temperature (or the Steam Temperature from Boiler Settings if the Steam switch is active).

- **Target Temperature**: Target temperature of the current profile. On the Embedded UI the setpoint temperature can be changed by swiping up or down on it.

- **Pressure**: Shows the current system pressure in Bar.

- **Tank level**: If an [TofnLED](/accessories/tofnled.md) is installed, the current water level in the water tank is shown in percent. When the water level is below 20%, a notification is displayed to fill the water tank. When no TofnLED board is installed, the graph permanently shows the maximum water level.

- **System uptime**: Shows for how long the machine has been switched on.

- **Shot weight**: Shows the shot weight in grams for the current profile. On the embedded UI the weight can be adjusted temporarily in 1g increments by tapping the '+' and '-' buttons or by tapping the weight field and using the number pad.

- **Weight**: If hardware scales are installed or Bluetooth scales connected, the current weight of the scales is shown in grams. The scales can be tared by tapping the current weight field. 

    > [!Note|style:callout|label:Scales Auto-tare|iconVisibility:visible]
    > The scales tare automatically when a shot is started.

- **Flush**: Tap the flush button to activate flush mode. The grey circle inside the button will light up green. Flushing can now be activated with the **brew** switch. Tap the flush button again to deactivate flush mode.
Tap and hold the button to perform a 5s flush. The grey circle will light up blue. The flush can be stopped by tapping the button again.

- **Descale**: Descale the machine.

# Cleaning 

### Back flushing

1. Insert a blind basket into the portafilter.
2. *OPTIONAL* Remove shower screen and add Cafiza to blind basket.
3. Lock the portafilter into the group head. 
4. Activate flush mode by tapping the flush button and press the **brew** switch. 
5. Let the machine perform multiple cycles.
6. Turn off the **brew** switch. Tap on the flush buttom to deactivateflush mode.

### Descaling

1. Empty the drip tray.
2. Fill the water tank up to the 'max' line with descale solution (i.e. water and citric acid). 
3. Lock a portafilter with a blind basket into the group head. 
4. Place a sufficiently big container under the steam wand (2l). 
5. Open the steam wand a quarter turn. 
6. Activate the descale mode by tapping the descale button (the circle inside will turn green). Press the **brew** switch. The machine will run through the descale cycle until the tank is empty. This will take around 30 minutes. 
7. When the tank is empty, turn off the **brew** switch. Take out the tank, clean it and fill it with clean fresh water to the 'max' line to rinse the machine. 
8. Start the descale cycle again by pressing the **brew** switch.
9. Wait until the tank is empty. 
10. The descaling was successful.

If the TofnLED board is installed, the descale cycle will stop automatically when the tank is empty.

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Descaling embedded" src="manual/gen3/mbed/001_004_descale.png">

- **Pause:** Pause the descaling.
<!-- tab:Web UI -->
<img alt="Shot in progress web" src="manual/gen3/web/001_004_descaling.png">

- **Elapsed time:** Shows for how long descaling has been active.
<!-- tabs:end -->

- **Descaling phase:** Shows the current descaling phase. During descaling the machine will cycle multiple times through all descaling phases.
- **Progress bar:** The progress of the descaling.
- **Close:** Close the descale progress view. (The descaling will continue.)

# Shot in progress

When a shot is started the live data is displayed. The time axis scales automatically. If hardware or Bluetooth scales are present the weight in the cup is shown, otherwise weight is calculated with predictive scales.

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Shot in progress embedded" src="manual/gen3/mbed/001_001_shot_in_progress.png">

- **Tare:** (Hardware and Bluetooth scales are tared automatically when a shot is started.) Tare the scales by tapping the circle in the top right hand corner of the screen. If you are using predictive scales and weight is greater than 0g, even though there is no liquid in the cup, press the tare button when the first drops land in the cup.
<!-- tab:Web UI -->
<img alt="Shot in progress web" src="manual/gen3/web/001_001_shot_in_progress.png">
<!-- tabs:end -->

# Shot History

> [!Note|style:callout|label:Requirements|iconVisibility:visible]
> * A microSD card is required to record and display shot history.
> * Gaggiuino must be connected to the internet with the time offset set to properly display the date and time

The recorded shot graphs are shown in a list. The shots are shown with a serial number, name, date and time and duration. Tap on an entry in the available shots to view a shot graph.

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Shot history embedded" src="manual/gen3/mbed/001_002_shot_history.png">

- **Older shots:** Tap on the right arrow key to load older shots.
- **More recent shots:** Tap on the left arrow key to load more recent shots.
<!-- tab:Web UI -->
<img alt="Shot history web" src="manual/gen3/web/001_002_shot_history.png">

- **Load more:** Tap on the button to load older shots.
<!-- tabs:end -->

### Shot Graph 

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Shot graph embedded" src="manual/gen3/mbed/001_003_shot_review.png">

<!-- tab:Web UI -->
<img alt="Shot graph web" src="manual/gen3/web/001_003_shot_review.png">

- **Menu:** Tap on the icon to open the menu.
- **Name and date:** Shows the name of the profile and the date the shot was recorded.
- **Download shot graph:** Download the shot graph data (.json).
- **Upload to sprofiler.io:** Upload your shot to [SproFiler](https://sprofiler.io). For instructions on how to register and use SproFiler, join the [Gaggiuino Discord](https://discord.com/channels/890339612441063494/1289578499581149204).
<!-- tabs:end -->

- **Delete shot graph:** Tap the icon to delete the currently viewed shot graph.
- **Home:** Return to the home screen.

# Settings

### Boiler

<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings embedded" src="manual/gen3/mbed/003_000_settings_boiler.png">

<!-- tab:Web UI -->
<img alt="Settings web" src="manual/gen3/web/003_000_settings_boiler.png">
<!-- tabs:end -->

- **Steam Temperature [°C]:** Set the default temperature for steaming. This setting applies for all profiles.
- **DreamSteam:** When enabled, fresh water is pumped into the boiler during steaming (Not recommended for machines with bigger boilers, like the Rancilio Silvia).
- **Temperature Offset [°C]:** If you have a device (e.g. Scathe) that can measure the temperature at the group head/portafilter accurately, you can adjust this value for more accurate brew temperature.
- **Brew Delta:** When enabled, the boiler temperature during shots will increase based on flow rate to more quickly transfer heat to the incoming cool water. Higher flow rates during a shot result in higher boiler temperature after the shot, which should settle before pulling the next shot. 
- **Advanced:** 
    > [!Warning|style:callout|label:Warning|iconVisibility:visible]
    > Only change these values if you have a non-Gaggia machine.
    - *HPWR:* Relay max pulse width (**H**igh **P**eak **W**idth **R**esolution).
    - *Main Divider:* Main cycle divider (aka non brew heating behavior), used in conjunction with HPWR.
    - *Brew Diviver:* Brew cycle divider.


### System
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings embedded" src="manual/gen3/mbed/003_002_settings_system.png">

<!-- tab:Web UI -->
<img alt="Settings web" src="manual/gen3/web/003_002_settings_system.png">

- **(Experimental) brewiu.io/sprofiler.io API key:** Reqiured to upload your shot to [SproFiler](https://sprofiler.io). For instructions on how to register and use SproFiler join the [Gaggiuino Discord](https://discord.com/channels/890339612441063494/1289578499581149204).

<!-- tabs:end -->

- **Pump Zero [ml]:** Amount of water pumped per cycle. 
- **Timezone offset [min]:** Set an offset for your current time zone.
- **WiFi:** Connect your Gaggiuino to a local WiFi network. If Gaggiuino is connected to the Internet, it will retrieve the current date and time. If Gaggiuino is not connected to a network, it acts as a WiFi access point named: *Gaggiuino AP*. The password is the network name with a zero substituted for the "o" and the space removed.

### Display

### LCD Settings
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings embedded" src="manual/gen3/mbed/003_003_settings_display.png">
<!-- tab:Web UI -->
<img alt="Settings embedded" src="manual/gen3/web/003_003_settings_display.png">
<!-- tabs:end -->

- **Brightness:** Adjust the brightness of the LCD screen.
- **LCD Sleep [min]:** Set a time after which the display goes into sleep mode. Wake up the screen by tapping it.

### Theme and Accents
- **Dark mode:** Enable a dark color scheme for the UI.
- **Theme:** Choose a color scheme for the UI.
- **Accent:** Choose an accent color for the UI.

### Scales

### Hardware Scales
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings scales embedded" src="manual/gen3/mbed/003_004_settings_scales.png">
<!-- tab:Web UI -->
<img alt="Settings scales web" src="manual/gen3/web/003_004_settings_scales.png">
<!-- tabs:end -->

- **Enabled:** Enable hardware scales if installed.
- **Calibration Factor:** Calibration factors for the to load cells. The calibration factors can be determined via the Web UI. Detailed instructions on how to calibrate the scales can be found [here](https://gaggiuino.github.io/#/accessories/hw-scales?id=flashingcalibration).

### Bluetooth Scales
- Enabled: Enable Bluetooth scales. A list of supported scales can be found [here](https://github.com/kstam/esp-arduino-ble-scales).

### Force Predictive Scales
- Enabled: Values from HW scales are ignored. The machine will stop on weight by the weight it has calculated during extraction.

## LED
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings LED embedded" src="manual/gen3/mbed/003_005_settings_led.png">
<!-- tab:Web UI -->
<img alt="Settings LED web" src="manual/gen3/web/003_005_settings_led.png">
<!-- tabs:end -->

- **Enable:** Enable the LED light if installed.
- **Brew Disco/Disco mode:** Brew in style.
- **LED Color:** Choose the LED color and brightness.

## About / Update
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Settings about embedded" src="manual/gen3/mbed/003_006_settings_about.png">

- **Firmware Versions:** Shows the firmware versions of the MCU (Core), Embedded UI, i.e. the screen/headless module (Mbed) and Web UI (Web).
<!-- tab:Web UI -->
<img alt="Settings update web" src="manual/gen3/web/003_006_settings_ota_update.png">

- **Over The Air (OTA) update:** Detailed instructions on how to update your Gaggiuino can be found [here](https://gaggiuino.github.io/#/guides-stm32/mcu-flashing).
- **Firmware Versions:** Shows the firmware versions of the MCU (Core), Embedded UI, i.e. the screen or headless module (Mbed) and Web UI (Web).
<!-- tabs:end -->

## Save changes

If you have made a change to the settings, a save icon will appear in the left hand corner of the screen. If you tap the icon a notification will be displayed saying "Settings persisted". Note: It is not necessary to save after every change. Saving once after making all the changes is sufficient.

# Profiles 
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Profiles embedded" src="manual/gen3/mbed/002_000_profiles.png">

- **Available profiles:** Tap on a name to select the active profile (a preview of the selected profile is shown). The selected profile is highlighted in color. 
<!-- tab:Web UI -->
<img alt="Profiles web" src="manual/gen3/web/002_000_profiles.png">

- **Available profiles:** Tap on a name to select the active profile (a preview of the selected profile is shown). The selected profile is highlighted in color. To change the order of the profiles, tap the 4 lines and drag the profile to the desired position in the list. 
- **Import:** Import a profile. The default and additional profiles can be downloaded from the [Gaggiuino Discord](https://discord.gg/gaggiuino). 
- **Stop conditions:** The selected option is highlighted in color. 
- **Duplicate:** Create a copy of the selected profile.
- **Export:** Exports a profile as a json file, so it can be easily shared. 
<!-- tabs:end -->

- **Active profile:** Name of the activate profile. 
- **New:** Create a new profile from scratch. 
- **Edit profile:** Edit the selected profile. 
- **Delete:** Delete a profile permanently. 


# Edit profile

## Global profile settings
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Profiles global settings embedded" src="manual/gen3/mbed/002_001_profiles_edit_global_settings.png">
<!-- tab:Web UI -->
<img alt="Profiles global settings web" src="manual/gen3/web/002_001_profiles_edit_global_settings.png">
<!-- tabs:end -->

- **Name:** Edit the profile name.
- **Save changes:** Saving once after making all the desired changes is sufficient. Saving applies to all changes. 
- **Close:** Exit profile editing.
- **Preview:** A preview of the profile. The phase that is currently viewed is indicated by background color (embedded UI) or thicker lines (web UI) for temperature, flow and pressure. 
- **Stop on:** Condition that stops the shot: Shot weight (e.g. 36g), total time after pressing the brew button (e.g. 35s) or amount of water pumped (e.g. 60ml). 
- **Switch to phase:** Switches to a different phase (e.g. next phase, previous phase).
- **Global profile settings:** Go to the global profile settings. 
- **Add phase:** Add a phase after the phase you are currently viewing. 
- **Delete phase:** Delte the phase you are currently viewing. 
- **Water temp [°C]:** Target shot temperature.

## Phase settings
<!-- tabs:start -->
<!-- tab:Embedded UI -->
<img alt="Profiles phase settings embedded" src="manual/gen3/mbed/002_002_profiles_edit_phase.png"> 

<!-- tab:Web UI -->
<img alt="Profiles phase settings web" src="manual/gen3/web/002_002_profiles_edit_phase.png"> 
<!-- tabs:end -->

- **Phase characteristic:** Either the configured pressure or flow are the target for the phase. The target/primary variable is displayed as a solid line while the secondary variable is a dotted line. 

### Targets
- **Adaptive:** Adapts the start of the next phase to match the actual end value of the previous phase. Example: Phase 1 of a profile targets 4 bar of pressure for 10 seconds. Phase 2 is a linear ramp from 4 to 7 bar over 10 seconds. During brewing phase 1 only reaches 2 bar. Adative option will change the ramp to match the real-time conditions, to have a smooth transition into phase 2. Practically this results in a linear ramp from 2 bar to 7 bar over the specified 10 second time interval.
- **Target:** Either flow [ml/s] or pressure [bar] target, depending on selection. 
- **limit:** If the phase characteristic is set to flow, the pressure won't exceed the limit value, to reach the desired flow and vice versa. 
- **Time [s]:** Transition to the next phase of the profile after the configured time if no stop condition is selected or met. 

### Stop conditions

If a stop condition is configured and triggered, the profile transitions to the next phase. If no stop conditions is configured or triggered, the profile transitions to the next phase after the configured time.

- **Pressure above [bar]:** Switch to the next profile phase if the pressure exceeds the configured value.
- **Pressure below [bar]:** Switch to the next profile phase if the pressure drops below the configured value. 
- **Flow above [ml/s]:** Switch to the next profile phase if the flow exceeds the configured value. 
- **Flow below [ml/s]:** Switch to the next profile phase if the flow drops below the configured value. 
- **Weight change [g]:** Switch to the next profile phase if the weight in the cup exceeds the configured value. 
- **Water pumped [ml]:** Switch to the next profile phase if the amount of water pumped exceeds the configured value. 

### Transition
- **Curve**: Choose a transition curve for the profile stages. 
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

