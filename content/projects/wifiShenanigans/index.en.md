+++
title = "Raspberry Pi Zero 2W wifi radioscope 1#"
description = "the unforeseen consequences when you give me a directional antenna.."
type = "posts"
tags = [
    "Interests",
    "Linux",
    "Shenanigans",
]
toc = true
date = "2026-03-12T10:00:00+02:00"
categories = [ "Technial" ]
series = []
[ author ]
  name = "Volchar"
+++
I was fascinated by this [video](https://www.youtube.com/watch?v=aeah3fFYlnA) from "The Thought Emporium," where they built a working 2.4GHz radio telescope that they used to scan their surroundings and create a map (graph) of signal strength versus location. So I thought, why not give it a try? 

### Why?
**Why not?**

I bought a MIMO square outdoor antenna measuring 25 cm², a slightly dodgy WiFi USB adapter with two detachable antennas, 2x RP SMA cables, and finally 2x RP SMA->TNC adapters. The whole thing cost me just under **`1,700 CZK [~70€]`**. The specific parts don’t matter, which is why I don’t include links here, unlike in the blog post about the [charger](../lifepo4Charger/index.en.md). The core of the entire project is a **directional antenna**.

### Directional Antenna
There are many antennas that would be suitable for this small project. Realistically, I had two types to choose from:

  - `Sector antenna` = _Sort of like a "streetlight"_
  
    - This type is suitable for covering a wider area.

  - `Directional antenna` = _Sort of like a "football stadium floodlight"_

    - This type is suitable for a specific connection between two points. Typical for connecting two buildings.

And then there are the designs and all sorts of variables.

A _directional antenna_ was suitable for this project because I actually need a narrow beam, but not so narrow that I have to measure the azimuths like a mortar. You could say I was looking for a _directional sector antenna_, and surprisingly, I found one.

#### The chosen one

This particular model, from some unnamed Polish manufacturer, has two TNC connectors as it supports *both 2.4 GHz polarizations*.
According to information I found online, the vast majority of standard Wi-Fi devices use **horizontal** polarization. My antenna is marked as such. Fortunately, I don’t have to worry about it, since it has a second TNC connector for **vertical** polarization. Realistically, I could just plug in one connector and make sure I’m holding it correctly, but I don’t like to arbitrarily give up options when navigating uncharted waters. Other flat antennas were the same price, if not more expensive.

### WiFi Adapter
I didn’t expect finding a USB WiFi adapter with two detachable antennas to be such a hassle.

The criteria were clear: two detachable antennas. That’s all.

The main reason I didn’t cobble together a random dual-antenna WiFi USB dongle is that my soldering skills aren’t perfect, and with radio gear, it’s better if it’s done just right, otherwise you’re in for noise and low gain.