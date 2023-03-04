# PREREQUISITES 
## Software requirements:
1. Install [VSCode](https://code.visualstudio.com/)
2. Install [Platform IO](https://platformio.org/)
3. Update [python](https://www.python.org/downloads/ ) to latest
4. Install [Git](https://www.git-scm.com/)
5. [Github](http://github.com) account required
6. [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)
7. [Cube Programmer](https://www.st.com/en/development-tools/stm32cubeprog.html)
    * Needed to install the necessary STM32 USB drivers so your system recognizes the STM chip
8. [Nextion Editor](https://nextion.tech/nextion-editor/)
    * Only necessary if planning on editing the ".HMI" file to amend the LCD functionality*
9. Restart machine

Then pull the code as shown in the below video:
<details>
<summary>Setup project using PIO (Click to expand)</summary>

[Platform IO](https://user-images.githubusercontent.com/109426580/193900425-15c42d9c-adf4-4073-aa46-34874528bf43.mp4 ':include :type=video controls width=70%')
</details>

Make sure to switch to the necessary branch once pulled, depending on the target platform (nano or stm). If using blackpill the recommended upload method is by using a physical STlink.

You select your environment based on your build and upload method i.e:
* **Lego** build if you have individual components, **PCB** if you have that.
* **STlink** if you are using one, **DFU** if not.

 