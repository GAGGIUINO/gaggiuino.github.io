This is a guide on how to make the relay (controlling the 3-way valve) and dimmer (controlling the pump) independent on "Lego" (component) builds.
Independent control allows proper phase recognition, calibration, and tracking.

!> This is required for installs that followed schematics released before 5-May-2023 wanting to use software releases past **e8933a6** (8-Apr-2023) 

> [!Warning]
> Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. **Always work with the Gaggia unplugged.** You are performing this project under your own risk and the author of this guide and anyone associated with this project are NOT liable for your actions. 


## Notes

*   Pump and relay wire size recommendation is now ≤22 gauge because it is difficult to fit multiple 18 gauge wires into the screw terminals. 
*   Standard short-circuit protection calculations show that 22 gauge wire is permissible for known breakers 20 amps and under, however, this is smaller than standard. Your safety is your responsibility.

!> Powering your machine through a GFCI/AFCI/RCD device is recommended. 

# Guide
1. Disconnect pump source Line that is going to Dimmer L-IN. Tuck away the stock female spade (do not reconnect to the pump) and completely remove the wire that connected it to the Dimmer L-IN in the component housing. 

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077019-95c1681c-e3e7-40f4-bfc9-07b60f433896.JPG">

!> If you followed the Nano build pictures instead of the STM32 build schematic your pump is likely wired backward. You will need to rewire it to match the corresponding schematic above. Here is an example of a correctly wired Gaggia Classic pump:  
<img height="300" alt="image" src="https://github.com/Loogl3/gaggiuino.github.io/assets/117388662/55e88ca2-f640-4cb9-be90-0d9c46f77fb2">

2. Find the Line wire going from the coffee switch to the Relay and disconnect it (confirm, but if you followed the schematics exactly it should be connected to Relay COM). 

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077658-491bb7ed-818c-4cc8-9082-2a1d7aa85e5f.JPG">

3. Move the disconnected coffee switch Line wire to Dimmer L-IN (where you removed the pump wire). You may also want to swap this for a 22 gauge wire for ease of connecting jumpers in the next step.

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077865-1c85d17f-5c47-4681-a0f0-65bbabf2ec78.JPG">

4. Jumper from Dimmer L-IN to Relay COM, and from Relay COM to the snubber (if present). It is recommended to verify that your changes match the updated schematics. This completes the update.

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235078161-5d425621-2257-48f2-9349-6e662d68b826.JPG">

# Schematics

Save the images or right-click and open in a new tab to view at full resolution.

## New (Independent Relay and Dimmer)

<details>
<summary><b>Gaggia Classic</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gc-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gc-lv-ird.jpg">
</details>

<details>
<summary><b>Gaggia Classic Pro</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp-lv-ird.jpg">
</details>

<details>
<summary><b>Gaggia Classic Pro Eco</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp_eco-hv-ird.jpg">

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/gcp_eco-lv-ird.jpg">
</details>

<details>
<summary><b>STM32 Component Build</b> <i>(Click to expand)</i></summary>

<img height="300" alt="image" src="schematics/retrofit-indep-relay-dimmer/stm32-comp-build-ird.png">

</details>

## Old

**HV Diagrams**
* [STM32 Comp GC HV](https://user-images.githubusercontent.com/53577819/220784848-ab1fe9f1-92cc-40b4-a1c7-7200ab9a2b87.JPG)
* [STM32 Comp GCP HV](https://user-images.githubusercontent.com/53577819/220784874-583bb885-dce0-4fda-a920-4dc289607213.JPG)
* [STM32 Comp GCP_Eco HV](https://user-images.githubusercontent.com/53577819/220784834-fb1536e3-81cc-47e8-a243-21f6c3e49a7f.JPG)

**LV Diagrams**
* [STM32 Comp GC LV](https://user-images.githubusercontent.com/53577819/220784856-c1b5f073-5c0b-470e-b47e-c78eda7099ea.JPG)
* [STM32 Comp GCP LV](https://user-images.githubusercontent.com/53577819/220784877-279de614-afe9-4bcf-bf27-a6e25edb06bc.JPG)
* [STM32 Comp GCP_Eco LV](https://user-images.githubusercontent.com/53577819/220784865-b52ffb3f-8380-4225-a539-15d44738d2fe.JPG)

**STM32 Component Build**
* [STM32 Internal Comp Housing Schematic](https://user-images.githubusercontent.com/117388662/230696068-e49df2fa-c3b6-49c2-80ff-629b80780938.png)