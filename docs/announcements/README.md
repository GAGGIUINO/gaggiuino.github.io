# Announcements

<!-- panels:start -->
<!-- panels:title -->
## Milestones
<!-- div:panels -->
* __September 2024 - Gaggiuino Generation 3 (NextMonday&trade;), based on an STM32 + ESP32-S3 UI architecture, is now open for public use.__  
    * Main features and basic installation documentation are complete. Additional features and comprehensive documentation are in process.  
    * The BlackPill / SMT32F411CEU6 is a Cortex&reg;-M4 that is nearing its limits. Significant effort was put into optimization and testing a stable overclock so Gen 3 software will work on current builds.
    * For new builds, PCBv4 will be available with a Cortex&reg;-M33 STM32U585CIU6. This "performance" option improves stability, cycle time, and capability with "unlimited" phases. It also has more headroom for future development. 
* __July 2023 - Nextion UI development has reached EOL, STM32 BlackPill + Nextion is the recommended install while a new UI solution is being developed.__ 
* __June 2022 - Arduino NANO based development has reached EOL, no new features will be added to it's branch going forward.__ 
<!-- panels:end -->

## Development Lifecycle
>
Gen| Microcontroller (MCU)                  | Screen/UI| Compatible Builds                                                     | Release Date       |Dev Stop | Current Support  | 
:-:|----------------------------------------|----------|-----------------------------------------------------------------------|--------------------|---------|:----------------:|
1  |ATmega328<br/> (Arduino Nano)           |Nextion   |**Component (Lego)**<br/>PCBv1<br/>(MainBoard + SubBoard)              | 2021               |June 2022|:x:               |
2  |STM32F411CEU6                           |Nextion   |Component (Lego)<br/>PCBv2 / PCBv2.1 :warning:<br/>PCBv3 / **PCBv3.1**           | June 2022          |July 2023|:heavy_check_mark:| 
3  |STM32F411CEU6 (OC)<br/>**STM32U585CIU6**|ESP32-S3<br/>(Embedded & Web)|Component (Lego)<br/>PCBv2 / PCBv2.1 :warning:<br/>PCBv3 / PCBv3.1<br/>**PCBv4**|September 2024|         |:heavy_check_mark:|     

>
* :warning: - *PCBv2 / PCBv2.1 are compatible but support is minimal.*
* **Bold** Item - *Recommended*
* Dev Stop - *Development for this combination of hardware has ceased.*
* Current Support - *Installation support available in the discord.*

>[!WARNING|style:callout|label:Considerations and caveats] Current plans for development are always in flux.  While the current plan may be to provide new features to the recommended install route, it is always possible that those plans will change, and new hardware will be required to upgrade.  The above recommendations are given with this in mind and we will try our best to keep you informed of any changes.

