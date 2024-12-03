---
layout: page
title: Self-coordinated Vehicle Formation
description: Robots use UWB technology for self-coordinating positioning.
img: assets/img/project/svf/svf.gif
importance: 2
category: work
giscus_comments: true
width: 250px
---

## Background
This project was developed `from October 2015 to March 2017`, advised by [Prof. Yuan Shen](http://oa.ee.tsinghua.edu.cn/~shenyuan/). 

In September 2015, inspired by [a TED Talk](https://www.ted.com/talks/vijay_kumar_the_future_of_flying_robots) and [this paper](https://www.science.org/doi/abs/10.1126/science.1254295), I became interested in swarm robotics.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/flying_robots.jpg" title="flying robots" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            <a href="https://www.ted.com/talks/vijay_kumar_the_future_of_flying_robots">TED Talk: The future of flying robots</a>
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/robot_swarm.jpg" title="robot swarm" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            <a href="https://seas.harvard.edu/news/2014/08/self-organizing-thousand-robot-swarm?utm_source=youtube&utm_medium=social&utm_campaign=harvard-youtube">Programmable self-assembly in a thousand-robot swarm</a>

        </div>
    </div>
</div>

The drone demo was pretty cool. However, it required OptiTrack for localization. In contrast, the self-assembly robot swarm did not require a base station for locating each node, though this limited the movement abilities of the inner nodes.

After reading [this paper](https://arxiv.org/pdf/1006.0890.pdf), I came up with an idea for a self-coordinated robot system. `If each robot node could know the distance between any 2 nodes, all nodes would have enough information to calculate the group's formation.` This scheme eliminates the need for a base station.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/broadcast1.jpg" title="Corporative Broadcast Ranging Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/broadcast2.jpg" title="Corporative Broadcast Ranging Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
        <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/broadcast3.jpg" title="Corporative Broadcast Ranging Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
        <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/broadcast4.jpg" title="Corporative Broadcast Ranging Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    <strong>Cooporative Broadcast Ranging Algorithm.</strong>
    <br/>
    After nodes A, B, C and D perform ranging using broadcast messages, all nodes receive sufficient information.
</div>

To implement this idea, we chose ultra-wideband (UWB) wireless technology. Using [Decawave DWM1000 transceiver modules](https://www.qorvo.com/products/p/DWM1000), we were able to measure distances between two modules with millimeter precision. However, as no existing API was available in late 2015, we had to develop the measurement algorithms and communication protocols ourselves.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/robot1.jpg" title="Our robot car at a glance" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/robot2.jpg" title="Our robot car at a glance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Our robot car at a glance.
</div>

From October 2015 to May 2016, I developed the first version of this project, `handling the entire workload—including the circuit, mechanism, embedded system, ranging algorithm, and broadcast protocol—all by myself`, except for the motor driver which was designed by [Zhe Weng](https://github.com/wengzhe).

From June 2016 to July 2016, [Feng Ge](https://ieeexplore.ieee.org/author/37086689078) assisted with the Decawave protocols for the second version. Additionally, I redesigned the motor driver to a brand new version:)

Subsequently, [Laixi Shi](https://laixishi.github.io/), [Wenhao Ding](https://wenhao.pub/), [Tuopu Wen](https://ieeexplore.ieee.org/author/37086546764), and [Junda Bi](https://junda.bi/) joined and contributed to the final version.

## Brief Introduction to the Project
We use ultra-wideband (UWB) wireless technology to measure the distance between any two robot cars, eliminating the need for a base station to localize any car. The cars self-coordinate to determine their positions.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/svf-intro.gif" title="svf demo" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            How it works.
        </div>
    </div>
</div>

## Demostrations of This Project
We broadcast the goal to every node, allowing them to determine their movements autonomously without remote control from central nodes or humans.
### Formation Change
The video below demostrates how the robot system transforms from a line into a rectangle shape.
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="assets/video/project/svf/formation_change.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>

The images below show the robot system changing in size.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/shrink.gif" title="Shrink the size" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            The robot system shrinks in size.
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/expand.gif" title="Expand the size" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            The robot system expands in size.
        </div>
    </div>
</div>

### Maintain Formation
The images below show the robot system maintaining its rectangular formation while rotating.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/rotate_ccw.gif" title="Maintain Formation, Then Rotate" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Maintain rectangle formation, then rotate counterclockwise.
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/rotate_cw.gif" title="Maintain Formation, Then Rotate" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Maintain rectangle formation, then rotate clockwise.
        </div>
    </div>
</div>

The images below show the robot system maintaining its rectangular formation while moving.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/forward.gif" title="Maintain Formation, Then Move" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Maintain rectangle formation, then move forward.
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/svf/backward.gif" title="Maintain Formation, Then Move" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Maintain rectangle formation, then move backward.
        </div>
    </div>
</div>