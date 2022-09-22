
# Scales

The scales functionality will require two load cells and a rigid frame that need to support the drip tray. In short, you are going to measure the weight of the drip tray + cup + espresso. Here are some terms used throughout the server:
- Single Clock = Both HX711 amplifiers will share one SCK line from the MCU (one SCK pin coming from MCU).
- Dual Clock = Each HX711 amplifier will have an independent SCK line supplied by the MCU (2 SCK pins coming from MCU).
- Twin-board - Two HX711 amplifiers on a single, compact PCB (designed by VAS).

For scales to function properly, the following hardware will be needed:

- [2x 500g Load Cells](https://www.aliexpress.com/item/32670225988.html)
- [2 x HX711 Amplifiers](https://www.aliexpress.com/item/32670225988.html)
- (STM32 ONLY) 1 kΩ resistor[^1] x the number of clock lines you plan on using.

[^1]: The addition of this resistor is credited to Havald.

**OPTIONAL** (needed for weight based pump control)
- [5V Relay x 1](https://a.aliexpress.com/_vpUdrT) (Deprecates the existing opto-coupler for the GC. **Needed for all that want weight-based pump control**)

A stable, rigid frame to mount the load cells is highly recommended. You can create your own mounting frame, but likeablebump has a few designs on thingiverse that have been used by others. Your frame needs to be able support (lift) the drip tray.

- [GC Load Cell Integration - no drill](https://www.thingiverse.com/thing:5276489)
- [GCP Load Cell Integration - no drill](https://www.thingiverse.com/thing:5276492)
- [GCP Load Cell Integration single HX711 board - no drill](https://www.thingiverse.com/thing:5276496)


## Wiring Load Cell to HX711

![Wiring the HX711 amplifier to load cell.](https://user-images.githubusercontent.com/80347096/186999709-377d2e57-76c5-498f-8ba1-57ffd8230b70.jpg)

A wiring diagram for typical load cells is shown in the above figure. The connections DT and SCK will need to interface with the MCU while VCC is +5VDC and GND is low-voltage ground.

## Load Cell Frame

This section shows a typical load frame cell setup using one of likeablebump's design. The idea remains the same if you chose to create your own rigid frame. You need to "lock'' the load cell to the frame using the rear mounting screws (M3 screws will work if you purchase the 500g load cells from AliExpress). The load cell needs to have a gap between it and the rigid frame. An extension piece is locked to the top of the load cell to give the load cell better leveraging.

The figure below shows the M3 screws locking the load cell to frame and leverage extension.
![Locking load cell to frame and leverage extension.](https://user-images.githubusercontent.com/80347096/186999854-024d76ba-9c30-4cf8-9f71-3587203d2789.jpg)



A side-view of the load cell attached to the frame and the top-extension leveraging piece is highlighted below.  

![Load cell mounted to frame.](https://user-images.githubusercontent.com/80347096/186999950-1f202fb7-aff7-4c2e-bfd7-46d9ab5c4fb4.jpg)


Once you lock the load cells to the rigid frame, you need to connect the HX711 amplifiers to the MCU (nano or STM32). The figure below shows one-half of a "single-clock" 5-pin magnetic POGO connector.

![5-pin POGO load cell connector.](https://user-images.githubusercontent.com/80347096/187000042-e6149235-6e99-4d73-8230-2d949f747af2.jpg)


The POGO connector snaps onto the mating POGO connector inside the tank riser piece as shown in the figure below. 

![5-pin POGO load cell connector mating image.](https://user-images.githubusercontent.com/80347096/187000103-bb95adbe-b790-4616-bea2-fd64c117cf64.jpg)

**Please note that this is only ONE method to "easily" connect and disconnect the scales hardware for tank removal.**


## Software/Hardware Integration

### SINGLE Clock MCU wiring
| nano pin    	| HX711 Connection 1 	| HX711 Connection 2	  |
| :---:       	|    :----:          	|        :---:	        |
| 10          	| SCK             	   | SCK			           |
| 12          	| DOUT               	| -            		  |
| 13		      | -			            |DOUT			           |


| STM32 pin    	| HX711 Connection 1 	| HX711 Connection 2	|
| :---:        	|    :----:          	|        :---:	      |
| PB0          	| SCK             	   | SCK			         |
| PB8         	   | DOUT               	| -            	   |
| PB9		         | -			            |DOUT			         |

> **FOR STM32 ONLY: You need to connect one 1-kΩ resistor between the 5 VDC source voltage and PB0.**

The figure below shows a 1-kΩ resistor connected between 5VDC and the SCK pin on STM32. Heatshrink tubing was used to isolate/protect the electrical connection. 


![1-kΩ resistor connected between 5VDCand SCK pin on STM32. NOTE: Heatshrink tubing was used to protect the electrical connection.](https://user-images.githubusercontent.com/80347096/187000190-b5fb6b59-2a48-48c0-80ab-4b328ea017c8.jpg)


### DUAL Clock MCU wiring


| nano pin    	| HX711 Connection 1 	| HX711 Connection 2	|
| :---:        |    :----:          	|        :---:	         |
| 10          	| SCK             	   | -			            |
| 12         	| DOUT               	| -            		   |
| 11		      | -			            | SCK			            |
| 13		      | -			            | DOUT		            |


| STM32 pin    	| HX711 Connection 1 	| HX711 Connection 2 |
| :---:        	|    :----:          	|        :---:	      |
| PB0          	| SCK             	   | 			            |
| PB8         	   | DOUT               	| -            		|
| PB1		         | -			            | SCK			         |
| PB9		         | -			            | DOUT               |


> **FOR STM32 ONLY: You need to connect two 1-kΩ resistors. One resistor between the 5VDC source voltage and PB0, and the other resistor between the 5VDC source voltage and PB1.** 

Once the connections are made, it's time to *calibrate* the load cells.

## Calibration
### nano (branch and environment)
Files from the scales-calibration folder in the main directory need to be flashed to **both** the Nextion and MCU. **If using a single clock, then the first line of the scales-calibration.ino needs to be uncommented.** Be sure to select the correct platformio branch and environment as shown in figures below for nano

![nano_branch](https://user-images.githubusercontent.com/80347096/191635523-0eeb9ca2-173e-444a-875b-889a3a8b701c.jpg)

![Nano_environment](https://user-images.githubusercontent.com/80347096/191634757-c95249a7-6162-4212-a5c8-af67fd23aae0.jpg)

### STM32 (branch and environment)
Files from the scales-calibration folder in the main directory need to be flashed to **both** the Nextion and MCU. **If using a single clock, then the first line of the scales-calibration.ino needs to be uncommented.** Be sure to select the correct platformio branch and environment as shown in figures below for STM32

Select the appropriate branch for STM32 (the dev branch is used in this example)

![STM32_branch](https://user-images.githubusercontent.com/80347096/191636260-ac47f90a-7bb9-4cec-8d5b-530450e3e00e.jpg)

Select the appropriate environment for uploading to the STM32

![STM32_environment](https://user-images.githubusercontent.com/80347096/191636552-59431719-a869-4845-842c-88c099bd4f22.jpg)

### Software Interface with Known Mass

You will need an object with a known mass which you place **directly** on the load cell as shown in the figure below.


![Known 50-gram mass directly on load cell.](https://user-images.githubusercontent.com/80347096/187000236-65dbac3e-95af-462d-837d-177f7e411399.jpg)

If you flashed the system correctly, then you should see a screen similar to the figures below.

![Nextion calibration screen.](https://user-images.githubusercontent.com/80347096/188332313-c2a598b3-dd8c-4f4a-ac1a-b7c68ab9cd87.jpg)

![Nextion calibration screen.](https://user-images.githubusercontent.com/80347096/187000647-ba72fabd-3803-4207-9397-135843081593.jpg)

You need to adjust the Scale factors by tapping on the + or - buttons. The goal is to match the value of the "Weight output in grams (g)''  to the mass of the object on the load cell. Once the value displayed matches the mass of the object, repeat the process for the other load cell. 

If you don't have an object of known mass, then you can use an external scale to measure an object's mass.

![Unknown object sits directly on load cell.](https://user-images.githubusercontent.com/80347096/187000709-1bad6198-fefb-4584-811a-b80d02fcb87d.jpg)

Adjust the Scale factors by tapping on the + or - buttons until the "Weight output in grams (g) matches the mass of the object. 

![Calibration factor adjusted to match object's mass.](https://user-images.githubusercontent.com/80347096/187000749-8fd5f694-5533-435a-a60a-71868a601efb.jpg)

### Saving Calibration Constants to nano
- Press the SAVE button to store the values of the Scale factors into eeprom. 
   - It is recommended that you write these values down as a safeguard. 

- Reflash both the Nextion and the nano MCU with the appropriate gaggiuino code.
   - **Single Clock users need to uncomment the first line of the gaggiuino.ino file.** 

- Make sure your scales hardware is connected, and place the drip tray on the assembly. 

- Power on the Gaggia and pull some amazing shots.

### Saving Calibration Constants to STM32 
- Write the values down on a piece of paper. 
   - You will update the coefficients from the Settings page on the gaggiuino display. 

- Reflash both the Nextion and the STM32 MCU with the appropriate gaggiuino code. 
   - **Be sure to select the correct platformio environment from the environment tab. For this example, a single clock is used in a Gaggiuino that uses a relay to stop the pump.**

![STM32_appropriate_env](https://user-images.githubusercontent.com/80347096/191637488-68c23a6a-24ff-4d92-9b72-6a257c58e7e6.jpg)
   
  <!--  ![platformio_stm32_environments](https://user-images.githubusercontent.com/80347096/191513205-bbff4100-7173-49a7-a95e-4603614064e8.jpg) -->

- Power on the Gaggia.

- Tap on the Settings icon on the Gaggiuino Home screen.

- Tap on the Power button.

![Tap the Power button to get to the calibration factors.](https://user-images.githubusercontent.com/80347096/188330783-70f1b55a-35ba-48b8-9224-f11a22a90c8c.jpg)

- The figure below shows the screen you should see for updating the calibration coefficients for the load cells.

![Updating calibration coefficients via Settings page in NEXTION.](https://user-images.githubusercontent.com/80347096/188330921-40f59182-c4c4-40e6-9f57-783d6d1c3326.jpg)

- Update LC1 and LC2 factors based on the calibration you just performed.

- Press the Save button. 

- Enjoy the fruits of your labor by pulling a shot or two!

## Troubleshooting load cells
Issues can arise while installing scales. The white epoxy on the load cell is designed to protect the strain sensor and add strain relief for the small wires. Take caution while handling the load cell's wires. If there is no signal from an HX711 amplifier, there are a few things you can troubleshoot.

- *First and foremost*, check and double-check the connections from the load cell to the HX711 (typically soldered so check all solder joints) and the connections from the HX711 to the MCU (can be performed with a multimeter by checking for electrical continuity). 

- Make sure that you flashed the correct code with the correct clock settings (single clock nano users need to uncomment the first line of the gaggiuino.ino file and STM32 users need to be sure that the -DSINGLE_HX711_CLOCK switch is listed under build_flags in the platformio.ini file.)

- If you suspect a bad load cell, then you can check the resistance between the four wires (disconnected from the HX711). Below is a table showing the resistances between two different load cell wires. Thanks to Novarion for pointing out the resistance values as a check.

| Color 1    	| Color 2		| Resistance	(Ω)	|
| :---:        |    :----:   	|        :---:	      |
| red          | black			| 1000			      |
| red         	| white        | 750          		|
| red		      | green			| 750			         |
| black		   | white			| 750			         |
| black		   | green			| 750			         |
| white 	      | green			| 1000			      |


If the load cell values resemble those listed in the table and the electrical connections look or test ok, then the issue may be a bad HX711 amplifier.