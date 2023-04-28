This is a guide on how to make the relay (controlling the 3-way valve) and dimmer (controlling the pump) independent on "Lego" (component) builds. 
Independent control allows proper phase recognition, calibration, and tracking.

> [!Warning]
> Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. **Always work with the Gaggia unplugged.** You are performing this project under your own risk and the author of this guide and anyone associated with this project are NOT liable for your actions. 

# Notes
*   Pump and relay wire size recommendation is now ≤22 gauge because it is difficult to fit multiple 18 gauge wires into the screw terminals. 
*   Standard short-circuit protection calculations show that 22 gauge wire is permissible for known breakers 20 amps and under, however, this is smaller than standard. Your safety is your responsibility.

!> Powering your machine through a GFCI/AFCI/RCD device is recommended. 

# Guide
1. Disconnect pump source Line that is going to Dimmer L-IN. Tuck away the stock female spade (do not reconnect to the pump) and completely remove the wire that connected it to the Dimmer L-IN in the component housing. 

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077019-95c1681c-e3e7-40f4-bfc9-07b60f433896.JPG">

2. Find the Line wire going from the coffee switch to the Relay and disconnect it (confirm, but if you followed the schematics exactly it should be connected to Relay COM). 

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077658-491bb7ed-818c-4cc8-9082-2a1d7aa85e5f.JPG">

3. Move the disconnected coffee switch Line wire to Dimmer L-IN (where you removed the pump wire). You may also want to swap this for a 22 gauge wire for ease of connecting jumpers in the next step.

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235077865-1c85d17f-5c47-4681-a0f0-65bbabf2ec78.JPG">

4. Jumper from Dimmer L-IN to Relay COM, and from Relay COM to the snubber (if present). It is recommended to verify that your changes match the updated schematics. This completes the update.

    <img width="800" alt="image" src="https://user-images.githubusercontent.com/117388662/235078161-5d425621-2257-48f2-9349-6e662d68b826.JPG">

# Schematics

[comment]: # (really wanted to make this a table but it just didn't agree with me)

## Old

**HV Diagrams**
* [STM32 Comp GC HV](https://user-images.githubusercontent.com/53577819/220784848-ab1fe9f1-92cc-40b4-a1c7-7200ab9a2b87.JPG)
* [STM32 Comp GCP HV](https://user-images.githubusercontent.com/53577819/220784874-583bb885-dce0-4fda-a920-4dc289607213.JPG)
* [STM32 Comp GCP_Eco HV](https://user-images.githubusercontent.com/53577819/220784834-fb1536e3-81cc-47e8-a243-21f6c3e49a7f.JPG)

**LV Diagrams**
* [STM32 Comp GC LV](https://user-images.githubusercontent.com/53577819/220784856-c1b5f073-5c0b-470e-b47e-c78eda7099ea.JPG)
* [STM32 Comp GCP LV](https://user-images.githubusercontent.com/53577819/220784877-279de614-afe9-4bcf-bf27-a6e25edb06bc.JPG)
* [STM32 Comp GCP_Eco LV](https://user-images.githubusercontent.com/53577819/220784865-b52ffb3f-8380-4225-a539-15d44738d2fe.JPG)

**Internal Component Housing**
* [STM32 Internal Comp Housing Schematic](https://user-images.githubusercontent.com/117388662/230696068-e49df2fa-c3b6-49c2-80ff-629b80780938.png)

## New (Independent Relay and Dimmer)

**HV Diagrams**
* [STM32 Comp GC HV - IRD](https://user-images.githubusercontent.com/117388662/235083196-739bb6db-7213-4cac-8293-75cbcc81b5ef.JPG)
* [STM32 Comp GCP HV - IRD](https://user-images.githubusercontent.com/117388662/235083465-80c8cb69-6442-453d-ac2a-821b7da190be.JPG)
* [STM32 Comp GCP_Eco HV - IRD](https://user-images.githubusercontent.com/117388662/235083687-5615555c-7295-4172-87b0-cbe3a2414cf9.JPG)

**LV Diagrams**
* [STM32 Comp GC LV - IRD](https://user-images.githubusercontent.com/117388662/235083350-c73974d9-bef9-4eee-9b8b-436c999ba291.JPG)
* [STM32 Comp GCP LV - IRD](https://user-images.githubusercontent.com/117388662/235083525-713be71f-dfb9-4c73-9d89-b93d0a19b8ed.JPG)
* [STM32 Comp GCP_Eco LV - IRD](https://user-images.githubusercontent.com/117388662/235083749-03cd7b0b-acbb-43b4-9705-1a42073605d4.JPG)

**Internal Component Housing**
* [STM32 Internal Comp Housing Schematic - IRD](https://user-images.githubusercontent.com/117388662/235083835-fa2b6721-598c-4fca-9ac7-eb23a2aa596b.png)