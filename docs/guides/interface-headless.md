# Interface: Headless

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

<img height="300" alt="Headless E177v1.1" src="media/headless.png">

# Assembly

> [!Note|style:callout|label:Magnetic housing only|iconVisibility:visible]
> For the magnetic housing (no vent clips), install magnets on the back of the housing using cyanoacrylate or double-sided tape  
>
> <img width="300" alt="image" src="https://github.com/user-attachments/assets/da035af4-4fdf-4b69-9bea-01b531723385">

Connect the cable to the control system (PCB or Lego). 

<details><summary><b>Schematics for reference</b> <i>(click to expand)</i></summary>

The headless PCB uses the same connection as the screens, JST-PH.

<!-- tabs:start -->
<!-- tab:PCBv3.1/v4 -->
  <!-- tabs:start -->
  <!-- tab:GCP -->
  <img height="500" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_1_LV.png">
  <!-- tab:GC -->
  <img height="500" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_1_LV.png">
  <!-- tabs:end -->
<!-- tab:PCBv3 -->
  <!-- tabs:start -->
  <!-- tab:GCP -->
  <img height="500" alt="image" src="schematics/stm32-lv/GCP_wiring_PCBv3_LV.png">
  <!-- tab:GC -->
  <img height="500" alt="image" src="schematics/stm32-lv/GC_wiring_PCBv3_LV.png">
  <!-- tabs:end -->
<!-- tab: Lego -->
  <img height="500" alt="image" src="schematics/stm32-comp-build.png">
<!-- tabs:end -->

</details> 

Route the power/serial cable to the mounting location (the left vent is recommended for all Gaggia Classic models).

Plug the power/serial cable into the headless PCB, *then* slide the PCB into the housing. Make sure it is fully seated before closing the case.

  > [!Tip|style:callout|label:Poka-Yoke|iconVisibility:visible]
  > The housing has been intentionally designed so the cover cannot close if the PCB isn't in place.  
  > <img height="200" alt="image" src="https://github.com/user-attachments/assets/5170f195-5679-455e-b4b4-b5720fe875c0">

>
Attach the housing to the machine  
  <img height="300" alt="image" src="https://github.com/user-attachments/assets/54b5debf-994f-40e8-8ae9-ceb904187f19">