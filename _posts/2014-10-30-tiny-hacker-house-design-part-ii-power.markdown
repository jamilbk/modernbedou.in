---
layout: post
title: "Tiny Hacker House Design Part II: Power"
comments: true
date: 2014-10-30
tags: tiny hacker house design power electrical
---

(If you missed the last post highlighting the major design choices for the tiny
hacker house, this one may be a little out of context. You should probably [go
read]({% post_url 2014-10-22-tiny-hacker-house-design-part-i-overview %}) it
now.)

When I first contemplated building a tiny house, the electricity system was the
first thing I researched. Maybe that's because it's what I'm most comfortable
with as an electrical / computer engineer, or perhaps it's because that's what
enables the rest of the house to come alive. Since I wasn't planning to be
grid-tied, I had to depend on my electrical system to provide the comforts for
everyday life. If I wanted to rely on my home to support a decent living, it
needed to be fault-tolerant and straightforward to manage.

<!-- break -->

After much research, I've chosen to go with a solar system and
propane-converted Honda generator for backup. The panels will lie flat on my
slanted roof and I'll park the house facing south whenever possible to maximum
sunlight absorption. I toyed with the idea of building a collapsible windmill
like [this one](http://windpax.com) for backup power, but it would be need to
be huge, durable, and powerful -- likely a too expensive and time-consuming job
for a tiny house. I'll just stick to solar and propane. At least until my
nuclear reactor arrives in the mail.

<center>
  <img src="/img/power-panels.png" alt="Power Solar Panels">
  <div class="caption">
    <i>
      You could say I'm a bit power hungry.
    </i>
  </div>
</center>

Tiny houses are already space-confined; I didn't want to feel
electrically-confined as well. At the very minimum, I knew I needed to power
A/C, a refrigerator, lights, internet equipment, and a computer simultaneously.
At the peak, however, that includes a few more things -- pressurizing water,
brewing coffee, and using a hair dryer perhaps. I wanted to be able to support
a realistic load without tripping the breaker. So I came up with the following
table:

Device | Max power draw (W)
-|-
Laptop | 85
Hairdryer | 1000
Coffee machine | 800
TV | 100
Air conditioner | 800
Refrigerator | 65
Wireless router | 10
Lights (4) | 60
Water pressurizer pump | 90
|=
Total | 3010

Knowing that I'd need up to 3010 W of power at any one time, I could size my
inverter. If you're not familiar with electrical systems, the inverter is the
device that takes power from a 12 V DC source like a car battery and converts
it to the 120 V or 240 V AC standards used in homes around the world. They're
never 100% efficient, so a little power is lost in the form of heat during the
conversion process. They also don't like being run at maximum capacity for
extended periods of time, so it's good to leave a buffer to account for
unexpected power draw. Because of this (and other reasons noted below), I decided
to go with Outback's [FlexPower
One](http://www.outbackpower.com/outback-products/integrated-systems/item/flexpower-one?category_id=441)
utilizing a 3600 W inverter.

To continue sizing the rest of the solar system, I needed to calculate my
average kWh used per day. A kWh, or kilowatt-hour, of electricity is simply the
amount of kilowatts used in one hour. To calculate this I determine the number
of hours I expect to use each device in a given day, multiply by its power draw
from the table above, and sum the result:

Device | Usage per Day (h) | Power usage (Wh)
-|-|-
Laptop | 4 | 340 
TV | 2 | 200
Air conditioner | 4 | 3200
Refrigerator | 8 | 520 
Wireless router | 24 | 240
Lights (4) | 6 | 360
Water pressurizer pump | 2 | 180
||=
|Total | 5040 Watt-hours

5040 Wh or about 5 kWh of power used in a typical day. To account for heat loss
inefficiencies in the system I multiplied this number by 1.5, ending up with
7.5 kWh. This means the battery bank will need to supply 7.5 kWh per day if
fully drained, but since it's damaging to discharge them more than 50%, we need
to multiply this number by 2. So 15 kWh of electricity is needed.

To find the number of deep-cycle batteries I'll need, I divide 15 kWh by the
voltage of my battery bank, 48 V. This gives me the required Ampere-hour (Ah)
rating of the bank.  [These](http://www.amzn.com/B00DDZ2H6E) heavy duty deep
cycle batteries offer 1240 Ah at 12 V, or 310 Ah at 48 V. This comes pretty
close to the 312.5 Ah required, and considering I'll have a 3000 W generator
backup, should be adequate for the tiny hacker house. For a better how-to on
sizing a solar battery bank, check
[this](http://www.instructables.com/id/How-to-Size-Your-Off-Grid-Solar-Batteries-1/)
Instructables DIY.

<center>
  <img src="/img/power-generator.png" alt="Honda Generator">
  <div class="caption">
    <i>
      A 3000 W propane-fueled generator sits on a hitch-mounted luggage rack on
the back of the trailer.
    </i>
  </div>
</center>

Finally, I need to be fairly confident the solar panel array can provide enough
juice to charge the battery banks to 100% on a clear, sunny day. This will vary
wildly depending on the time of year, where I'm parked, the weather, angle of
the panel, and efficiency of the panel. For example, using
[this](http://www.sunsoglobal.com/calculator.html) panel sizing calculator,
Phoenix, AZ receives about 5.75 sun-hours in the winter, while Seattle, WA only
musters 1.6. This means your solar panel array would need to be about 3.5 times
larger if living in Seattle than Phoenix.

For the tiny hacker house, the majority of power is used by the A/C, so in the
winter months my power needs will be reduced to about 1.8 kWh -- less than half
required in the summer months.  Heating will be provided by in-floor solar
heating with a propane stove as backup, so minimal electricity requirements
there. I should mention that insulation plays a huge role in the power
requirements to heat and cool the home. Closed-cell spray foam insulation seems
to be the best available, which I'll cover in a later article.

<center>
  <img src="/img/power-panels2.png" alt="Solar panels">
  <div class="caption">
    <i>
      At 21.3" x 47", <a href="http://amzn.com/B009Z6CW7O">these</a> Renogy 100
W panels fit perfectly on the roof.
    </i>
  </div>
</center>

The tiny hacker house roof has room for about 800 W of panels. Taking
everything into consideration, in the worst case scenario, I'd be able to
produce 0.8 kW * 1.6 h = 1.28 kWh / day on average during the winter in
Seattle. At an estimated usage of 1.8 kWh / day with no A/C, that means my 3000
W generator will need to run at full load for (1.8 - 1.28) / 3 = 0.1733 hours,
or about 10.4 minutes per day to make up the difference the solar panels can't
provide. I'm ok with that.

As you can tell, designing and managing an off-grid electrical system is pretty
complicated. That's why I chose to go with an integrated power management
system like the FlexPower One. It provides an inverter, MPPT charge controller,
logging device, and will even remote-start my generator when the battery bank
falls below a supplied charge threshold. With 100 lb of propane, I could run
the generator at full load for up to 40 hours (calculated from
[here](http://www.yamaha-propane-natural-gas-generators.com/fuel_consumption.htm)).
Plenty of power to live comfortably without worry!

That sums up the electrical system -- hope you made it all the way
through. If you have any questions please leave a comment below or [shoot me an
email](mailto:contact@modernbedou.in). In the next post we'll dip into some
smelly subjects as we take a splash in the bathroom. :-)

{% include all_design_posts.markdown %}
