* **Q: What is the current recommendation for the method of installation?**

  **A:** The "LEGO" method for STM32 Blackpill is recommended for most users.

* **Q: Why Arduino and STM32 and not some other processor like ESP32?**

  **A:** STM32 and Arduino were selected because of platform familiarity and safety concerns. Different microcontrollers have different purposes and strengths. Espresso machines are potential pressure bombs, electrocusion hazzards, and (unlikely) sopurces of causing a fire or leaking water. Based on how the STM32 vs ESP32 are designed there are faster floating-point calculations, better safety controls, and fewer unnecessary performance variables.

* **Q: How do I contribute to the Gaggiuino code?**

  **A:** The project repository is in the [Zer0-bit/gaggiuino] repo. Pull requests are welcome.

* **Q: How do I contribute to this documentation?**

  **A:** The documentation is hosted in the [GAGGIUINO/gaggiuino.github.io] repo. Pull requests are welcome. Please see the [Gaggiuino Documentation README] for more information.

* **Q: Is a mobile app/interface planned?**

  **A:** One of the goals of this project is for the modified espresso machine to be fully self-sufficient, that is, not dependent on any external mobile App or website. That said, adding a web or mobile interface to Gaggiuino is a feature that would be welcome, provided it does not prevent local control of the machine.

* **Q: How much does a PCB cost?**

  **A:** This depends greatly on how the PCB is sourced. Assembled PCBs will occasionally pop up for sale in the [marketplace channel], and it's up to the seller to set the price, though boards are usually around \$60 USD and shipped out within days. If ordering through PCBWay, 10 boards can be purchased for about \$350 USD, including the PCB itself, the BOM, assembly, and shipping. Boards ordered this way will have a lead time of about 3-5 weeks. If purchased through a group buy, the price will be even less, but the delivery time will be longer, as you'll need to wait for a group buy to happen.

* **Q: How do I order a V3 PCB using PCBWay?**

  **A:** This is for advanced users, and only recommended for people who have ordered PCBs in the past, but the easiest way to order a board is using the "Add to cart" button in the [GaggiaBoard_V3] shared project through [PCBWay]. The defaults are fine, but it's recommended to choose a lead-free process such as "HASL lead free" or "ENIG", and make sure that the PCB quanity you choose matches the assembly quantity.

[Zer0-bit/gaggiuino]: https://github.com/Zer0-bit/gaggiuino
[GAGGIUINO/gaggiuino.github.io]: https://github.com/GAGGIUINO/gaggiuino.github.io
[Gaggiuino Documentation README]: https://github.com/GAGGIUINO/gaggiuino.github.io/blob/main/README.md
[marketplace channel]: https://discord.com/channels/890339612441063494/1064338101536817223
[GaggiaBoard_V3]: https://www.pcbway.com/project/shareproject/GaggiaBoard_V3_6c90dfac.html
[PCBWay]: https://www.pcbway.com/