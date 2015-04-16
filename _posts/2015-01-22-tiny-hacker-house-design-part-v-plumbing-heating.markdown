---
layout: post
title: "Tiny Hacker House Design Part V: Supply Plumbing / Heating"
comments: true
date: 2015-01-22
categories: tinyhouse
tags: tiny hacker house design supply plumbing radiant floor heating
---

Hi folks. It's been a while since the last update, but for good reason! I've been
busy building. More on that in another post. But first, I'd like to discuss
plumbing.

(A little aside: Unless you're willing to spend hours and hours designing a
system from scratch (and likely still get it wrong), please just hire a
professional. I'm only offering here the resources I've found helpful in the
hopes it'll be helpful for other DIY'ers. I certainly wish I had more examples
available to study as I dove into this adventure.)

<!-- break -->

Since the tiny hacker house will be heated via a closed-loop in-floor radiant
heat system, the plumbing is a bit more complicated than your typical tiny
house. One heater will need to provide hot water for
both the fixtures and home heating, so a "smarter" system is required to ensure
everything flows properly and stays hot. Unfortunately, that means a bit
of back-of-the-napkin calculations are in order.

<h3>Water heater sizing for mortals</h3>

The first order of business is figuring out a "worst case" scenario
for hot water usage. This will serve as the maximum heat load for the system,
measured in BTUs / hr. If you have a stationary home with traditional heating,
this is pretty easy -- just throw in one or more electric tank heaters
(depending on the size of your family) and you're done. With mobile homes and
radiant heating, though, it requires answering some questions first. Tank or
Tankless? Planning ski trips? Having house guests? Using an automatic dish
washer? Everyone's scenarios are different.

__My "worst case" scenario is taking a 110&deg;F shower in 0&deg;F weather
while keeping the house at a comfortable 75&deg;F.__

To calculate the required BTUs per hour for this load, I simply need to know 4
things: the starting temperature of the water I want to heat for my shower, the
flow rate of the shower head, the area of my walls, floors, and ceilings, and
the insulation R-value for each.

If I assume the temperature of the water for my shower comes from the tank at
32&deg;F (hopefully not frozen!), we can estimate the BTU/hr required to heat
the water to 110&deg; through a 2.2 GPM shower head using the calculation:

_BTU/hr = 500 * water flow rate * (temperature inside - temperature outside)_

_BTU/hr = 500 * 2.2 * (110 - 32)_

_BTU/hr = 85,800_

Now, to estimate the BTU/hr required to heat the home, I can use the following
equation:

_BTU/hr = (wall surface area / R-value) * temperature difference_

Shown below is a table summarizing the R-value and area of my walls and
windows. I'm assuming a very conservative R-value of 20 for all my walls and 1
for windows. With more efficient windows, thermal barriers, and 3" of spray
foam insulation, it should be much higher in practice.

| Location | Area (sq) | R-value | A / R |
|-
|N Wall| 75 | 20|3.75|
|S Wall| 55 | 20|2.75|
|E Wall| 130| 20|6.5|
|W Wall| 130| 20|6.5|
|Ceiling| 116| 20|5.8|
|Floor|106|20|5.3|
|Windows|70|1|70|
| | | | |
|Total| | | 101.1 |

Notice the majority of heat loss occurs through the windows due to their
relatively low R-value. Increasing the efficiency of the windows to R-2 or even
R-5 can help dramatically. But in this worst-case scenario, the required BTUs /
hr to heat the house is:

BTU/hr = 101.1 * 75 = 7,582

So the total BTU/hr needed for my "worst case" scenario noted above is

85,800 + 7,582 = 93,382 BTU/hr

After a bit of searching around, I decided to go with the
[Takagi T-KJr2](http://www.takagi.com/products/tankless-water-heaters/t-kjr2-in-p).
Its 140,000 BTU capacity and 82% efficiency means it'll be able to supply up to
114,800 BTUs of heat -- more than enough for my maximum heat load scenario.

<h3>Let's get pumped</h3>

After the water heater's been decided, we need to find a circulation pump to
move the water through the radiant floor loop, heat exchanger, and water heater
at the proper flow and pressure. With a pump too small, the efficiency of the
plate heat exchanger suffers -- I may not be able to reach the 110&deg;F design
temperature for the domestic hot water. With a pump too large, the efficiency
of the system suffers -- pressure drops exponentially with higher and higher
flows.

<center>
<img src="/img/plumbing/takagi_curve.png"
  alt="tiny hacker house plumbing taco bumblebee curve">
<div class="caption">
<i>Pressure drop and temperature rise charts for a given flow for the
Takagi T-KJr2 water heater.</i>
</div>
</center>

At this point, a professional plumber would calculate the required flow for
maximum heat transfer for my heat exchanger in my worst case scenario, the
pressure drop through the radiant floor loop, and accurately size a high
pressure, low flow pump based on this information.

We're not going to do that.

Instead, I've opted to go with the Taco Bumblebee -- a variable speed, low
power programmable pump. At just under $200, it's in the ballpark of most
conventional circulation pumps, and uses as little as 9 W at the lowest speed
setting. Pretty efficient if you ask me.

Except the issue with this pump (or rather, my system) is that I have a
relatively high pressure drop compared to most conventional radiant floor
systems. This is because of my choice of 1/2" PEX pipe, which I chose because
of its 5/8" outside diameter -- my subfloor plywood in which I'm laying the
radiant piping is only 1 1/8" thick. With 3/4" PEX I need a 7/8" groove in the
subfloor, meaning for long length-wise runs of my floor, I'd have only 1/4" of
subfloor plywood supporting the load above. If it cracks or breaks, the
hardwood floor above would likely crack soon after (it's running in the same
length-wise orientation as the heating loops), and I'd have to rip up the whole
floor down to the trailer frame to fix everything. In a conventional home, I'd
have plenty of space to use larger pipes. But with a tiny house, there are
trade-offs I have to make.

Here's a table of my estimated combined max pressure drop vs flow in the
radiant loop, calculated from the Takagi chart above and the pressure drop
tables from the [residential pex design
guide](http://www.huduser.org/portal/publications/pex_design_guide.pdf) (PDF):

| Flow (GPM) | Pressure Drop (ft. of head) |
|-
|1.0|6|
|1.5|11|
|2.0|18|
|2.5|29|
|3.0|40|
|3.5|52|
|4.0|65|
|4.5|81|
|5.0|96|
|6.0|140|

Experienced plumbers and hydro engineers may look at this table and say, "get a
cheap diaphragm pump, dummy! High pressure, low flow!". But the Bumblebee is
_programmable_, that's like marketing kryptonite for software engineers such as
myself. It has 3 modes of operation! 2 temperature sensors! Bring on the
Arduino shield baby!

<center>
<img src="/img/plumbing/taco_curve.png"
  alt="tiny hacker house plumbing taco bumblebee curve">
</center>

The good news is the Bumblebee will work for my system, albeit at a maximum
flow of 1.5 - 2 GPM. But this reduces my electricity usage anyway, and provides
the maximum heat rise from my water heater. The only issue now is the heat
exchanger loses its efficiency at that low flow.

Theoretically, roughly the same amount of heat is applied to a fluid through a
heat exchanger regardless of flow, but in reality, faster flows generate more
turbulence across the plates, covering more surface area and transferring more
heat.

My solution to this final puzzle is to buy the largest heat exchanger feasible
-- a 1,000,000 BTU/hr copper-brazed plate exchanger (sometimes the brute force
approach is best). The difference between the small and large ones is
a matter of a few hundred dollars and a few inches, but the heating capacity
gains are ten-fold. It's an upfront cost that will save on both electricity and
propane costs for the life of the house.

<h3>Tap supply</h3>

To supply cold / hot water to the fixtures in the house, there are two possible
scenarios to take into account.

If the tap water's already coming from a pressurized source such as a garden
hose, city water, or RV hookup, you simply need to filter the water before
running to your heat exchanger and taps. It's also recommended to install a
water pressure regulator in case you happen upon any extreme pressures in your
travels.

If, however, it's coming from the tank, you need to pressurize it, feed it to a
buffer / accumulator tank (to prevent rapid pump cycling and surges) then feed
it to the rest of your tap lines.

Many choices for parts abound for scenario 2, but what's most important is the
GPM rating of the pressure pump and its power consumption. I've selected one
rated for 3.0 GPM at 90 W, but they come in all sizes.

<h3>Mixing electricity and water</h3>

Finally, we need to add a bit of smarts so that everything is automatic.

The state of the plumbing system can represented by 2 "bits" of information:
fixture (shower) on / off and radiant floor on / off. So there are four
possible states the system can be in: both off, both on, fixture on, or radiant
on.

Using an HVAC thermostat and flow switch, we can control the system with a
simple "truth table":

| Thermostat requesting heat? | Hot tap flow? | Pump state | Radiant zone valve |
|-
|No|No|Off|Bypass|
|Yes|No|On|Floor loop|
|Yes|Yes|On|Floor loop|
|No|Yes|On|Bypass|

So if I'm showering and it's cold outside, the pump is on and the thermostat
switches the zone valve to the floor loop. If I'm showering in the summer, the
pump is on but the zone valve is set to bypass the floor loop so as not to heat
up the house. The water heater fires up automatically when it senses flow above
0.5 GPM, so the pump triggers the water heater in this setup.

Add in a couple relays to provide the switching and I should be good to go.

<h3>Putting it all together</h3>

I now humbly present to you, the schematic:

<center>
<img src="/img/plumbing/schematic.png"
  alt="tiny hacker house plumbing schematic">
<div class="caption">
<i>Ok, so I like to color outside the lines a little</i>
</div>
</center>

If any professional plumbers are reading this and feeling generous,
please offer your critique in the comments below!

_Update:_

The [reddit discussion](http://www.reddit.com/r/TinyHouses/comments/2tdin6/finally_finished_my_tiny_house_radiant_floor/)
concerning this design has prompted me to reconsider going with a dual zone heater, known as a "combi"
boiler. The problem is, they're very pricey -- this 
<a href="http://www.amazon.com/gp/product/B0082LSCKO/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B0082LSCKO&linkCode=as2&tag=modebedo-20&linkId=265ZGRACS6NKR7PD">Rinnai E110CP</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=modebedo-20&l=as2&o=1&a=B0082LSCKO" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
is about 2x the cost of the setup shown here for a similar BTU rating. It would
be nice to save a bit of space and plumbing complexity, but if the pump, heat
exchanger, or zone valve fail I'm stuck with OEM replacements.
