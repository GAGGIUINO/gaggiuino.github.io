# MCU Flashing

## Software Prerequisites:
<!-- tabs:start -->
<!-- tab:Gen 3 -->
For wired flashing - required for BlackPill-based PCBs (PCBv2, PCBv3) and PCBv3.1:  
* [STM32 Cube Programmer](https://www.st.com/en/development-tools/stm32cubeprog.html) *(Email signup required)*

<!-- tab:Gen 2 -->
1. Install/Update [VSCode](https://code.visualstudio.com/)
2. Install/Update [Platform IO](https://platformio.org/) 
3. Install [Git](https://www.git-scm.com/)
4. Install [STM32 Cube Programmer](https://www.st.com/en/development-tools/stm32cubeprog.html) *(Email signup required)*

Then pull the code as shown in the below video:
<details>
<summary>Setup project using PIO (Click to expand)</summary>

[Platform IO](https://user-images.githubusercontent.com/109426580/193900425-15c42d9c-adf4-4073-aa46-34874528bf43.mp4 ':include :type=video controls width=70%')
</details>

Make sure to switch to the necessary [release branch](#Releases) once pulled, depending on the target platform (nano or STM32). For STM32 the recommended upload method is by using a physical ST-Link or WeAct Mini Debugger.
<!-- tabs:end -->

# Releases

<!-- tabs:start -->
<!-- tab:Gen 3 -->

> [!Warning|style:callout|label:Warning|iconVisibility:visible]
> __1. Gaggiuino Gen 3 (NextMonday&trade;) is *NOT* compatible with Nextion screens.__  
> __2. Failing to flash the correct binary for your hardware will yield unexpected results.__   
> __3. Make sure the microcontroller and screen unit are in sync.__  

Released binary (.bin) files can be found on the [Gaggiuino Github Releases](https://github.com/Zer0-bit/gaggiuino/releases) page. Files selection depends on your system hardware.
  * Core (STM32): 1 file, named in format *MCU - Build Type - LED Controller .bin* per hardware (see table below).  
   _MCU_                                    | *Build Type*                  | *LED Controller*     |  
   :---------------------------------------:|:-----------------------------:|:--------------------:|  
   __performance__<br/>*STM32**U585**CIU6*  |**pcb**<br/>*PCBv2 - PCBv4*    |**ncp**<br/>*NCP5623* |  
   <br/>*STM32**F411**CEU6*                 |**lego**<br/>*Component build* |**pca**<br/>*PCA9632* |  
  * UI (ESP32)
    * Screen: *ui-embedded.bin* and *ui-web.bin*  
    * Headless: *ui-headless.bin* and *ui-web.bin* 

> [!Note|style:callout|label:Note - Extra Defines Eliminated] 
> * Those without an LED module can use either ncp or pca firmware as ToF presence/absence and LED absence are recognized automatically. 
> * Predictive, hardware, and Bluetooth scales are enabled/disabled via the UI  

<!-- tab:Gen 2 -->

> [!Warning|style:callout|label:Warning|iconVisibility:visible]
> __1. Gaggiuino Gen 2 (Nextion UI) is *NOT* compatible with PCBv4 / STM32U585CIU6.__  
> __2. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __3. Make sure the microcontroller and screen unit are in sync. When in doubt, flash both.__  

Files are at [release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)

<!-- tabs:end -->
>

# Flashing
<!-- tabs:start -->
<!-- tab:Gen 3 -->
## Wired - STM32 / BlackPill

Make sure you have necessary [Software Prerequisites](#software-prerequisites) installed.

> [!Warning|style:callout|label:Warning|iconVisibility:visible]
> * BlackPill-based PCBs (PCBv2, PCBv3) and PCBv3.1 should be flashed using STM32CubeProgrammer with **machine power off** unless [PA15 pulldown functionality ](guides-upgrade/pcb-upgrade.md#pa15-pulldown-upgrade) has been verified. Otherwise, the boiler heaters may turn on while the STM32 is connected or flashing.  
> * If your ST-Link doesn't work with STM32CubeProgrammer try using the old [ST-Link utility](https://www.st.com/en/development-tools/stsw-link004.html)

1. Identify the core file to flash from [Releases](#Releases). 

2. Open STM32CubeProgrammer and in the **Erasing & programming** pane (A) browse to and select the *MCU - Build Type - LED Controller .bin* that corresponds to your system using the **File path** input (B).  
Make sure **Verify programming** is selected and **Skip flash erase before programming** is not selected.  

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/fee8093d-cabe-4158-bfdf-40ce2cc233a3">

3. If you haven't already done so, connect the PCB or BlackPill<sup>1</sup> to the WeAct Mini Debugger or ST-Link (connect 3.3V, SWDIO, SWCLK, and GND). Note that the pictures show *only* this connection for clarity.

  <img height="300" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/58377fd5-49f2-47f2-98d6-7c800eb6e712">  

  <img height="300" alt="image" src="https://user-images.githubusercontent.com/117388662/262874364-c44f2eea-6a64-4731-adb8-a0c1a16089d6.png">

    <sup>1 *Pins should be on the back of the BlackPill for PCBv3 compatibility*</sup>  

4. Connect the WeAct Mini Debugger / ST-Link USB to the computer (the PCB or BlackPill USB-C port should **not** be connected).

5. In the STM32CubeProgrammer **Erasing & programming** pane click **Connect** (D). Once connected, click **Start Programming** (E).

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/13df020c-9989-4ae9-ac7b-abaf5ce19d6c">

6. Acknowledge the success messages and click **Disconnect**. Once disconnected, unplug the WeAct Mini Debugger / ST-Link USB from the computer.

## OTA - ESP32, STM32U585

> [!Warning|style:callout|label:Warning|iconVisibility:visible]
> * ESP32 systems **must be enabled by official suppliers** to work with Gaggiuino Gen 3.  
> * Core OTA is compatible with STM32**U585** (PCBv4 and PCBs with custom uPill) only. Sometimes those PCBs may need to be flashed with STM32CubeProgrammer - this will be stated in the release notes if necessary. 

1. Identify the file(s) to flash from [Releases](#Releases).  

2. If your Gaggiuino is not on your local network, connect to Gaggiuino AP.  
The password is the network name with a zero substituted for the "o" and the space removed.

  <img width="300" alt="image" src="https://github.com/user-attachments/assets/af24bb4e-1608-4b45-b78d-ccb7d15bec18">

3. Navigate to [gaggiuino.local](http://gaggiuino.local/)

4. Select the SETTINGS page and scroll down to the **OTA Update** section.

  <img width="300" alt="image" src="https://github.com/user-attachments/assets/0c7114ec-6e85-4894-bfc8-d779a8de38b5">

5. Select **Core Upgrade Package** for core (STM32U585) files, or **LCD Upgrade Package** for UI (ESP32) files. Click **SELECT FILE**, select the file to flash, then click **UPLOAD**.

  <img width="300" alt="image" src="https://github.com/user-attachments/assets/f70a4726-daa2-459b-aacc-4167444edf87">

> [!Note|style:callout|label:File Order|iconVisibility:visible]
> Flash files in the following order unless otherwise noted in the release notes:
> * *ui-embedded.bin* / *ui-headless.bin*
> * *ui-web.bin*
> * core file (per hardware)  

6. Wait for the upload, flash process, and reboot. The screen will be black during these operations. 

  <img width="300" alt="image" src="https://github.com/user-attachments/assets/ae9f802d-d9a1-4b26-a504-dbecb29cdab7">

7. After a successful upgrade, click **START OVER** and begin again from step 5 to flash additional files. 

  <img width="300" alt="image" src="https://github.com/user-attachments/assets/faba0d3e-15fd-4324-a28f-f170c0950757">


> [!Note|style:callout|label:Notes|iconVisibility:visible]
> * Do not power down the system during an update. If an update fails or is cancelled before completion the system will automatically revert to the previous firmware.  
> * After a *ui-web.bin* update the browser may need to be refreshed to load new elements (if any). 

<!-- tab:Gen 2 -->
## STM32 / BlackPill
  
Make sure you have necessary [Software Prerequisites](#software-prerequisites) installed, and any applicable extra defines entered and saved in `extra_defines.ini` before starting. Do not have STM32 Cube Programmer open if uploading via VS Code.

>[!Tip]
>extra_defines.ini is used for accessories and other special functions. You do not need one for the base install.

1. Select the environment based on the upload method:
    - **Lego** if you have individual components, **PCB** if you have one.
    - **forced-predictive** if you don't have hardware scales
    - **STlink** if you are using an ST-Link or the WeAct Mini Debugger, **DFU** if not (deprecated).
2. Click "Build" in VSCode (PlatformIO tab)

  <img width="300" alt="image" src="https://github.com/Loogl3/gaggiuino.github.io/assets/117388662/0ba13397-65b5-4b8f-b528-c41bf547266f">

3. Connect the PCBv3.1 or BlackPill<sup>1</sup> to the WeAct Mini Debugger or ST-Link (connect 3.3V<sup>2</sup>, SWDIO, SWCLK, and GND)
  <img height="300" alt="image" src="https://github.com/GAGGIUINO/gaggiuino.github.io/assets/117388662/58377fd5-49f2-47f2-98d6-7c800eb6e712">  

  <img height="300" alt="image" src="https://user-images.githubusercontent.com/117388662/262874364-c44f2eea-6a64-4731-adb8-a0c1a16089d6.png">

4. Make sure the BlackPill/PCBv3.1 USB-C is **not** connected to anything
5. Connect ST-Link/WeAct Mini Debugger USB to the computer
6. Click Upload in VS Code (PlatformIO tab)
7. Wait until you see green/success logs

> [!Note|style:callout]
> *1 Pins should be on the back of the BlackPill for PCBv3 compatibility*  
> *2 Some ST-Links may have issues if 3.3V is connected and the system is powered through the 120/220 VAC PSU when flashing. If unsure about your ST-Link, only connect 3.3V if you'll turn off or disconnect AC power before flashing.*

## Nextion/TJC display

Flashing instructions:
1. On an otherwise-empty ≤32 GB FAT32 microSD card, copy the applicable *Brand*-*Type*-lcd.tft  
    - Brand: nextion or tjc  
    - Type: basic or discovery (Nextion Orange PCB)  

  <img width="300" alt="image" src="https://github.com/Loogl3/gaggiuino.github.io/assets/117388662/161ef925-94d1-4ae4-a332-8dd761b0c009">

  > [!Tip|label:Scales Calibration Files|style:callout]
  > Display files for scales calibration are in the "scales-calibration" folder
  
2. While **powered off**, put the microSD card in the display
3. Power on the display. When not installed in the machine, power for flashing may be provided through the USB-C port on the Blackpill/PCB. Use a USB power adapter rated for 5 VDC and 500+ mA.  
> [!Note|style:callout]
> Make sure the ST-Link is disconnected. Don't use it, a battery bank, or PC USB ports for power).  
4. Wait for the display to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.
<!-- tabs:end -->