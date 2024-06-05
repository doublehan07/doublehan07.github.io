---
layout: page
title: Ham Radio
description: DE BI1NWO 73 <br> Satellite, FM, SSB, CW, FT8......
img: assets/img/project/ham_radio/ham_radio.jpg
importance: 2
category: fun
giscus_comments: true
width: 250px
---

> Amateur radio, also known as ham radio, is the use of the radio frequency spectrum for purposes of non-commercial exchange of messages, wireless experimentation, self-training, private recreation, radiosport, contesting, and emergency communications.

I immediately fell in love with ham radios `when I was 13 years old`, after learning a tutorial on how to make a [crystal radio receiver](https://en.wikipedia.org/wiki/Crystal_radio) from my physics textbook. I started with designing antenna at [MF bands](https://en.wikipedia.org/wiki/Medium_frequency), then followed by designing rectifiers and amplifiers. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/crystal_radio.jpg" title="crystal radio circuit" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            My first crystal radio receiver circuit, designed at age 13.
        </div>
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/coil.jpg" title="DIY" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Handmade inductor crafted with enamel-insulated wire, set to around 300µH for the MF band.
        </div>
    </div>
        <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/reed_speaker.jpg" title="crystal radio circuit" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Upgrade the reed speaker by using a tiny enamel-insulated wire to increase the DC impedance
        </div>
    </div>
</div>

I received my license and callsign in 2022. I'm also a member and operator of [BY1QH](https://www.qrz.com/db/By1qh), which stands for the Tsinghua University Amateur Radio Club.

## My Rigs
Currently, I have several transceivers for different bands.

My main device for [VHF](https://en.wikipedia.org/wiki/Very_high_frequency) and [UHF](https://en.wikipedia.org/wiki/Ultra_high_frequency) bands is the Yaesu FT-5DR.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/5dr.jpg" title="My Rigs" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Yaesu FT-5DR for VHF/UHF bands, with a Diamond SRH770 or SRH771 antenna.
        </div>
    </div>
</div>

For satellite contacts, I prefer to use a handheld [Yagi antenna](https://en.wikipedia.org/wiki/Yagi%E2%80%93Uda_antenna).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/so-50.jpg" title="My Rigs" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            My friend and I are using the Yaesu FT-5DR and a U7V4 Yagi antenna, trying to make QSOs on <a href="https://amsat-uk.org/2012/01/30/working-the-fm-sat-so-50/">the FM repeater from the satellite SO-50</a>.
        </div>
    </div>
</div>

I enjoy [QRP portable operations](https://en.wikipedia.org/wiki/QRP_operation)! Just like camping, it's cool to drive to a park, assemble the antenna, connect the power bank, and make the whole system work in an unfamiliar environment.

During portable operations, I often use an ICOM IC-705 with [a DIY V-pole or inverted-V antenna](https://en.wikipedia.org/wiki/Dipole_antenna).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/705.jpg" title="My Rigs" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            My IC-705, paired with a DIY V-pole antenna, operates on the <a href="https://en.wikipedia.org/wiki/FT8">FT8 mode</a> of the 20m band.
        </div>
    </div>
</div>

## Under Construction: My Ham Radio Base Station
Recently, I was lucky enough to acquire rooftop access thanks to my friend **BI1OLC**. This has given me the opportunity to build my own ham radio base station at [ON70](https://gridmaster.fr/grid-on70-sat).

For satellite communication, I purchased Diamond Yagis for the base station.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/yagis_at_on70.jpg" title="The Diamond U15 Yagi antenna at my base station" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            <a href="https://www.diamondantenna.net/pdfdocs/A430S10and15.pdf">The Diamond U15 Yagi antenna</a> at my base station, temporarily mounted on a tripod.
        </div>
    </div>
</div>

Typically, Yagis should be mounted on a rotor. However, the Yaesu rotor is too expensive for operating just 2 Yagis. Therefore, I decided to buy a cheap industrial camera rotor instead, and modified it to serve as an antenna rotor. I plan to add encoders inside the rotor to obtain precise azimuth and elevation values. Then, I will write a script for the motion planning part.

For [HF](https://en.wikipedia.org/wiki/High_frequency) communication, I purchased the ICOM IC-7300 in Akihabara during ICRA '24. It will be the main device I operate in the HF band. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/7300_at_Akihabara.jpg" title="ICOM IC-7300 at Akihabara" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            Got an ICOM IC-7300 at Akihabara, Tokyo, Japan.
        </div>
    </div>
</div>

## My QSL Cards
I have several different designs of [QSL cards](https://en.wikipedia.org/wiki/QSL_card).

### V1
The first commemorative card is available in limited numbers from October 2023 to March 2024.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/qsl1.jpg" title="My QSL Cards" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            The first commemorative card shows me using an RTL-SDR and a U7V4 Yagi antenna to receive <a href="https://amsat-uk.org/beginners/iss-sstv/">the SSTV signal from the International Space Station</a>.
        </div>
    </div>
</div>

### V2
The second QSL card, also printed in limited numbers, commemorates my first [Summits On The Air (SOTA)](https://en.wikipedia.org/wiki/Summits_On_The_Air) operations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/qsl2.jpg" title="My QSL Cards" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            The second commemorative card features my DIY <a href="https://en.wikipedia.org/wiki/High_frequency">HF</a> antenna and a baby van. Just 2 days after this SOTA operation, my friend BI1OHI began a road trip around China in this baby van.
        </div>
    </div>
</div>

### V3
`Currently, the third QSL card is in use` and aims to advocate for our robot, [ArrayBot](https://steven-xzr.github.io/ArrayBot/).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project/ham_radio/qsl3.jpg" title="My QSL Cards" class="img-fluid rounded z-depth-1" %}
        <div class="caption">
            The third QSL card advocates for our robot.
        </div>
    </div>
</div>

`I enjoy collecting paper QSL cards!` If we have a QSO, please send me your card, and I will send back my card. SWL QSLs are also welcome. For more details, see [here](https://www.qrz.com/db/BI1NWO).

## Friends in Ham Radio

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <a href="https://www.qrz.com/db/BY1QH/">
            {% include figure.html path="assets/img/project/ham_radio/by1qh.jpg" title="Tsinghua Amateur Radio Club, BY1QH" class="img-fluid rounded z-depth-1" %}
        </a>
        <div class="caption">
            <a href="https://www.qrz.com/db/BY1QH/">Tsinghua Amateur Radio Club, BY1QH</a>
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <a href="https://yurihou.github.io/">
            {% include figure.html path="assets/img/project/ham_radio/bh9dwe.jpg" title="Yurihou, BH9DWE" class="img-fluid rounded z-depth-1" %}
        </a>
        <div class="caption">
            <a href="https://yurihou.github.io/">Yurihou, BH9DWE</a>
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <a href="https://echoandmoonlight.com/">
            {% include figure.html path="assets/img/project/ham_radio/bi1qgx.jpg" title="Hydroxide, BI1QGX" class="img-fluid rounded z-depth-1" %}
        </a>
        <div class="caption">
            <a href="https://echoandmoonlight.com/">Hydroxide, BI1QGX</a>
        </div>
    </div>
</div>

## My Logbook
You can use the HRDLOG search service below to check our [QSO](https://en.wikipedia.org/wiki/Contact_(amateur_radio)).

<p>
    <iframe width="750" height=600 scrolling="auto" src="https://www.hrdlog.net/hrdlogframe.aspx?user=BI1NWO&amp;lastqso=20&amp;qsomap=&amp;options=search"></iframe>
    <!-- HRDLOG.net script stop -->
</p>