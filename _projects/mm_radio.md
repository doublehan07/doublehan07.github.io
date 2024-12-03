---
layout: page
title: McNugget Receiver
description: How I turned a McDonald's toy into a satellite receiver!
img: assets/img/project/McDonald_toy_receiver/McDonald-Walkie-Talkie.jpg
importance: 1
category: fun
giscus_comments: true
width: 250px
---

## Background

According to this [report](https://daoinsights.com/news/mcdonalds-releases-retro-walkie-talkie-for-childrens-day-while-kfc-hosts-nostalgic-toy-fair/): 

>Recently, McDonald’s kicked off a series of activities ahead of Children’s Day on 1 June, focusing on their classic McNuggets. The fast-food chain launched a special offer of 20 McNuggets for 20 RMB and a variety of limited edition ‘Walkie-Talkie’ toys. The ‘Walkie-Talkie’ is designed in the style of the classic McNuggets and fries. Users can also buy a ‘Walkie-Talkie’ and a graffiti sticker for an additional 38 RMB. On 22 May, the McDonald’s ‘Walkie-Talkie’ toy went on sale, causing the restaurant’s app to crash.

The McNuggets and fries toy walkie-talkies are really cute. They can transmit and receive FM signals at 409.9 MHz, which is a public, license-free walkie-talkie frequency.

I managed to get one on ``May 22, 2024``, immediately after McDonald's released the toy offer. **I rushed to the nearest store** and bought 20 McNuggets so I could be eligible to buy the toys.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/mm-walkie-talkie.jpg" title="McDonald's McNuggets- and fries-shaped toy walkie-talkies." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                McDonald's McNuggets and fries toy walkie-talkies.
            </div>
        </div>
    </div>
</div>

``As a ham and an engineer, I naturally disassembled them.``
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/mm-teardown.jpg" title="The teardown details of McDonald's toy walkie-talkies." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                The teardown details of McDonald's toy walkie-talkies.
            </div>
        </div>
    </div>
</div>

Then I discovered that **the RF IC inside the toy is a BK4802, which can be operated at 430-440MHz**. This range covers both local amateur radio FM repeaters, and several well-known satellite FM repeaters, including [ARISS](https://www.ariss.org/current-status-of-iss-stations.html), [the TEVEL series](https://www.amsat.org/tevel-mission-to-launch-on-spacex-transporter-3-mission-january-13th/), and [SO-50](https://www.amsat.org/two-way-satellites/so-50-satellite-information/).

So, an idea came to mind: ``what if I could modify the firmware of these toy walkie-talkies to make them capable of receiving signals from satellites?``

## Demo Showcase!
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/McDonald_toy_receiver/RS40S-SSTV-zip.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
        <div class="caption">
            🛰️ RS-40S (UmKA 1) SSTV signal received by McNugget Receiver. Try to <a href="https://www.google.com/search?q=sstv+decoder">decode</a> it!
        </div>
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/McDonald_toy_receiver/ISS-zip.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
        <div class="caption">
            🛰️ FM repeater at International Space Station received by McNugget Receiver.
        </div>
    </div>
</div>

## How I Made It

To start with, I disassembled the toy walkie-talkies.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/DisassembleMM.gif" title="I disassembled the toy walkie-talkies." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                I disassembled the toy walkie-talkies.
            </div>
        </div>
    </div>
</div>

Then, I used a multimeter to measure the connectivity of each pad on the circuit board. This helped me to eventually draw the circuit diagram of the toy walkie-talkie.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/DrawtheCircuit.gif" title="Draw the circuit diagram of the toy walkie-talkie using a multimeter." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                Draw the circuit diagram of the toy walkie-talkie using a multimeter.
            </div>
        </div>
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/mm-circuit-en-zip.jpg" title="The circuit diagram of the McDonald's toy walkie-talkie." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                The circuit diagram of the McDonald's toy walkie-talkie.
            </div>
        </div>
    </div>
</div>

After analyzing the circuit, I decided to remove the original MCU, and connect those I/Os to a new programmable MCU, where I could design and write new firmware to change the RX frequency.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/removemcu.gif" title="I decide to remove the original MCU." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                I decide to remove the original MCU.
            </div>
        </div>
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/connectio.gif" title="Then connect those I/Os to a new programmable MCU." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                Then connect those I/Os to a new programmable MCU.
            </div>
        </div>
    </div>
</div>

Next, I bypassed the original filter behind the antenna since its working frequency was not suitable for satellite frequencies. I also replaced the original antenna with a 50-ohm coaxial cable, allowing for the future connection of a more powerful antenna.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/BoardConnection.jpg" title="Board connections." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                Board Connections: The red wire bypasses the original filter.
            </div>
        </div>
    </div>
</div>

After modifying the circuit, it was time for the embedded part. So, I wrote the firmware for the STM32F042K6T6, a new MCU that handles all functions.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/coding1.gif" title="Me, writing the new firmware." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                Me, writing the new firmware in my studio.
            </div>
        </div>
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/McDonald_toy_receiver/coding2.gif" title="Developing the STM32F042K6T6 firmware using STM32CubeMX and Keil UV5." class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                Developing the STM32F042K6T6 firmware using STM32CubeMX and Keil UV5.
            </div>
        </div>
    </div>
</div>

After several rounds of testing and bug fixing, I finally made it work. Hooray! 🎉

[I've open-sourced the entire project](https://github.com/doublehan07/MM-Radio/), so you can make your own McNuggets Receiver as well. 

Please consider **adding a reaction below**, and **star the project on GitHub** if you like it!