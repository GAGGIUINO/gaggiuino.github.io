# MCU Flashing

## Software Prerequisites:
1. Install/Update [VSCode](https://code.visualstudio.com/)
2. Install/Update [Platform IO](https://platformio.org/) 
3. Install [Git](https://www.git-scm.com/)
4. Drivers (select per your build type)
    * STM32 USB/ST-Link [Cube Programmer](https://www.st.com/en/development-tools/stm32cubeprog.html)
    * Arduino Nano [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)

Then pull the code as shown in the below video:
<details>
<summary>Setup project using PIO (Click to expand)</summary>

[Platform IO](https://user-images.githubusercontent.com/109426580/193900425-15c42d9c-adf4-4073-aa46-34874528bf43.mp4 ':include :type=video controls width=70%')
</details>

Make sure to switch to the necessary [release branch](#Releases) once pulled, depending on the target platform (nano or stm32). If using blackpill the recommended upload method is by using a physical ST-Link.

# Releases

  MCU             |                               Code branch         
------------------|------------------------------------------------------------------------------------
  Arduino Nano    |[release-nano-final-v4](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final-v4)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

>

# Flashing

## STM32 Blackpill
  
Make sure you have necessary [Software Prerequisites](#software-prerequisites) installed, and any applicable extra defines entered and saved in `extra_defines.ini` before starting.

>[!Tip]
>extra_defines.ini is used for accessories and other special functions. You do not need one for the base install.

1. Select the environment based on the upload method:
    - **Lego** if you have individual components, **PCB** if you have one.
    - **forced-predictive** if you don't have hardware scales
    - **STlink** if you are using one, **DFU** if not (deprecated).
2. Click "Build" in VSCode (PlatformIO tab)

  <img width="300" alt="image" src="https://github.com/Loogl3/gaggiuino.github.io/assets/117388662/0ba13397-65b5-4b8f-b528-c41bf547266f">

3. Connect the Blackpill to the ST-Link<sup>1</sup> (connect SWDIO, GND, SWCLK, and 3.3V<sup>2</sup>)

  <img width="300" alt="image" src="https://user-images.githubusercontent.com/117388662/262874364-c44f2eea-6a64-4731-adb8-a0c1a16089d6.png">

4. Make sure the Blackpill USB-C is **not** connected to anything
5. Connect ST-Link USB to the computer
6. Click Upload in VS Code (PlatformIO tab)
7. Wait until you see green/success logs

> [!Note|style:callout]
> *1 ST-Link pins should be on the back of the Blackpill for PCBv3 compatibility*  
> *2 If the system is powered through the 120/220 VAC PSU then only connect 3.3V to the ST-Link if you're sure you have a genuine ST-Link or WeAct Mini Debugger.*

## Nextion/TJC display

Flashing instructions:
1. On an otherwise-empty ≤32 GB FAT32 microSD card, copy the applicable *Brand*-*Type*-lcd.tft  
    - Brand: nextion or tjc  
    - Type: basic or discovery (Nextion Orange PCB)  

  <img width="300" alt="image" src="https://github.com/Loogl3/gaggiuino.github.io/assets/117388662/161ef925-94d1-4ae4-a332-8dd761b0c009">

  > [!Tip|label:Scales Calibration Files|style:callout]
  > Display files for scales calibration are in the "scales-calibration" folder
  
2. While **powered off**, put the microSD card in the display
3. Power on the display. Power for flashing may be provided through the USB-C port on the Blackpill so long as the ST-Link USB is disconnected and you are using a USB power adapter that will supply 4.6-5.2 VDC (don't use a battery bank or PC USB 2.0 ports for power).  
4. Wait for the display to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.