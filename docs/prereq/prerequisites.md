## Software requirements:
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

Make sure to switch to the necessary branch once pulled, depending on the target platform (nano or stm). If using blackpill the recommended upload method is by using a physical STlink.

Select the environment based on the upload method i.e:
* **Lego** build if you have individual components, **PCB** if you have that.
* **STlink** if you are using one, **DFU** if not.

 