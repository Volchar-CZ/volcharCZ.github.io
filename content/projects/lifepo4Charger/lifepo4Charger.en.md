---
title: "LiFePO4 DIY Charger"
date: 2025-08-25T11:00:00+02:00
draft: true
toc: false
images:
tags:
  - 3D printing
  - Soldering
---
One of my first projects that features soldering and actual product design! At least for me.

Why LiFePO4? Why not simple LiPo? Because if I f-ed it up, there wouldn't be any unexpected fireworks.

## A solution for a future problem
I would like to make a LiFePO4 battery bank, through which I could power not only my phone and USB-C PD laptops, but also custom tools, non-USB-C PD laptops and power tools. Understandably this is a big project, so I'm now making "supportive" elements which will help me. Again, as I stated above, I won't be using LiPo as this is DIY project and therefore I'm big decisive element if it will be fun project for me or the fire department.

In order to shine little bit of a light on this battery bank:
 - Normal USB-A & USB-C w/PD [100W] ports
 - Variable output (for laptops, tools, custom tools)

Because I want to future proof, this powerbank will be versatile. the reason for 100W for the USB-C is because of a portable soldering Iron which I would like to have with me. The variable output, again repeating myself, for laptop who can be charged via the barrel jack only and for charging powertools or even run them off of it.

# Components
Everything was bought on laskakit.cz, a czech DIY website. This is not sponsored by them.
 - [Battery holder](https://www.laskakit.cz/bateriovy-box-1x18650-do-dps/)
    - I could've 3D printed it, but it's 20,- czk
 - [USB-C PD board module](https://www.laskakit.cz/laskakit-usb-c-pd-ch224k-prepinac-napajeciho-napeti/)
    - Really cool looking board and cheap. You can set it's input voltage!
 - [LiFePO4/LiPo battery charger (TP5000)](https://www.laskakit.cz/nabijecka-li-ion-clanku-tp5000--2a-lifepo4-lithium/)
    - The only LiFePO4 battery charger they had. No other reason tbh.
## Soldering 1/
I've soldered a screw terminal onto the USB-C PD board. The idea is if I ever wanted to gut it out, so it would be easier.

Also I've soldered the provided LED onto the charger, as it indicates what's going on. IMHO, they could've make the traces little bit more descriptive, as I had to read the PDF documentation of the TP5000 and looking up the traces in order to solder the LED right. I don't mean soldering Input onto GND, I mean soldering the right color for the right status.

Apart from that I've soldered some thicker wires onto the bat. holder. Excess wires from when I was installing under-cabinet LED strip. 
## Design
Like with the Raspberry Pi Zero 2W modular case, I just made the design by placing the components on top of them with a little pinch of imagination.

The general idea was to place the USB-C PD board with the charger on top of each other. Pretty much having the charger at the same level as the top of the screw terminal.

Now it was drawing time. I just placed the components on a paper, traced them and started designing the encloser.