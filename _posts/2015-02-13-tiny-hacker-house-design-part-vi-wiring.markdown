---
layout: post
title: "Tiny Hacker House Design Part VI: Wiring"
comments: true
date: 2015-02-13
tags: tiny hacker house design power electrical wiring
---

_Disclaimer: I'm not a certified electrician, just a stubborn DIY'er._

**tl;dr:** Scroll to the bottom for the [schematic](#schematic).

Electricity is one of the most important aspects of building a house. If you
get it wrong, your house can burn down. Or you'll constantly be throwing
breakers and frying devices. Definitely hire a professional electrician if you
just want a system that works and is safe. But if you're a stubborn
DIY'er-at-all-costs like me, read on.

Since the tiny hacker house is designed to operate off grid, the electrical
wiring closely resembles what you'd find in a typical RV. I have to say,
information on wiring an RV is extremely hard to come across on the web.  The
main hangup is accommodating for both 12V and 120V supplies. 120V wiring is
straightforward enough -- just follow your local building code's guidelines.
But throw in 12V appliances, a battery bank, inverter, "shore power" and you
have a little more thinking to do.

<!-- break -->

### Picking an Inverter

Needless to say, inverters are extremely important. The good ones seem to do it
all safely and with flying colors, and the really bad ones can hiss, crackle,
spark, and smoke if you even get close to their rated capacity. There are a few
key metrics you need to keep in mind when picking one. Here's what I learned:

##### Signal Quality
There are two types of inverters: pure sine and modified sine wave. The
modified sine wave inverters "mimic" 120V AC with a step wave so while fine for
most devices, it can cause problems for sensitive devices like fluorescent
lights, battery chargers, and some medical equipment. Pure sine wave inverters,
however, generate an AC supply identical to what you'd receive from the city
power grid. Presumably, it makes more sense to go with a pure sine model, but
they can be nearly double the price for the same capacity. Personally, I'm
making the tradeoff for a pure sine model. I don't want any surprises on the
road.

##### Voltage
Assuming you've already determined your [power]({% post_url 2014-10-30-tiny-hacker-house-design-part-ii-power %}) requirements and settled
on a battery bank configuration, you need to pick an inverter that matches your
bank voltage. Most inverters are designed for 12V, but if you need more than
4000W or so they typically require 24V or even 48V DC sources instead. A 24V or
48V system is fine, but then you'll need a step-down converter to power any 12V
appliances you may have (yes, "technically" you can just tap your 48V battery
bank at a 12V point to avoid the converter, but this will drain the bank
unevenly and could reduce its lifetime). If you're using solar as well, this
will have to match your solar MPPT charger's output. Also, you should pick an
inverter with about 120% of the power capacity you plan to use in an ongoing
basis. Most aren't designed to run at 100% capacity for long periods of time.

##### Charging / Pass-through Capability
If you plan to ever hook up to a city power grid or shore power at an RV park
(or even some generators), a charging inverter may suit you better. These smart
devices are essentially an inverter with an AC input to automatically charge
your batteries when you connect to an AC source. The switching happens on the
fly -- when you disconnect (or the generator runs out of gas), the inverter
will automatically and instantly switch from charging mode to inverting mode
with no loss of power to your house in between. Some of the beefier
inverter/chargers can even pass split-phase 240V AC input through to power your
devices. So if your tinyhouse uses a 50A shore power inlet, you'll be able to
use both 120V hot legs of the supply instead of just one, basically doubling
your available power. More on that later.

According to everything I've read so far, the [Magnum
Energy](http://magnumenergy.com) ones are some of the best. They have [a 48V
4000W+ inverter](http://magnumenergy.com/ms-pae-series-invertercharger/)
that supplies split-phase 240V so it could power electric ranges, large ACs,
and electric dryers! We won't be needing any of that for the tiny hacker house,
but it is nice to know I am future-proofed in case my electrical needs grow. 

### 30A or 50A Shore Power: What's the Difference?

When you pull up to your spot at an RV park or campground, you'll typically see
an electrical panel like this:

<center>
  <img src="/img/rv-power-pedestal.jpg" alt="RV Power Pedestal">
  <div class="caption">
    <i>
      From left to right: 50A outlet, 30A outlet, and two 20A outlets all with
corresponding breakers. Notice the double-throw breaker for the 50A outlet!
   </i>
  </div>
</center>

Called the power pedestal, these are pretty much the "main panel" for your
electrical system -- they're where the neutral is bonded to ground. _Note: that
means you **DO NOT** bond your neutral to ground in your tinyhouse's electrical
panel!_

As you may know, 120V systems in the US utilize three wires: hot, neutral,
and ground. Power is applied to your devices via the difference in potential
between the hot and neutral wires. The ground is just a safety measure -- if
the hot leg accidentally shorts to the casing of the device it's powering,
electricity will safely short to ground, tripping the associated breaker
instead of shorting through you if you happen to touch the afflicted device
(think: old rusty washing machine). This is why old homes and some devices are
in "two-prong" configuration -- the ground can sometimes be omitted.

Now, you may notice in that picture the 50A outlet on the left utilizes _four_
wires. Three of them are the same as any ordinary outlet, but the fourth is
actually another hot wire. This means there are _two_ hots, one neutral (shared
between the hots), and one ground. Without getting too technical, this is to
provide 240V AC to certain high-power devices. The additional hot is 120V as
well, but shifted 180&deg; out of phase with the other one, so the average
potential between them sums to 240V. Pretty neat huh?

The corresponding breaker (the two handles on the left) is a double-throw
breaker. That simply means it is actually two 50A breakers with a mechanism in
place such that if one breaker trips, it forces the other 50A one to trip as
well. So with a standard four-wire 50A outlet we actually get 50A + 50A =
_100A_ at 120V, or 12,000W power. That's over **three** times what the 30A
outlet can provide and **five** times what a standard 20A outlet can provide.

So what does this mean for a tinyhouse? If you think you'll ever need more
power than what the three-wire 30A outlet can provide (namely 3,600W), you need
to make sure to use a 50A inlet and wire your house accordingly. That means
picking an inverter that can pass through split-phase AC input, and having at
least two separate 50A electrical circuits for your tiny house: one for each hot
leg of the 50A power.

### Schematic
<a name="schematic"></a>

Finally, here is what all that adds up to:

<center>
  <img src="/img/wiring-schematic.png" alt="Tiny Hacker House Wiring Schematic">
  <div class="caption">
    <i>
      Nothing beats good ol' paper and pencil!
   </i>
  </div>
</center>

In my design, I actually have three panels in order to electrically isolate the
inverter without having to rewire anything. Hence the "main panel" and transfer
panel.

Good luck and email me or comment with any questions!

{% include all_design_posts.markdown %}
