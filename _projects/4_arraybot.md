---
layout: page
title: The Hardware Design of ArrayBot
description: A tutorial on building the ArrayBot.
img: assets/img/publication_preview/arraybot.gif
importance: 1
category: work
giscus_comments: true
width: 250px
---

[ArrayBot](https://steven-xzr.github.io/ArrayBot/) is a 16×16 array of vertically actuated pillars, each equipped with tactile sensors, published at [ICRA 2024](https://ieeexplore.ieee.org/abstract/document/10610350). 

For a visual demonstration of ArrayBot's capabilities, you can view the following video:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/ArrayBot/ArrayBot.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
        <div class="caption">
            ArrayBot: Reinforcement Learning for Generalizable Distributed Manipulation through Touch
        </div>
    </div>
</div>

``I designed all the hardware for ArrayBot myself.`` While I’m happy to share the details, its complex structure makes it pretty **tough to build**. As you can see in the picture below, even with a bunch of people helping, it still took me more than 24 hours straight to put it all together.

<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
            {% include figure.html path="assets/img/project/ArrayBot/assemble.gif" title="Me assembling the ArrayBot" class="img-fluid rounded z-depth-1" %}
            <div class="caption">
                Me assembling the ArrayBot—no sleep for 2 days 😅
            </div>
    </div>
</div>

## Detailed Hardware Demo

I built a UI to visualize the pillar height and tactile information. The video below shows me testing a smaller version of ArrayBot, the 4x4 model.

In the first video, you can see that when I tap on the ArrayBot’s surface, the pressure grid in the UI changes from dark to light. Dark represents higher pressure, while light means lower pressure. Since the FSR tactile sensor isn’t super precise, we ended up binarizing its data for the RL policy.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/ArrayBot/arraybot-tactile-demo.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
        <div class="caption">
            Tapping the ArrayBot tabletop and observing the pressure grid.
        </div>
    </div>
</div>

In the second video, I send a command to lift all the pillars. The height grid in the UI also shifts from dark to light — dark shows lower heights, and light shows higher heights.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/ArrayBot/arraybot-combo-demo.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=false %}
        <div class="caption">
            Sending a lift command and watching the height grid update.
        </div>
    </div>
</div>

## Key Highlights of the Hardware design

In this post, I’ll cover some key points about the hardware design. **If you need more help, just let me know!** You can leave a comment below or email me directly—I’m always happy to help you build your own ArrayBot.

### The Atom Unit of ArrayBot
The hardware of ArrayBot can be perceived as a 16 × 16 array of vertically sliding atom units.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/ArrayBot/atom_unit.png" title="The Atom Unit of ArrayBot" class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                The exploded view of an atom unit.
            </div>
        </div>
    </div>
</div>

Each atom unit is composed of the following components:

| Component                          | Description                                                                  | Link                                               |
|------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------|
| DC Motor                           | Provides motion for the unit.                                                | [Chihai Motor, 050, DC 12V, 800 rpm (Reduction ratio 20:1)](https://www.aliexpress.us/item/2255800795255295.html) |
| Encoder Board                      | Tracks the motor's position and movement.                                    | Custom design |
| Sliding Rail                       | Ensures smooth motion while maintaining undisturbed FSR signal transmission. | Custom design |
| Coupling                           | Connects the motor to the lead screw.                                        | [Parallel Line Coupling D12L18.5, 3mm to 5mm](https://www.aliexpress.us/item/3256807134297874.html) |
| Lead Screw with Screw Nut          | Converts rotational motion into linear motion.                               | [T5*4 Lead Screw, Pitch 1mm, Length 100mm](https://www.aliexpress.us/item/3256807407600395.html) ``with Square Screw Nut`` |
| Pillar                             | Provides linear motion (dimensions: 16mm × 16mm × 200mm).                    | Custom design |
| Force Sensing Resistor (FSR)       | A Low-cost tactile sensor for pressure detection.                            | [RXD1016, Male terminal, Range 200g](https://www.aliexpress.us/item/3256805480273214.html) |
| Silicone Hemispherical End-Effector | Protects the tactile sensor and enhances friction at the end-effector.      | Custom design |

In the original design, I used CNC techniques to manufacture the pillar and the mold for the silicone hemisphere. However, I believe it’s feasible to 3D print both the pillar and the mold directly, which could significantly reduce costs.

### The Modular Unit of ArrayBot

Every two atom units are assembled with one STM32 board as a modular unit.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/ArrayBot/modular_unit.png" title="The Modular Unit of ArrayBot" class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                The modular unit of ArrayBot.
            </div>
        </div>
    </div>
</div>

| Component       | Description                                     | Link                                                |
|-----------------|-------------------------------------------------|-----------------------------------------------------|
| Atom Unit       | Represents a single element of the 16×16 array. | [Atom Unit of ArrayBot](#the-atom-unit-of-arraybot) |
| Control Board   | An STM32 board serving as the main controller.  | [Custom design](#control-board)                    |

Since the ArrayBot uses a 16x16 array, and every two atom units form a modular unit, it’s easy to figure out we need 128 modular units in total. Simple math, but a *huge* number🤯.

```Getting over 100 custom circuit boards to work together wasn’t easy.``` There were plenty of hardware failures—soldering errors, broken components, random short circuits—you name it💥. To make sure I had 100 functional boards, I actually had to manufacture over 150. And let me tell you, soldering 150+ boards was an absolute nightmare😵‍💫. Easily one of the toughest parts of the whole project!

### Control Board

The control board manages everything. 

It reads data from the FSR sensors using an Analog-to-Digital Converter (ADC) via Direct Memory Access (DMA). It counts the rising and falling edges of the encoder's A/B phase rectangular orthogonal pulses, generates PWM signals and basic I/O control signals for the motor driver, and supports the CAN transceiver for communication with the PC.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/ArrayBot/control_board_functions.png" title="The Functions of the Control Board" class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                The control board handles sensors, motors, encoders, and PC communication.
            </div>
        </div>
    </div>
</div>

The actual circuit board is as small as a coin, as shown in the picture below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <div class="image-container" style="display: inline-block; position: relative;">
            {% include figure.html path="assets/img/project/ArrayBot/control_board.jpg" title="Control Board" class="img-fluid rounded z-depth-1" %}
            <div class="caption" style="text-align: center; width: 100%; margin-top: 5px;">
                A coin-sized circuit board.
            </div>
        </div>
    </div>
</div>

I’ve included the schematic design for this control board. 

If you’d like to manufacture the same board, you can simply send the <a href="/assets/files/project/ArrayBot/Gerber_control_driver_board_V6_0.zip">Gerber file</a> and <a href="/assets/files/project/ArrayBot/PickAndPlace_control_driver_board_V6_0.xlsx">pick-and-place file</a> to JLCPCB or PCBWay.

<iframe src="/assets/files/project/ArrayBot/SCH_control_driver_board_V6_0.pdf" width="100%" height="600px"></iframe>
