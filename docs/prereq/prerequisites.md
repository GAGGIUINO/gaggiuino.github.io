## **REQUIREMENTS** 
### **Software requirements:**
1. [Arduino IDE](https://www.arduino.cc/en/software)
    >*Needed to upload the code ".ino" to the arduino ROM*


   **Libraries to [add](https://www.arduino.cc/en/Guide/Libraries?setlang=en):**
   
         Library manager:
          - Easy Nextion Library
          - MAX6675 by Adafruit
          - TimerInterrupt_Generic


         External libraries:
          - PSM > https://github.com/banoz/PSM.Library
          - HX711 > https://github.com/banoz/HX711


2. [Nextion Editor](https://nextion.tech/nextion-editor/)
    >*Only necessary if planning on editing the ".HMI" file to ammend the LCD functionality*
3. [CH340 USB Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)
    >*USB driver so your system recognizes the Arduino clone board, let's say i have found this the hard way as apparetly the majority of cloned arduinos use a cheaper USB controller comparing to "genuino"*