# Interface: Screen

> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

# Assembly

<!-- tabs:start -->
<!-- tab:Gen 3 -->

Overview of mount variants: 

<img width="500" alt="image" src="https://github.com/user-attachments/assets/888b31f2-d0e5-48d8-af31-7133bd122f70">

> [!TIP|style:callout]
> If not already done, connect the wiring to the control system first as was done during the [pre-install test](guides-stm32/pcb-guide.md#pre-install-test) - the 2 small screen connectors can typically slip through the recommended housing gaps but the other side often cannot. 

<details><summary><b>Schematics for reference</b> <i>(click to expand)</i></summary>

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

  <!-- tabs:start -->
  <!-- tab:Front Mount -->
  
  Place a magnetic surface under the mount and glue the magnets into the front mount, 2 per pocket.  
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/ead5c319-6b55-48c7-8b6b-0f29e8354e0f">  

  Route the wires through the housing gap as shown.

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/588d2c45-c75d-4f03-a2a2-f3a7fb753912">

  Insert the cable through the front mount, then the screen housing back, and then plug in per schematic (black wires shown as wire coloring has varied in the past).  
  Arrange the wires so they are not over any large components. Kapton tape may be used to hold the wires in place if desired.  

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/028e9195-825e-48e4-b37b-14276b37e91b">
  <!-- tab:Funnel Mount -->

  Use a screwdriver in the backside pry slot of the funnel cover assembly to gently separate the sliding lid.   

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/9c2613aa-ff02-441f-bdfa-e8db1686fb72">

  Use a soldering iron to install the heat-set insert (if not pre-installed), and then press the latch into the cover plate by hand. The latch is what locks screen rotation - press it to rotate the screen out of the way for water tank fill.    

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/6b5498d2-14ce-473d-86b5-116dd9999caa">

  Route the wires through the vent as shown. The wires may be centered if desired, but shifting them over gives more clearance to the AC wiring. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/8c1e694a-89a4-4cce-9641-f92db90aab87">

  Insert the cable through the screen housing back and then plug in per schematic (black wires shown as wire coloring has varied in the past).  
  Arrange the wires so they are not over any large components. Kapton tape may be used to hold the wires in place if desired.  

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/99454a58-6f10-4422-9010-ad2a61bfa8cc">
  <!-- tab:Rear Mount -->
  Route the wires through the vent as shown. The wires must be in this position (and the proper side of the rear mount) to center the screen.

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/1ecfdfb7-cd2e-49c0-895f-76fc201f7e7c"> 

  Insert the cable through the rear mount, then the screen housing back, and then plug in per schematic (black wires shown as wire coloring has varied in the past).  
  Arrange the wires so they are not over any large components. Kapton tape may be used to hold the wires in place if desired.  

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/8724315e-99c0-4e59-8242-e98b0531ee6c">
  <!-- tabs:end -->

Place the screen onto the upper posts first as they have a retention feature. Ensure the wires settle below the surface of the housing and screen PCB, and are not pinched under the connectors. 

<img width="500" alt="image" src="https://github.com/user-attachments/assets/2d059c58-a688-409c-9bd9-183443854bc7">

Place the front cover on, starting with the top side (with the thinner bezel). Verify no wires are in the way, then snap the lower side on. If you need to remove the housing cover, use the fingernail slots. 

<img width="500" alt="image" src="https://github.com/user-attachments/assets/fc37622f-ee69-4ec3-af85-874e8c00d273">

  

  <!-- tabs:start -->
  <!-- tab:Front Mount -->

  Align the mount with the interface. Gently press the clip down to align the features, then push the mount forward until the retaining clip can relax back into place. Make sure the wires are centered without too much excess slack so they don't get pinched while doing this. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/343d150b-3509-481a-80a5-b4e811b0ea3c">

  Attach the assembly to the front of your machine, clean up the cable routing as shown and feed the excess back into the machine. Tape the cable in place with Kapton (or other high-temp) tape. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/2a1c65f7-1ec7-46a0-bfa5-59710317190d">

  Put the machine funnel and cup warming plate back on after everything is arranged as desired (don't forget to connect the ground wire).

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/44cd4587-2e95-4c72-bc0c-595ed9d91755">

  <!-- tab:Funnel Mount -->

  Tape wires into place. Align the adjustable plate with the interface. Gently press the clip down to align the features, then push the plate forward until the retaining clip can relax back into place. Make sure the wires are in the gap, then remove the tape. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/d9653f52-dd7f-4593-b4bb-dfeb9fba9cd2">

  Attach the swivel to the adjustable plate with the screws, washers, lock washers, and lock nuts. Pay attention to the washer order so the lock washers can't cut into the print. The lock washers are used as springs - tighten the screws and nuts until the mount angle can be adjusted by hand and stays in place when released.    

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/9bc40925-76a9-4868-bed5-2a554826f1b7">

  > [!TIP|style:callout]
  > If the vertical screw loosens over time, a **tiny drop** of plastic-safe threadlocker or cyanoacrylate may be used on the heat-set insert threads to hold it in place. 

  Zip-tie the wires into place (optional).

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/bc3a08cb-6f48-489a-9d2c-367b53e5f1c9">

  Put the machine funnel and cup warming plate back on after everything is arranged as desired (don't forget to connect the ground wire). Place the funnel mount onto the funnel.

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/8f151c1e-93fa-4e46-81d0-cb45a3dc9d63">
  
  <!-- tab:Rear Mount -->

  Tape wires into place. Align the adjustable plate with the interface. Gently press the clip down to align the features, then push the plate forward until the retaining clip can relax back into place. Make sure the wires are in the gap, then remove the tape. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/d9653f52-dd7f-4593-b4bb-dfeb9fba9cd2">

  Attach the rear mount to the adjustable plate with the screws, washers, lock washers, and lock nuts. Pay attention to the washer order so the lock washers can't cut into the print. The lock washers are used as springs - tighten the screws and nuts until the mount angle can be adjusted by hand and stays in place when released.   

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/69b796ea-27e1-4fb2-a55e-b474187ac989">

  Put the machine funnel and cup warming plate back on after everything is arranged as desired (don't forget to connect the ground wire). While it's possible to install with the rear mount in place, it's much easier without.  
  Insert the upper mounting features into place in the vent, then clip the bottom side in. Push on the back of the latch handles to make sure they're fully attached. 

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/d8067907-8ccb-4b46-b1b2-455515eea056">

  >

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/e498133e-9f96-4136-bac3-5a3531091e48">
  
  <!-- tabs:end -->
<!-- tab:Gen 2 -->

There should be extra wire length so the screen can remain connected while the cover is removed. Snake the screen wires through the housing components and replace the pins in the connector. Make sure the wire order matches what you successfully tested in the bench test. I also like to put the nuts in the screen housing cover, use screws to draw them tight, and put a drop of super-glue on the nuts (**not the screws**) to hold them to the housing. When it's dry remove the screws.

![Screen wiring](https://user-images.githubusercontent.com/117388662/239463397-25c3e82c-07e3-4b10-b056-59cbf8d36efc.png ':size=500')

Put the screen housing together, push the spare screen wire (and heat shrink tubing) back through the vent hole and you're ready for espresso! 

![Finished!](https://user-images.githubusercontent.com/117388662/239463949-0e90b52f-a5fa-4aed-8ea7-9047154cc213.png ':size=500')

<!-- tabs:end -->
