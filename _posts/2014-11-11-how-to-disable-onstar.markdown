---
layout: post
title: "How to Disable Onstar on Newer Trucks"
comments: true
date: 2014-11-11
tags: onstar removal tracking
---

I bought a 2015 Chevrolet 2500 HD earlier this year to tow my [tiny
house]({% post_url 2014-10-22-tiny-hacker-house-design-part-i-overview %}). The
dealer claimed they can't completely disable the remote control and
tracking device, a.k.a. Onstar, from my new vehicle. They could only
unsubscribe me from its paid service and monthly maintenance reminder emails.

That's a problem. I want it gone.

Let me clarify by saying I think Onstar is a great idea, in theory. Find your
vehicle if stolen, unlock your doors if you lose your keys, send help when you
wreck... what's not to love? Devices are becoming smarter and this is
generally a good thing, but not when the user has almost no control over the
device he or she purchased (and spent lots of money on). When will the auto
industry begin providing open APIs for engineers and empowered users to
leverage?

A cursory [Google image search](https://www.google.com/search?as_st=y&tbm=isch&hl=en&as_q=onstar+control+room&as_epq=&as_oq=&as_eq=&imgsz=&imgar=&imgc=&imgcolor=&imgtype=&cr=&as_sitesearch=&safe=images&as_filetype=&as_rights=)
leads one to believe Onstar may have some room for improvement in the privacy
department -- if pictures of their control room are so readily available,
imagine what's happening with your private conversations, driving statistics,
and location data? And even if they
[claim](https://www.onstar.com/web/portal/privacy?g=1) strict privacy policies
themselves, what's to stop a malicious third party from [hacking the
database](http://resources.infosecinstitute.com/fbi-tor-exploit/) or
[coercing](http://www.theguardian.com/technology/2013/oct/07/fbi-bitcoin-silk-road-ross-ulbricht)
Onstar employees to hand it over? Best to just temporarily disable the system
completely.

These instructions will show you how to disable the Onstar LTE antenna in your
2015 GMC / Chevy HD truck. This process shouldn't void your warranty, throws no
check engine lights, and can be easily reversed at a later date. DISCLAIMER:
I'm not responsible for any damage you may impart to your vehicle following
this guide! Follow these instructions at your own risk.

### Step 1: Remove radio faceplate surround

Using suction cups or a spudger, gently pry the plastic plate surrounding the
LCD and radio controls from the dash.

<center>
  <img src="/img/onstar-removal/1.jpg" alt="Remove plastic surround">
  <div class="caption">
    <i>
      The plastic surround is held in with little clips.
    </i>
  </div>
</center>

### Step 2: Remove LCD screen

Remove the hex bolts holding the LCD screen to the dash assembly.

<center>
  <img src="/img/onstar-removal/2.jpg" alt="Remove LCD screen">
  <div class="caption">
    <i>
      LCD screen should come out pretty easily.
    </i>
  </div>
</center>

### Step 3: Disconnect the wires from the Onstar unit

Carefully disconnect the wires from the metal-enclosed Onstar unit. Pay
attention not to damage the coaxial antenna cable, as it is sensitive.

<center>
  <img src="/img/onstar-removal/3.jpg" alt="Remove Onstar cables">
  <div class="caption">
    <i>
      Wires are color-coded for easy re-attachment.
    </i>
  </div>
</center>

<center>
  <img src="/img/onstar-removal/3.5.jpg" alt="Module model">
  <div class="caption">
    <i>
      Wait I thought these were American-made trucks?
    </i>
  </div>
</center>

### Step 4: Remove the six Torx screws holding the Onstar module together

I believe these are T8 screws -- it's been while since I performed this
procedure.

<center>
  <img src="/img/onstar-removal/4.jpg" alt="Remove Onstar module screws">
  <div class="caption">
    <i>
      Don't lose the screws!
    </i>
  </div>
</center>

### Step 5: Remove the plastic electrical bridge from the antenna daughter board.

Carefully separate the Onstar module to reveal a plastic bridge connecting the
module's mainboard to the antenna daughter board. Remove this bridge to disable
the antenna and therefore prevent Onstar connectivity.

<center>
  <img src="/img/onstar-removal/5.jpg" alt="Remove antenna daughter board
bridge">
  <div class="caption">
    <i>
      Don't bend or break the pins!
    </i>
  </div>
</center>

### Step 6: Assemble it back together

Simply follow the procedure in reverse to assemble everything back together.
Now, when you press the blue Onstar button, you should hear a notice about the
computer failing to connect to Onstar!

One privacy-enhanced Heavy Duty truck: check! Now if I could only figure out
how to trash the Sirius XM radio system and get them to stop hassling me to
continue service.
