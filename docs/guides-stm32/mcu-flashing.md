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
  Arduino Nano    |[release-nano-final](https://github.com/Zer0-bit/gaggiuino/tree/release-nano-final)
  STM32 Blackpill |[release/stm32-blackpill](https://github.com/Zer0-bit/gaggiuino/tree/release/stm32-blackpill)

> [!TIP|style:callout|label:ADVICE|iconVisibility:visible]
> __1. Failing to run the right code branch on the chosen set of hardware will yield unexpected results.__   
> __2. Make sure you _ALWAYS_ flash both the microcontroller as well as the LCD unit.__   
> __3. Arduino Nano won't flash with the LCD attached to the RX/TX pins so make sure to disconnect it at that time.__

>

# Flashing

## STM32 Blackpill
  
Make sure you have necessary [Software Prerequisites](#software-prerequisites) installed, and any applicable extra defines entered and saved in `extra_defines.ini` before starting.

1. Select the environment based on the upload method:
    - **Lego** if you have individual components, **PCB** if you have one.
    - **forced-predictive** if you don't have hardware scales
    - **STlink** if you are using one, **DFU** if not (deprecated).
2. Click "Build" in VSCode (PlatformIO tab)

  <img width="300" alt="image" src="https://private-user-images.githubusercontent.com/117388662/289216600-9e089033-9489-4816-8477-698977b2ea60.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDIwODEzMTAsIm5iZiI6MTcwMjA4MTAxMCwicGF0aCI6Ii8xMTczODg2NjIvMjg5MjE2NjAwLTllMDg5MDMzLTk0ODktNDgxNi04NDc3LTY5ODk3N2IyZWE2MC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBSVdOSllBWDRDU1ZFSDUzQSUyRjIwMjMxMjA5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDIzMTIwOVQwMDE2NTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02Mjc2NTFmZDVlNWJhM2ExYjVhOWZkNzhlMzNmYTJjZjFmZjBlZTNiMDFlZGY0M2MxYzdhYmEzMjhjYzU4OWNkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.Bm8Er0F5N4gh7O3TCRYEPYRrlqOUqKkdy_YxeWzf50Q">

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

  <img width="300" alt="image" src="https://private-user-images.githubusercontent.com/117388662/289217784-3a204b92-879b-4f91-af6c-6c1ac7ac78de.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDIwODIyNzksIm5iZiI6MTcwMjA4MTk3OSwicGF0aCI6Ii8xMTczODg2NjIvMjg5MjE3Nzg0LTNhMjA0YjkyLTg3OWItNGY5MS1hZjZjLTZjMWFjN2FjNzhkZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBSVdOSllBWDRDU1ZFSDUzQSUyRjIwMjMxMjA5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDIzMTIwOVQwMDMyNTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01NTkyNDE2OGRhMDRkYzUyZDljZDJjNWFmZjMzYWEwNGI3OTU1MjJjZGM3NWQwNWM2MWVjYjRiZTUwY2FiNWVmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.bKmlZyoGGMCknnkv_aacCRapDmy5FBJqQhT5qebq6tg">

  > [!Tip|label:Scales Calibration Files|style:callout]
  > Display files for scales calibration are in the "scales-calibration" folder
  
2. While **powered off**, put the microSD card in the display
3. Power on the display. Power for flashing may be provided through the USB-C port on the Blackpill so long as the ST-Link USB is disconnected and you are using a USB power adapter that will supply 4.6-5.2 VDC (don't use a battery bank or PC USB 2.0 ports for power).  
4. Wait for the display to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.